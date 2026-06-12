---
title: "Wifi wont connect after startup - need advice"
date: 2008-12-01
forum: Networking &amp; Wireless
---

### Post by keeper85 on 2008-12-01
Hey guys hoping I can get some help. heres my situation:

I'm brand new to ubuntu and loving it so far. Got some good help from these forums so far. One of the things i got help with is setting up my wifi adapter (Belkin f5d8053 usb N adapter). Anyway the walk through I followed basically added a wireless connection to the network settings. This all worked like a charm and I could browse fine until I restarted. Once I restarted all of a sudden the "Wireless Connection" disappeared from the network settings and hence wouldn't connect up to my wifi. 

Anyway after a bit of ******* around I worked out that to get it up and running i need to put the following into the terminal to make it work.

$ sudo modprobe ndiswrapper
then press enter
then enter my loggon password
then hit enter again and the wifi would connect back up

now im a real noob here and I have no idea what that bit of code actually does but I know it fixes my problem. what I want to know is if there is a way that I can get that lil piece of script to run automatically on startup so that I don't have to type it ever single time.

I know this stuff is probably really easy for some of you (I'm hoping so anyway) Thanks to all in advance. again im sorry for being such a noob as ive had Ubuntu now for 2 days lol if theres anything not clear pls ask.

Keeper

---

### Post by keeper85 on 2008-12-02
anyone have any ideas?

---

### Post by ubuntergeist on 2008-12-02
I have experienced the same problem. Every time I log out then logon again I have to type my password again, it doesn't work until I type the password again with the box "show password" checked. Just try this and see what happens, It might be just a bug in "network-manager".
Sometimes I have to type twice or three times to have it work properly. I haven't experienced this problem in the beta version. 

good luck

---

### Post by keeper85 on 2008-12-04
see if i log out and log back in it still works fine...its only when i restart that I have to run that lil code in terminal to get it working

---

### Post by keeper85 on 2008-12-05
Nothing at all? :(

---

### Post by aBitLater on 2009-02-04
Hey Keeper85 - was this resolved in another forum, or did you find an answer elsewhere?

I'm not versed enough to give you the answer, but I do know this can be done.

you might try searching here and google for startup scripts or bash startup scripts.

---

