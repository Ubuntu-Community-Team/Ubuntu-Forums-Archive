---
title: "no hugin 0.7.0 for hardy"
date: 2009-01-10
forum: New to Ubuntu
---

### Post by antony_css on 2009-01-10
The latest stable release of hugin panorama creator does not appear in hardy LTS.:(:(:(

I really miss the the new "Exposure correction" feature...
My camera does not have settings for exposure, so sad...:(:(:(

---

### Post by Michael.Godawski on 2009-01-10
hi, 
you can download the 0.7 version from here:
[http://sourceforge.net/projects/hugin/](http://sourceforge.net/projects/hugin/)

If you need help with installing just ask.
You find some instructions in the file 
Install_cmake.

---

### Post by antony_css on 2009-01-10
Do you mean a deb package?
I don't feel well about compiling from source... It often crashes.

---

### Post by antony_css on 2009-01-10
BTW, getDeb returns no results.

---

### Post by Michael.Godawski on 2009-01-10
Give compiling a go :). It is not that evil.

First download the necessary installation package:

```
sudo apt-get install cmake
```
and perhaps these too
```

sudo apt-get install build-essentials
```

Now navigate in terminal into the extracted folder of hugin and run these command in sequence:
```

cmake -DCMAKE_INSTALL_PREFIX=/usr/local .
make
make install
```

---

### Post by antony_css on 2009-01-10
> 
$ cmake -DCMAKE_INSTALL_PREFIX=/usr/local .
-- Check for working C compiler: /usr/bin/gcc
-- Check for working C compiler: /usr/bin/gcc -- works
-- Check size of void*
-- Check size of void* - done
-- Check for working CXX compiler: /usr/bin/c++
-- Check for working CXX compiler: /usr/bin/c++ -- works
**CMake Error: wxWidgets required, please specify it's location.**
-- Configuring done


:p haha, dependencies problem

---

### Post by Michael.Godawski on 2009-01-10
Try this:

```
sudo apt-get install libalien-wxwidgets-perl
```
and install one more time :)

---

### Post by antony_css on 2009-01-10
This is the result:
> 
$ sudo apt-get install libalien-wxwidgets-perl
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libalien-wxwidgets-perl


---

### Post by Michael.Godawski on 2009-01-10
:confused:
Open Synaptics and search for  wxWidget.

Was my first entry in the search results.

---

### Post by antony_css on 2009-01-10
none.
only found "plplot9-driver-wxwidgets"
something like plugin for the program "PLplot"

---

### Post by antony_css on 2009-01-10
I am going to compile the whole hugin according to this link:
[http://wiki.panotools.org/Hugin_Compiling_ubuntu]("http://wiki.panotools.org/Hugin_Compiling_ubuntu")

I think this will spend me a whole day... wish me good luck.

---

### Post by Michael.Godawski on 2009-01-10
Are your sources activated?

Can you please post the output of
```

cat /etc/apt/sources.list
```

Edit:

Good luck with this guide. Looks good. Report back when you managed to install it :)

---

### Post by antony_css on 2009-01-10
Here are the list of sources...

BTW, I have already compiled and installed hugin 0.7.0 using "auto-apt" and "checkinstall". How can I upload the deb files so that others can download and install the latest hugin in Hardy?

---

### Post by antony_css on 2009-01-16
Just for reminder...
A bug encountered when I first use the "Stitch Now!" function after I had compiled and installed hugin-0.7.0 from source.

"**enblend**" was set as "**false**" in the makefile:
> 
**false** -f12024x3667 -o panorama.tif panorama0000.tif panorama0001.tif
make: ** [panorama.tif] Error 1

"-f12024x3667" specifies the output dimension; "panoramaXXXX.tif" are the remapped images; and "panorama.tif" is the final panorama that supposes to be created using an external program "enblend".

This problem can be solved by re-setting the preference file:
File>Preferences>Load Defaults>Apply

I am sure I downloaded a stable version from the official site, not from svn. I think preference file provided in the source may be already corrupt.

To guys who are using the latest version of Ubuntu shipped with hugin-0.7.0, did you also encounter this problem?

---

