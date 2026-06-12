---
title: "Unable To install Ubuntu"
date: 2010-03-06
forum: New to Ubuntu
---

### Post by killachandra on 2010-03-06
Hi, am an absolute novice with linux, i have a studio xps 1640, with windows 7, i downloaded Ubuntu 9.10 64 Bit, 4 GB ram, and burnt it on a disk. i want to install it to E:\, an empty partition i have created, windows is is c:. 

Now i have tryied installing via Wubi but (the default installation size is 17gb for me and i didn't change it, i changed the  installation drive to E:\ and gave a password to my account. Desktop environment is ubuntu and language is english). But after clicking istall it gives out an error after a while saying "error executing command **>>command=C:\windows\sysnative\bcedit.exe/set**
[B]>>retval=1
>>stderr=an error occured while setting the element data
the request is not supported
>>stdout=[/B]

And when i try installing ubuntu from the boot menu and select the language and select install ubuntu, the screen just fresses though my processer light keeps blinking, i tried waiting for around 15 min but nothing happens i just have to shut it off.

Pls advice...

---

### Post by bumanie on 2010-03-06
Seeing you have a spare partition, it would probably be best to make a dual boot system - there is no real advantage to a wubi install, other than to test ubuntu. With a wubi install, ubuntu is slower and 'ham-strung' from working from within windows. Dual booting does not have these issues.
If you really want wubi, do an md5 checksum of your download and ensure it has no errors and also ensure you have burned the live cd .iso as an image - the alternate installation cd does not work for wubi. If they check out OK, may be wubi will not work on your computer. I have little experience with wubi - may be someone else can tell you more.

---

### Post by spiky001 on 2010-03-06
are you trying to do a dual boot? Booting straight off of cd or loading it with windows running

---

### Post by norbert26 on 2010-03-06
If using WUBI it would have to install WITHIN the windows partition. You cannot use WUBI to install in a partition outside of windows. The idea of WUBI was so ubuntu could be uninstalled using windows add and remove programs making it easy to test ubuntu and try it. To use a seperate partition outside windows you would need to do a regular ubuntu install and choose your partition where to install.

---

### Post by killachandra on 2010-03-06
I am ok with the dual boot as well as wubi. but would prefer dual but to avoid any issues, also when i insert the disk in windows it runs ok. but when i try to install through wubi i get the above mentioned error. also when i try to dual boot it just freezes i suppose as there is no glowing ubuntu logo for about 15min into waiting after selecting install ubuntu.

I suppose i could do the md5 error check thats mentioned above but i dont know how to do that!!!

---

### Post by Rex Bouwense on 2010-03-06
Check here for instructions on how to md5sum check of your download of Ubuntu ISO.  [https://help.ubuntu.com/community/HowToMD5SUM#Check%20the%20iso%20file](https://help.ubuntu.com/community/HowToMD5SUM#Check%20the%20iso%20file).  Enjoy.

---

### Post by pm_mazur on 2010-03-25
did you install ubuntu on this computer before? if so check your hard drive for any remaining ubuntu folders from previous installation. In this case there should be a folder named "Ubuntu" which you have to delete. its either directly in your drive, program files or windows folder (sorry can't remember). 
hope this helps

---

