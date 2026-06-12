---
title: "Hardy Heron on Inspiron 1521 network troubles"
date: 2008-06-18
forum: Networking &amp; Wireless
---

### Post by jfleming9232 on 2008-06-18
Well, I finally swapped my Inspiron 1521 to Ubuntu and now I have no internet connection.  The system is a Dell Inspiron 1521 AMD 64 Athlon X2.  After searching some of the threads, I have managed to get the following information but I don't know what to do with it.  Any help would be greatly appreciated.

---

### Post by jfleming9232 on 2008-06-19
bumping

---

### Post by molotov00 on 2008-06-19
You're going to need to clarify what's going on here. Bumping alone isn't going to do anything.

"no internet connection"

Does that mean you misplaced your network chord, your ISP cut your service, your wireless drivers aren't working, or you can ping computers on the network but cannot access the internet?

The command you ran returned "WARNING: ..." that means to run the command as a super user. Next time when you get that error, use 'sudo command'.

I could ask you run a bunch of commands but first clarify exactly what your problem is. And are you working with a wireless or wired connection? Is a built-in network card? How's your network set up?

---

### Post by jfleming9232 on 2008-06-19
My home internet connection is a DSL modem.  When I connect the computer to the modem, I recieve a "No network connection" message when I hover over the network icon.  I have tried resetting the modem but to no avail.  When I try a manual connection, I still get the same message and I am unable to connect to the internet.  It would also appear that my wireless card is not even being recognized by Ubuntu.  lshw -C network returns the results in screenshot1.  When I right-click the network icons and go to Edit wireless networks, I can't find any and I know there are three good signals at my location.  These problems started after a clean install of Ubuntu Hardy Heron.  I admit that I am really new at this, so any help you could give would be greatly appreciated.

---

### Post by danbodoh on 2008-06-19
To get your wireless working, search the forums for "Broadcom 4328".  You'll probably find similar information for you wired port, by searching similarly.  In short, you'll have to use ndiswrapper with the windows driver.

Dan Bodoh

---

### Post by jfleming9232 on 2008-06-20
Thanks for the info.

---

