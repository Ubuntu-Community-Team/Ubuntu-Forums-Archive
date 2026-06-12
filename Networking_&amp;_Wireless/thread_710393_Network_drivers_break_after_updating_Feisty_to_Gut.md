---
title: "Network drivers break after updating Feisty to Gutsy"
date: 2008-02-28
forum: Networking &amp; Wireless
---

### Post by Nichololas on 2008-02-28
I have Feisty installed on my Dell Inspiron 6400 with a Broadcom BCM4401-B0 100Base-TX (rev) ethernet controller. My wired and wireless network connections both worked out of the box but when I updated to Gutsy using the Update Manager they both broke and it said that no Network Devices could be found (or something to that effect). I tried various things to get it working again, like ndiswrapper, but basically it wasn't coming back and the easiest way I saw was to reinstall. Is there any way I can get the update without changing any network settings? Please keep in mind I'm pretty new to Linux.

---

### Post by myddewji13 on 2008-02-28
ur gonna have to use ndiswrapper....if your pretty new..try this tutorial:
[http://ubuntuforums.org/showthread.php?t=709447](http://ubuntuforums.org/showthread.php?t=709447)

also post the results of 'lspci' in terminal to figure out wat type of card you have...

---

### Post by Nichololas on 2008-02-28
Well, it's working as it is, without ndiswrapper. I'd rather not change it if I can help it, as I didn't get it working last time. 

lspci shows this:

03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)

---

### Post by myddewji13 on 2008-02-28
well if its working then theres no problem?

---

### Post by Nichololas on 2008-02-28
It stopped working after I updated to Gutsy. See title and OP ..

---

### Post by myddewji13 on 2008-02-28
so have you tried to use ndiswrapper + gutsy to make it work?

---

### Post by Nichololas on 2008-02-28
Giving ndiswrapper another shot. Should I do it after I install Gutsy or can I do it before - i.e will the updates change anything related to it?

---

### Post by myddewji13 on 2008-02-28
do it after installing gutsy...and if you can..try doin a clean install...ie..backup files ... download iso....install over prev version...then update....and then follow the above tutorial (my prev post)... with you drivers..r

---

