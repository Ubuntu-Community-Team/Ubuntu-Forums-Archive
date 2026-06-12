---
title: "Ubuntu 10.10, MacOSX 10.6.7, dual boot, sharing a folder"
date: 2011-04-20
forum: New to Ubuntu
---

### Post by Whenry on 2011-04-20
Hi,

I have Ubuntu 10.10 and MacOSX 10.6.7 installed on a macbook pro in a dual boot setup.

I mainly use Ubuntu for MATLAB at this point but I also use MATLAB on my Mac.

I would like to be able to use the same folder for MATLAB codes, so that I can update the files from either Ubuntu or MacOSX.

Right now I have the MATLAB folder in /Users/shared on my Mac partition, but I only have read permissions from Ubuntu.

I managed to change my user ID in Ubuntu to 501, the same as my user ID in Mac OSX, I even have permissions when I do a get info on the folder from within Ubuntu, but when I try to save a file from within Matlab I get an error stating the folder is read-only.

any help would be great! :-)

Will

---

### Post by coffeecat on 2011-04-20
Your Mac partition will be formatted with the journalled version of the HFS+ filesystem. The Linux driver can only read the journalled version, not write to it. But it can write to the non-journalled version of HFS+, and it is possible to switch off the journal of a HFS+ formatted partition to make it writeable from Ubuntu.

If you want the (MacOS) terminal command to disable the journal, I could hunt this out for you, but it's not something I would want to do with my Mac system.

---

