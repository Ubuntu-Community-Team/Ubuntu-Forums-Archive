---
title: "Ubuntu broke my lacie? Help please!"
date: 2009-11-14
forum: New to Ubuntu
---

### Post by datelus on 2009-11-14
Hi. 
I have a problem and im quite desperate about it.
My laptops hdd broke down so i decided to boot ubuntu from cd. Thats what i did and then i had an idea to install it to my 1tb lacie. I did not format it infact i installed it from system - administration- usb startup disc creator. As i said i did not format it due to important information that is inside there (and hopehully still is)

so i did the install it copied all the files and now i cant acces my data from lacie :((

it just shows up as a 1000gb drive and its empty. In win xp setup it shows as some )&)&)@@:: and win cannot be installed but thats not the problem. So- can i get all my data back and how? Please help i dont know what to do :( oh and i can see that there is some free space as it was 700gb free.  
it was fat 32 ... Thanks alot

---

### Post by empty_spaces on 2009-11-14
Was your external usb drive partitioned for accomodating ubuntu?

---

### Post by datelus on 2009-11-14
Not sure what you mean by that. 
Before it was just a fat32 drive that i used to store everything for years. 
I had no problems with reading or writing to it from ubuntu or any other os.
Thanks for the replay. 
When i go to gpart and select partition tables or sothething it offers a format, but i dot want that

---

### Post by bumanie on 2009-11-14
As far as I know, usbdisk creator formats the entire drive (and from memory, gives one a warning that it is going to do so)- it is highly likely you have lost your information. You could try tools like [testdisk/photorec]("http://www.cgsecurity.org/wiki/TestDisk") or possibly[ scalpel/foremost]("http://www.ubuntugeek.com/recover-deleted-files-with-foremostscalpel-in-ubuntu.html") to retrieve the data. Make sure you do not try and write anything else to it. Read all documentation very carefully before trying. Never used scalpel/foremost, but testdisk and photorec work very well.

---

### Post by datelus on 2009-11-14
It offers an option to format, but that is a button, that you press if you want to format that drive. I just pressed the make startup disc button and it started to copy files from cd. Im gonna try those programs thanks (as soon as i get acces to internet)
if it would be completle wiped it would show ~980gb free, then i would have no questions ,but now it shows ~700 free and that gives me hope :)

---

### Post by empty_spaces on 2009-11-14
> **datelus said:**
> Not sure what you mean by that. 
Before it was just a fat32 drive that i used to store everything for years. 
I had no problems with reading or writing to it from ubuntu or any other os.
Thanks for the replay. 
When i go to gpart and select partition tables or sothething it offers a format, but i dot want that

From your reply, it looks like you installed ubuntu on the whole external drive without making any partitions or backing up your data.
You really should understand partitioning before playing with OS installations. That's like driving a car without knowing where the brakes are.
I'll wait and see if someone with more data recovery experience posts here.

Edit : Whoops. I guess I'm a slow typer :)

---

