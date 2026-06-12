---
title: "Linux noob with an 1100"
date: 2009-10-06
forum: New to Ubuntu
---

### Post by Tavin237 on 2009-10-06
Good afternoon world of Linux and Ubuntu! :)

     I've installed Ubuntu 9.04 on to an Inspiron 1100 but with out thinking.... I deleted my windows partition. Soooo..... that make my problem all that more worse. In the instalation the screen resulution worked perfictly but when I started Ubuntu after the install its stuck on a smaller screen resulution. As for everything else it works great. I love it.
     
     I was wondering if some one was willing to help a Linux noob well... a computer noob in general to help get this worked out. I looked around a bit to see if anyone had the same issue and it looks quite commen. But there seems to be a diffrent solution for every single thread. Along with the fact that I can't make sence of any of it.

    *Pitifull face* Can anyone help me work though this step my step? I dono how to even open up my command lines in Ubuntu Alt+Ctrl+F1?

     Thanks for takeing the time to read my speal. Hope to see ya around. =D

---

### Post by Temposs on 2009-10-06
Welcome to Ubuntu and the forums!

You can open the command line by going to Applications->Accessories->Terminal

You can play around with the screen resolution by going to System->Preferences->Display. See if you can adjust the resolution there, and post back what happens.

---

### Post by Tavin237 on 2009-10-07
Thanks for the reply that helpped alot wiht what a friend of my helpped me find I found this link and used the 

code: "sudo nano /etc/X11/xorg.conf"

and I manually edited my file so that it matched this post at 

[https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsDell](https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsDell)

I'll post the stuff that I manually inputted but it seems like quite a bit to copy and past into a post. All that asides it didn't work saddly... I took a look into the display setting but it doesn't offer me any resulution settings above 800x600. So where would you say we go from here?

Edit: Maybe a little more helpful when I restarted the computer I have an error message saying it was to run in low graphics mode. Also it said "(EE)Problem Parsing the config file" And under it is said "(EE)Error Parsing the confid file"

---

### Post by lavinog on 2009-10-07
> **Tavin237 said:**
> Thanks for the reply that helpped alot wiht what a friend of my helpped me find I found this link and used the 

code: "sudo nano /etc/X11/xorg.conf"

and I manually edited my file so that it matched this post at 

[https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsDell](https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsDell)

I'll post the stuff that I manually inputted but it seems like quite a bit to copy and past into a post. All that asides it didn't work saddly... I took a look into the display setting but it doesn't offer me any resulution settings above 800x600. So where would you say we go from here?

I think you have to restart X to apply the new xorg.conf file...Try rebooting and see.

---

### Post by Tavin237 on 2009-10-07
I did restart my computer initially and thats when the error came up, thanks for the suggestion I'm following the guide on 

[http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)

I'll update when I'm finished if it worked or not please keep feeding the suggestions though I've been learning a lot about the command and the OS in general.

---

### Post by fraser_m on 2009-10-07
That guide probably isn't the thing you want to get working, could you open up Terminal and run
:

```
lspci
```

---

### Post by Tavin237 on 2009-10-07
FIN! END! FIXED!

So. That guide worked like a charm for me after a few tweeks. Namely I used the command

"sudo nano"

over

"gksudo gedit"

Thanks to the people who helped me out I will sleep better tonight then I would of if I didn't get it to work. If anyone happens to have this same problem as I did send me an email at [email]KROdd2.0@gmail.com[/email] and I'll be happy to walk it though to you if you do not understand the guide. Night everybody.

---

### Post by wilee-nilee on 2009-10-07
I am trying help a friend with this model so keep us posted if you can, it would be helpful.

---

### Post by lavinog on 2009-10-07
> **Tavin237 said:**
> FIN! END! FIXED!

So. That guide worked like a charm for me after a few tweeks. Namely I used the command

"sudo nano"

over

"gksudo gedit"

Glad you got it working...I am a little lost on why it would matter what editor you used.


> 
If anyone happens to have this same problem as I did send me an email at [email]###############[/email] and I'll be happy to walk it though to you if you do not understand the guide. Night everybody.
I would not post your email on here if you don't want a bunch of spam.
You can request others to send you a private message instead.

---

### Post by Tavin237 on 2009-10-08
Thanks for the concern in all honesty though that is my spam email I use when ever I think I might get spam not my normal communication email.

