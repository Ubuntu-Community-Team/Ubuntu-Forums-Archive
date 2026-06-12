---
title: "wireless router / can't connect"
date: 2006-09-16
forum: Networking &amp; Wireless
---

### Post by djillucid on 2006-09-16
TIA for all your help:

I've been using Ubuntu for about 24 hours now and I really like it. I've been a windows guy my whole life but times are changing. I have no clue what I am doing in Ubuntu, but I can't seem to get my wireless lan card to work. I followed some tutorial for a linksys card like i have but it doesn't work. On the bix, I just realized that it says min requirements are windows xp... does this mean it wont work on ubuntu??? ..or am I not doing something right? When I active eth02 (thats the wireless one) it takes a while and saysactivated, but the liht on the lan doesn't turn on, and of course it doesn't open any webpages other than the local start page. I am also new to firefox. What should I do please help!

- illucid

---

### Post by wieman01 on 2006-09-16
Not sure which model you are using but I have a "wusb54g v4" which works well with Ubuntu. The crux is to install a wireless container called "ndiswrapper" that deploys the native Windows driver (yes, the one that you have installed under Windows).

It's fairly easy to configure. Check it out and look for some howtos in this forum.

**EDIT:**

This is a ndiswrapper howto for Broadcom: [http://www.ubuntuforums.org/showthread.php?t=201902&highlight=ndiswrapper+howto]("http://www.ubuntuforums.org/showthread.php?t=201902&highlight=ndiswrapper+howto")

---

### Post by djillucid on 2006-09-16
Thanks, but I have tried using this so called ndiswrapper. I believe it returned some errors, which I have no clue what they mean. I followed the tutorials and didn't get it to work. Should I retry and write the errors???

---

### Post by wieman01 on 2006-09-16
Yeah... Post the errors. Perhaps you're missing something.

---

### Post by djillucid on 2006-09-16
I tried another persons script and it is still not working. I am following his trouble shooting 
I tried this:

sudo rmmod ndiswrapper
I got an error message saying Module ndiswrapper does not exist in /proc/modules


I have no idea but i means, but it doesn't sound right...


sudo modprobe ndiswrapper
Error message to the effect of error inserting, invalid argument

anything else I can do that would make it easier to help u help me?

---

### Post by djillucid on 2006-09-16
anyone help???

---

### Post by wieman01 on 2006-09-16
I think you're problem is that "ndiswrapper" is not correctly installed... Have you installed these packages?

[http://packages.debian.org/stable/source/ndiswrapper]("http://packages.debian.org/stable/source/ndiswrapper")

Fire up Synaptic and install otherwise you won't be able to install your Windows drivers.

**_EDIT:_**

You need to install "ndiswrapper-utils" to get it working. The remaining packages come with Ubuntu:

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper")

---

### Post by djillucid on 2006-09-17
I have installed and reinstalled the ndiswrapper several times. I checked in synaptic and it says its there and that I have the newest version...

When I tried to do the sudo ndiswrapper -m it said something about X (modprobe maybe?) already having an alias something??

and then I tried the sudo modprobe ndiswrapper and it gave an error of some sort like...

Error message to the effect of error inserting...kernel....invalid argument

---

