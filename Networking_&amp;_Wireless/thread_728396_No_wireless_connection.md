---
title: "No wireless connection"
date: 2008-03-18
forum: Networking &amp; Wireless
---

### Post by skullins on 2008-03-18
I was using 7.10 but couldn't get my sound to work then updated to 8.04 and that fixed my sound issue. The thing is now when I go into network settings there is no wireless option. It worked fine using 7.10 and I just put in the Live CD and it still worked fine.

My card is Atheros AR242x 802.11abg Wireless PCI Express Adapter (rev 01).

I'm very new to Ubuntu, installed two days ago, so I have no clue what to do. I tried searching around here but couldn't seem to find anything that related specifically to this card running 8.04.

Thanks for any help.

---

### Post by uberlube on 2008-03-18
First off, you will need your windows wireless drivers for your chipset. You may have them on CD or you can grab the from their website. Then install ndiswrapper from the repositories and use this guide to install the firmware:

[http://ubuntuforums.org/showthread.php?t=574501&highlight=ndiswrapper](http://ubuntuforums.org/showthread.php?t=574501&highlight=ndiswrapper)

Hope this helps :)

---

### Post by skullins on 2008-03-18
Alright I'll take a look at that and see how it goes.

Thanks for replying so quickly.

---

### Post by uberlube on 2008-03-18
Post back here if you have any problems. I'll try to help you out as much as I can.

---

### Post by skullins on 2008-03-18
Alright this is where my lack of ubuntu skills becomes very transparent haha...

I got the ndiswrapper and it's telling me to place the file in the ~/ndiswrapper directory. Now thing is I don't know how to get to that directory and do I put the actual .tar file in there or do I extract it and put the folder in there?

---

### Post by uberlube on 2008-03-18
Did you download ndiswrapper from a website or the repositories?

---

### Post by skullins on 2008-03-18
From a website.

---

### Post by uberlube on 2008-03-18
k just delete that file. Go into the synaptic package manager and search for ndiswrapper. Click the box beside it and go 'apply' and then it will install it for you. he repositories are the best way to go to install most software.

---

### Post by skullins on 2008-03-18
Ok I tried that but got an error. I'm not connected to the net so it won't work haha I'm using my wifes laptop to talk here. I downloaded the file on her computer, burned it to disc, then transferred it to my laptop.

I guess I need to use the file I downloaded.

---

### Post by uberlube on 2008-03-18
A) Cant you just hook up your computer to the internet with the Ethernet cord plugged into your wifes cpu? 

b) There should be some instructions that came with the download on how to install it. What is the file name? Where did you get it from?

---

### Post by skullins on 2008-03-18
A) I could but she is busy working on it tonight so I can't unplug here haha

B) There are instructions but I need to be online it seems to do it. The file is ndiswrapper-1.5.2.tar.gz

I'm going to just wait until tomorrow when I can hook my laptop up to the internet. Seems that will make this a whole lot easier.

Thanks for your help.

---

### Post by uberlube on 2008-03-18
np good luck.

---

### Post by skullins on 2008-03-19
Ok I hoked up the internet with the ethernet cord and installed ndiswrapper through repositories. Then I went and got the driver off Toshibas site. Now I'm at this step....

Next create and place your Window's wireless driver into ~/driver:
Code:

cd ~
mkdir driver
cd driver

Ensuring the ***.sys and ***.inf file for the Window's driver are in the~/driver directory:
Code:

sudo ndiswrapper -i *****.inf




How do I put the driver in /driver?

---

### Post by skullins on 2008-03-19
Alright I got it fixed...

I installed ndiswrapper through repositories then I downloaded my windows wireless drivers. I extracted the .zip and then went to system>administraion>windows wireless drivers and added the .inf I got in the .zip and it worked.

---

