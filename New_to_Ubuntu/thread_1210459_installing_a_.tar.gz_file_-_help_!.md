---
title: "installing a .tar.gz file - help !"
date: 2009-07-11
forum: New to Ubuntu
---

### Post by listerdl on 2009-07-11
Hi, can you guys please direct me to the best place to understand how to install from a .tar.gz file?

I was recommended by Vuze to download the .tar.gz to get the latest Vuze version for linux, 4.2

Thanks! As always you guys are the best!!

---

### Post by mano cazalet on 2009-07-11
# tar xvzf package.tar.gz 
# cd package
# ./configure
# make
# make install

generally is like this

but after unpacking the archive there must be a description in readme

edit: dont forget doin it as root, with sudo

---

### Post by Ratscallion on 2009-07-11
First of all, what tar.gz are you trying to "install"? For the record, the program is inside the tarball (technical term for programs inside tar.gz, or any other archive for that matter).

---

### Post by Ratscallion on 2009-07-11
> **mano cazalet said:**
> # tar xvzf package.tar.gz 
# cd package
# ./configure
# make
# make install

generally is like this

but after unpacking the archive there must be a description in readme
Basically that. +1

---

### Post by listerdl on 2009-07-11
Hi thanks for info...

This is the message in the readme:

REQUIREMENTS:
Azureus requires Sun Java 1.5.x or newer to run.
JRE 1.6 (6.0 series) is highly recommended.
[http://java.sun.com](http://java.sun.com)

RUNNING:
1. Extract the contents of this .tar.bz2 file.
2. Change to the 'azureus' directory where the files were extracted.
3. Start Azureus by running the script named 'azureus'; ex. "./azureus"

NOTE:
If you have the Java JRE installed somewhere unusual (or not in your PATH),
use the JAVA_PROGRAM_DIR option in the script.

-- 

With the 2 instruction - does that mean that I overwrite the code in the programme - i.e. does it have to be in the same folder?

Thanks - all advice greatly appreciated - I would like to master this .tar issue...

---

### Post by mano cazalet on 2009-07-11
it should be ok if you installed java the ususal way from repos

---

### Post by jerome1232 on 2009-07-11
> **listerdl said:**
> Hi thanks for info...

This is the message in the readme:

REQUIREMENTS:
Azureus requires Sun Java 1.5.x or newer to run.
JRE 1.6 (6.0 series) is highly recommended.
[http://java.sun.com](http://java.sun.com)

RUNNING:
1. Extract the contents of this .tar.bz2 file.
2. Change to the 'azureus' directory where the files were extracted.
3. Start Azureus by running the script named 'azureus'; ex. "./azureus"

NOTE:
If you have the Java JRE installed somewhere unusual (or not in your PATH),
use the JAVA_PROGRAM_DIR option in the script.

-- 

With the 2 instruction - does that mean that I overwrite the code in the programme - i.e. does it have to be in the same folder?

Thanks - all advice greatly appreciated - I would like to master this .tar issue...

Basically as long as you have suns java jre installed already, just double click the file in there called 'azereus'

---

