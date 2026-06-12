---
title: "very green user, need help with ndiswrapper"
date: 2010-10-25
forum: New to Ubuntu
---

### Post by flyguyeddy on 2010-10-25
Ok, i have an asus eeepc 1001px with an atheros wifi internal wifi card.  Im pretty sure ive got the latest version of ubuntu (i just downloaded it amd installed it the day before yesterday).  

Anyway i was reading a writeup on how to use ndiswrapper and im a little confused.  How do i blacklist the current drivers?  It said to edit a specific file, but i cant seem to figure that out.  Help?

---

### Post by fatality_uk on 2010-10-25
From what I know, the atheros wifi should work. What writeup were you following?

---

### Post by flyguyeddy on 2010-10-25
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

Im running 10.04 lucid lynx i believe.  My computer doesnt see my connection is why im doin this.

---

### Post by anewguy on 2010-10-25
From what I saw in that thread, it is trying to get you to blacklist the old Broadcom drivers.  If you don't have a Broadcom adapter there is no need to do it.

Let's check a few things first:

- if you right click on the network manager icon, is the "Enable Wireless" checked?

- is your router broadcasting the network ID, or is it hidden?  If it is hidden, it won't show and you have to manually set up the connection via network manager.


Let's also see what you actually have for an adapter:

- open a terminal window (Applications/Accessories/Terminal)
- type:

lspci > anewguy.txt

lsusb >> anewguy.txt

lshw -C network >> anewguy.txt

ifconfig >> anewguy.txt

iwconfig >> anewguy.txt

The first ">" tells it to pipe the output to a file called "anewguy.txt".

The rest of the commands have ">>" to say to append to the file.

Then, post back here and use the attach function (it's the paperclip on the menu line) and attach the file anewguy.txt.

That way we can take a look at everything.

Dave ;)

BTW - have you already tried loading a driver with ndiswrapper?  If so, we'll need to clean that up first before we try to go beyond the information I requested.

---

### Post by flyguyeddy on 2010-10-25
i dont have an internet connection on the laptop in question, so i have to cut and paste that file with an sd card with my windows server2008r2 equipped dell laptop.  


i have not installed any drivers that i know of, but i did install the files it told me to download.

---

### Post by flyguyeddy on 2010-10-25
here ya go.  when i typed in the iwconfig one it said an error message like this :  

lo    no wireless extensions
eth0   no wireless extensions

---

### Post by anewguy on 2010-10-25
Okay, so now we know you have Atheros AR8132 wireless adapter.  The next step is to use the search function of the forum to see if anyone has reported problems or a fix for it.  In addition, an internet search with AR8132 and ubuntu should turn something up.

I'll try to do a little of that myself, but you might want to try also.

Dave ;)

BTW - since you are new to ubuntu, I created a new thread for help on getting a driver working for your adapter in 10.10.  That way if there are any replies it can help others, and I can try to weed through anything that might be more technical and try to give easier instructions to follow.

---

