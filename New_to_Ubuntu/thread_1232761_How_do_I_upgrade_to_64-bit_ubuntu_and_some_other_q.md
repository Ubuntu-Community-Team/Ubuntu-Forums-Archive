---
title: "How do I upgrade to 64-bit ubuntu? and some other questions."
date: 2009-08-05
forum: New to Ubuntu
---

### Post by ChubbySauce on 2009-08-05
I was told Im using 32-bit do I need to reinstall or is there like an upgrade I can do. I heard its something called PAE the 64 bit that is I dont know a lot about it so halp. :3 ty


oh also I was having trouble with the extraction program  in  ubuntu so I got 7-zip
now I uninstalled z-zip cause I got the default extraction program to work.
but its still appears in my applications but I got rid of it through the synatpic package manager so I dont know why its still there. I click it and no such file directory.

btw if I buy cs3 or 4 would it install on ubuntu?

lastly I tried to install adober reader for linux through adobes site. I ran it in terminal and chose a directory but it didnt work can someone walk me through the process if youve expienced it.

again thanks for all who reply much appreciated

---

### Post by starcraft.man on 2009-08-05
> **ChubbySauce said:**
> I was told Im using 32-bit do I need to reinstall or is there like an upgrade I can do. I heard its something called PAE the 64 bit that is I dont know a lot about it so halp. :3 ty 

[http://en.wikipedia.org/wiki/Physical_Address_Extension#Linux](http://en.wikipedia.org/wiki/Physical_Address_Extension#Linux) Explains it. There is no upgrade to 64 bit, that's an architectural change. Backup and reinstall if you want 64. PAE is really just to allow you to address more RAM, it's not equivalent to 64 bit, it's a workaround. It's a long explanation the benefits and costs for 32 and 64, please search forums for them and you'll see better explanations of the difference. For the average user, there is little need IMO for 64 bit or more than 4GB ceiling on RAM without PAE.

> oh also I was having trouble with the extraction program  in  ubuntu so I got 7-zip
now I uninstalled z-zip cause I got the default extraction program to work.
but its still appears in my applications but I got rid of it through the synatpic package manager so I dont know why its still there. I click it and no such file directory. Right click menu, click Edit Menu, then navigate to section of menus it is listed in and unselect it. This will stop it displaying.

> btw if I buy cs3 or 4 would it install on ubuntu?
Nope. See WINE. Search forums for it, I'm sure there's one or two guides. I don't have any off hand. CS3 and 4 are Windows or OSX only, no support for linux. 

> 
lastly I tried to install adober reader for linux through adobes site. I ran it in terminal and chose a directory but it didnt work can someone walk me through the process if youve expienced it.

Adobe reader = bloated. We have lighter software like Evince in GNOME and oKular in KDE (among other programs) that provide equivalent support for pdfs.

---

### Post by 3rdalbum on 2009-08-05
> **ChubbySauce said:**
> I was told Im using 32-bit do I need to reinstall or is there like an upgrade I can do. I heard its something called PAE the 64 bit that is I dont know a lot about it so halp. :3 ty

In order to get a true 64-bit system, you need to reinstall Ubuntu with the 64-bit disc. Choose the "manual" partitioning method and install straight onto the current partition WITHOUT formatting, and then tell it to import the current documents and settings in the next screen.


> lastly I tried to install adober reader for linux through adobes site. I ran it in terminal and chose a directory but it didnt work can someone walk me through the process if youve expienced it.

You don't need to go to the Adobe site to install Acrobat Reader. It's in the Canonical Partner repository (which is listed, but not enabled by default, in System > Administration > Software Sources).

---

### Post by ChubbySauce on 2009-08-06
much thanks for the z-zip part Id give you a bean but Im not sure how :3

---

