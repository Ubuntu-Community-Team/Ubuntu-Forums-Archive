---
title: "I Can't connect to my lynksys!"
date: 2008-05-04
forum: Networking &amp; Wireless
---

### Post by summuner848 on 2008-05-04
I installed Ubuntu 8 yesterday, and I have tried everything i could find on how to connect to my wireless internet from my laptop. I know that the network is on and working because Windows Vista can still connect (other partition on the same laptop) and My mom's laptop can still connect. Every technique i found involved connecting to the internet to download ndiswrapper or whatever it is. Of course, that way is logical, just one problem, I CANT DOWNLOAD NDISWRAPPER! Also, I tried connecting directly by plugging a usb into my modem. But none of these settings make sense! As you can see by my post count/rating thingy, I'm a complete newb at linux. Please give me some idea as to what i can do to connect to the internet from Ubuntu.

Edit:

 * I believe i am running hardy heron
 * I have a broadcom BCM94311MCG wlan mini-PCI (rev 02)


 * DFSHJWAHABLAHWAAAAA!!!!!!!!!! okay, i got it to connect via a wired connection, now, all i need it to do is figure out how to go wireless, please help

---

### Post by CleverJake on 2008-05-04
I had alot of similar problems when I first got ubuntu on my laptop

few things to find out first

what ubuntu are yo urunning (feisty/hardy, etc)
are networks available to be seen and just not able to connect
do you know your wireless card/chipset

---

### Post by xyphur on 2008-05-04
Hi there. This should be a fairly straightforward fix. I have a Broadcom-based wireless card in my laptop, and I have it working under both Feisty and Hardy. The only variable really is what chipset exactly your card uses. Mine's a BCM4306 card.

To find out what it is, and what version of Ubuntu you have, post the output of these separate terminal commands:

uname -r

-and-

lspci

Once we know what type of hardware we're dealing with, getting proper drivers for it so it'll work as expected will be much easier. :)

---

### Post by summuner848 on 2008-05-04
sorry about not naming the chipset, i did not know what exactly it was before, but i have a BCM94311 wlan mini-PCI (rev 02)

I hope that helps

---

### Post by Charlie708 on 2008-05-04
I got a 4311 (packaged under Dell 1390) and it was a real pain to get it to work.  What worked the best for me was using fwcutter.  I can't remember the steps offhand, but I will back track and see what guide I used.  I also tried Ndiswrapper, but it didn't work at all for the card.

I just tried this, check it out:
[http://forums.fedoraforum.org/archive/index.php/t-152871.html](http://forums.fedoraforum.org/archive/index.php/t-152871.html)

---

### Post by kwacka on 2008-05-04
The thread at [http://ubuntuforums.org/showthread.php?t=475963&highlight=BCM4311](http://ubuntuforums.org/showthread.php?t=475963&highlight=BCM4311)

might be useful?

---

### Post by summuner848 on 2008-05-04
..bump..

---

### Post by summuner848 on 2008-05-05
Solved!!! Yay

---

