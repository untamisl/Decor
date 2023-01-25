Decor
======

<a href='http://android-arsenal.com/details/1/1773'><img src='https://img.shields.io/badge/Android%20Arsenal-Decor-brightgreen.svg?style=flat'></a>

*Decor* is a library that applies decorators to Android layout with additional attributes
without the need to extend and create a custom View for each functionality.

Decor plugs into Android's layout inflation and applies custom attributes to Views.

If you have written a custom View like AutofitTextViewWithFont : to make a TextView resize it's text and have a specific font
and if you want to animate it you can write a custom View like AnimatedAutofitTextViewWithFont and if there's another runtime
custom attribute you want to add you will have to yet create another custom View.
 Decor comes to the rescue to solve this unnecessary class explosion by using a separate decorator for each functionality :
    : AutoFitDecorator , FontDecorator, AnimateDecorator (See decorators module for examples of how to create a decorator)
     and register them in attachBaseContext :
     
```java 
@Override
protected void attachBaseContext(Context newBase) {
   super.attachBaseContext(DecorContextWrapper.wrap(newBase)
           .with(Decorators.getAll()));
}
```
```xml
 <TextView
        xmlns:tools="http://schemas.android.com/tools"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="I'm a TextView"
        app:decorTypefaceAsset="Ubuntu-M.ttf"
        app:decorAutoFit="true"
        tools:ignore="MissingPrefix"/>
```
or with an ImageView : 
<ImageView xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:id="@+id/search"
    android:layout_gravity="center"
    android:layout_width="150dp"
    android:layout_height="24dp"
    android:src="@drawable/search_vector_drawable"
    app:decorAnimateSearch="true" />
    
    
        android:layout_gravity="center"
    android:layout_width="150dp"
    android:layout_height="24dp"
    android:src="@drawable/search_vector_drawable"
    app:decorAnimateSearch="true" />
    
This has the advantage of reusing these decorators in other Views.
The module decorators contains some examples of useful decorators that you can start using now,
or write your own by extending ``` AttrsDecorator<T>``` where T is the type of the View the decor will be applied on.

If you want to apply only a subset of decorators :

```java
@Override
protected void attachBaseContext(Context newBase) {
    super.attachBaseContext(DecorContextWrapper.wrap(newBase)
            .with(new FontDecorator());
}
```

Check the samples for a working example :

![](images/decor_sample.png)


Android Studio (lint) will likely mark this XML with a warning despite being correct. You may want to add tools:ignore="MissingPrefix" to either the View itself or its parent ViewGroup to get rid of it. Also add tools namespace xmlns:tools="http://schemas.android.com/tools" to have access to "ignore" attribute.

Binaries
========

Binaries and dependency information for Maven, Ivy, Gradle and others can be found at [http://search.maven.org](http://search.maven.org/#search%7Cga%7C1%7Ccom.mounacheikhna).

<a href='http://search.maven.org/#search%7Cga%7C1%7Ccom.mounacheikhna.decor'><img src='http://img.shields.io/maven-central/v/com.mounacheikhna/decor.svg'></a>
<a href='http://search.maven.org/#search%7Cga%7C1%7Ccom.mounacheikhna.decorators'><img src='http://img.shields.io/maven-central/v/com.mounacheikhna/decorators.svg'></a>

for Gradle:
```groovy
compile 'com.mounacheikhna:decor:0.2.4'
compile 'com.mounacheikhna:decorators:0.2.4'
```

and for Maven:

```xml
<dependency>
    <groupId>com.mounacheikhna</groupId>
    <artifactId>decor</artifactId>
    <version>0.2.4</version>
</dependency>
<dependency>
    <groupId>com.mounacheikhna</groupId>
    <artifactId>decorators</artifactId>
    <version>0.2.4</version>
</dependency>
```

and for Ivy:

```xml
<dependency org="com.mounacheikhna" name="decor" rev="0.2.4" />
<dependency org="com.mounacheikhna" name="decorators" rev="0.2.4" />
```

Want to help?
=============

File new issues to discuss specific aspects of the API or the implementation and to propose new
features or add new decorators.


Licence
=======
    Copyright (c) 2013 Madis Pink
    Copyright (c) 2015 Mouna Cheikhna

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

        http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.

External code
=======
This project includes code from third parties:
[pretty](https://github.com/madisp/pretty) by [Madis Pink](https://github.com/madisp). MIT licence.