As for an update on the laptop that Ubuntu 9.04 is on, an Inspiron 1100, it working great I've changed my Video Mem from 1MB to 8MB via my BIOS but I do not recall if that guide susgested that. Even still I have occasional video issues (I belive) such as that the (Linux Noob Speak) the desktop environment not always starting up nor am I able to get into the text base of Linux useing "Ctrl+Alt+F1". I have yet to add any add-ons or packets at all asides the ones from the guide and the game Battle for Wesnoth. Saddly I don't belive that this computer has enough video mem to run it. =(

It works excelent right after the install and fix as an office computer and the GIMP program though a bit slow on this vurtual dinosour works fine with a bit of paticents on the user side.

Again I offer to anyone haveing the same problem if they need help I will be more then easy to help you walk though it, but as I said the email stated in my above post is my spam email and it make take me a little bit to reply.

I give Ubuntu on this rig   (AND I STRESS ONLY ON THE COMPUTER I AM USEING THE INSPIRON 1100)   a 3 and 1/2 out of 5, Partly because the computer itself is so old that to today's standards its a slow turtle that can't really be helped even with RAM upgrades, it would be cheeper to buy a computer for $300 on [www.newegg.com]("http://www.newegg.com") then add Ubuntu. Also for the video issue I had that was indeed quite difficult to work though. 

I susgest that from how many people try to get Ubuntu onto any of the Inspiron series, that they sticky note the guide to the top of the fourms and provide good links to it.

See ya around.

Edit:   I forgot to add why I used the editor that I did. Being a Linux noob that I am, and not used to multitasking with Linux since Windows does not. "nano" offered a much more linear approach to the problem and for me that made it that much less complicated also when I first started working on Ubuntu, I was useing the Terminal opend with "Ctrl+Alt+F1" and it could not open up "gedit" only "nano" so it stuck with me.

---

### Post by Mr. Hibba on 2009-10-08
Hi, 

If you are still having the issue of the screen resolution not being able to be set higher than 800x600, I'd recommend clicking "System" on the top-left area of the screen, going down to "Administration", then the menu that pops out from that should have a selection called "Hardware Drivers." After clicking on it, it should automatically search for any available drivers and let you install them. If it finds a video driver (preferably one that has "recommended" next to it, if it finds more than one driver), I would recommend trying it, as that usually solves the resolution issue.

---

### Post by lavinog on 2009-10-08
> **Mr. Hibba said:**
> Hi, 

If you are still having the issue of the screen resolution not being able to be set higher than 800x600, I'd recommend clicking "System" on the top-left area of the screen, going down to "Administration", then the menu that pops out from that should have a selection called "Hardware Drivers." After clicking on it, it should automatically search for any available drivers and let you install them. If it finds a video driver (preferably one that has "recommended" next to it, if it finds more than one driver), I would recommend trying it, as that usually solves the resolution issue.

That particular card doesn't have a restricted driver.

Some of the older intel cards have issues with new software...I remember one model requires 16bit color instead of 24bit if you want 3d support.

---

### Post by wilee-nilee on 2009-10-08
> **Tavin237 said:**
> Thanks for the concern in all honesty though that is my spam email I use when ever I think I might get spam not my normal communication email.

As for an update on the laptop that Ubuntu 9.04 is on, an Inspiron 1100, it working great I've changed my Video Mem from 1MB to 8MB via my BIOS but I do not recall if that guide susgested that. Even still I have occasional video issues (I belive) such as that the (Linux Noob Speak) the desktop environment not always starting up nor am I able to get into the text base of Linux useing &quot;Ctrl+Alt+F1&quot;. I have yet to add any add-ons or packets at all asides the ones from the guide and the game Battle for Wesnoth. Saddly I don't belive that this computer has enough video mem to run it. =(

It works excelent right after the install and fix as an office computer and the GIMP program though a bit slow on this vurtual dinosour works fine with a bit of paticents on the user side.

Again I offer to anyone haveing the same problem if they need help I will be more then easy to help you walk though it, but as I said the email stated in my above post is my spam email and it make take me a little bit to reply.

I give Ubuntu on this rig   (AND I STRESS ONLY ON THE COMPUTER I AM USEING THE INSPIRON 1100)   a 3 and 1/2 out of 5, Partly because the computer itself is so old that to today's standards its a slow turtle that can't really be helped even with RAM upgrades, it would be cheeper to buy a computer for $300 on [www.newegg.com]("http://www.newegg.com") then add Ubuntu. Also for the video issue I had that was indeed quite difficult to work though. 

I susgest that from how many people try to get Ubuntu onto any of the Inspiron series, that they sticky note the guide to the top of the fourms and provide good links to it.

See ya around.

Edit:   I forgot to add why I used the editor that I did. Being a Linux noob that I am, and not used to multitasking with Linux since Windows does not. &quot;nano&quot; offered a much more linear approach to the problem and for me that made it that much less complicated also when I first started working on Ubuntu, I was useing the Terminal opend with &quot;Ctrl+Alt+F1&quot; and it could not open up &quot;gedit&quot; only &quot;nano&quot; so it stuck with me.

 Thanks for the update my friends computer is having problems with the desktop starting as well I had heard of the video cache being rather low. I have a inspiron 4100 and it runs like a champ with 512ram and 1gig chip. I have it running Koala but there are graphic problems because of the ancient ati radeon card, plays dvd's and video no problem, just a few desktop graphics starting in Koala.

---

### Post by Tavin237 on 2009-10-08
Keeping updated on this I've started to notice that there are still some bugs to be solved on this. Namely I seems the desktop environment tends to "Quit and Crash" at times. such as when I've had a few windows open in Pidgin and a few Tabs open in Firefox. Firefox quits and if I try to restart it with out a few minuets paused the entire system ether freezes up or crashes.

Now I'm not sure if this is just because I'm pulling too much of a strain on the computer or if theres a bug to be fixed some where. I've been running it easy now for a few hours with no problem. I'll keep updated if this problem persists I will try and solve it or if it is just Ubuntu being unstable I'll try to find a more stable configuration.

Edit: There are no drivers recommended drivers for the Inspiron 1100 with Ubuntu 9.04. The last time that the correct drivers were found from what I have gathered was in Ubuntu 8 or 7. I did try that as one of the original (hopeing to just be a quick fix) fixes, but to no avail.

---

