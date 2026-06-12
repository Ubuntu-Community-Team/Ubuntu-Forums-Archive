---
title: "RTL 8185 yet still"
date: 2008-03-29
forum: Networking &amp; Wireless
---

### Post by jjgauthi on 2008-03-29
Okay totally at wits end here.

I've read mutliple posts, even tried the majority of what they suggest regarding the rtl8185 wireless network card.  Here is sumation of what I have tried to date....

First things first, I have tried three versions of Ubuntu (6.06, 7.10, currently 8.04) to limited degrees of success.

Under 6.06 it will at least let me recognize wireless networks, under 7.10 I get a hard lock of my computer when I try to connect to wireless networks, under 8.04 it dosn't even recognize wireless networds.

1) went to realtek's site and downloaded the windows XP drives which were suggested, 
2) installed ndiswrapper - as suggested
3) installed the driver (rtl8185.inf and rtl8185.sys) as required when i ran *ndiswrapper -i rtl8185.inf*
4) did a ndiswrapper -l, here it now tells me its an invalid driver
     a) how do I remove a driver so that I may try something else?
5) its a laptop so the option of ripping out the network card and replacing it are not there
   a) its a gateway W340UI laptop, with a realtek 8185 network card
6) when I do a lshw it tells me that the wired connection works but I dont have a CAT cable to hook it up to my router so i'm not sure if it truely works or not
    a) it also tells me now under 8.04 that the network is unclaimed unlike 7.10 where it says it was disabled

Been trying to get this to work for two weeks, I'm new to unix and my other option is vista which sucks.  I've not really been able to comprehend what most of you are saying when you describe most of what you say to fix the issue, such as compile from binaries (this sounds like something from star trek).

Please if anyone can help with a small guide that is written for morons that would be great, Baby Jesus is Crying because I can't get network working on my laptop.

---

### Post by dstew on 2008-03-29
> did a ndiswrapper -l, here it now tells me its an invalid driverThere should be a directory /etc/ndiswrapper/rtl8185 created when you install, and the .sys file should be in there. Can you look to see if the .sys file is there?```
ls -l /etc/ndiswrapper/rtl8185
```If it is not there, copy it to that directory. Also, is the original rtl8185.sys file that you got from Windows named with upper case or lower case characters? If upper case, change the file name to lower case.

---

### Post by jjgauthi on 2008-03-29
I appreciate your help on this got it to work finally.

Downloaded ME drivers which coincidentally have the 98 driver in a sub-folder (this is the key to  me getting it working)  - There is a post on here if you search for RTL8185, that guy really saved my bacon from blowing up my computer.  It is called RTL8185 fresh install he gives you all the commands you need.

One thing I managed to do with reading the man pages on ndiswrapper was to uninstall the previous driver that was xp based.  Once again the 98 drivers are the key follow his instructions and you will have wireless in no time flat.

I upgraded to 8.04 because that is what someone suggested, but i'm not sure if it works under 7.10 but it should if follow basic logic.

Once again thanks all you Ubuntu maniacs.  Now to figure out what to do with the awesomely goodness of Ubuntu.

---

