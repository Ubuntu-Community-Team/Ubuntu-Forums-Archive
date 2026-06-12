---
title: "Can't install this .bz2"
date: 2010-10-07
forum: New to Ubuntu
---

### Post by AkaChan83 on 2010-10-07
Trying to install [this]("http://www.amok.am/en/freeware/amok_exif_sorter/download/#") but I'm stuck :( I got some info from [this page]("http://ubuntuguide.org/wiki/Ubuntu:Lucid#Package_Installation_and_Updates") but I don't know what to do after that. *sigh* :confused:

---

### Post by halitech on 2010-10-07
what have you done so far?

---

### Post by godspeedmav on 2010-10-07
> **AkaChan83 said:**
> Trying to install [this]("http://www.amok.am/en/freeware/amok_exif_sorter/download/#") but I'm stuck :( I got some info from [this page]("http://ubuntuguide.org/wiki/Ubuntu:Lucid#Package_Installation_and_Updates") but I don't know what to do after that. *sigh* :confused:

Firstly, open up a terminal, here is how:
```
Applications > Accessories > Terminal
```

Then ```
cd /path/to/your/folder
``` that has your .bz2 file. after that type: ```
tar xvfj yourfile.bz2
```

after that you will see that it's been unzipped so ```
cd ./your-unpacked-folder-name
``` then it would probably be ```
./configure
``` if successful you could do ```
make && make install
``` 
Or you might want to try reading the README file after unzipping the file.

---

### Post by gandaran on 2010-10-07
just extract the package, this is java software, then run Exifsorter.jar package with java, (right click the Exifsorter.jar package and choose open with sun-java) you will need to install sun-java or openjdk-java to run this software.

---

