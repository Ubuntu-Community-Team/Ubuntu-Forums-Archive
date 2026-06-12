---
title: "HP Stream 11-inch Ubuntu 14.04 WiFi Issue (Broadcom 43142)"
date: 2015-10-23
forum: Networking &amp; Wireless
---

### Post by david447 on 2015-10-23
Hello Ubuntu Universe!

I recently purchased an HP Stream 11-inch and installed Ubuntu 14.04. Here's the deal:

_Issue_
When the HP Stream's wifi works, it works really well, at least in terms of the speed. The trouble is, the wifi disconnects a lot, and is generally unstable. This is a big problem because the laptop is a netbook!

```
sudo lshw -C network
```

```
description: Wireless interface
product: BCM43142 802.11b/g/n
vendor: Broadcom Corporation
driver:  wl0
driver veresion: 6.30.223.248 (r487574)
```

Any help would be greatly appreciated :)!

---

### Post by Beren Camlost on 2015-10-23
Sadly, 6.30.223.248 is the latest version of the driver bundled with Ubuntu. It's fairly old.

 Broadcom released version 6.30.223.271 back in January this year but for some reason it hasn't been picked up by Ubuntu yet. I have a bcm4360 and my own solution to the problem was to download the latest source code from [Broadcom]("https://www.broadcom.com/support/?gid=1") and compile it myself. The documentation can be found [here]("https://www.broadcom.com/docs/linux_sta/README_6.30.223.271.txt").

May I ask what kernel you are using?
```
$ uname -r
```

Since an easy installable recent driver is not available for Ubuntu I have considered building the kernel module with dkms and put it up in a PPA, as I bet the Broadcom wifi chips are fairly common by now.

---

### Post by Bucky Ball on 2015-10-23
> **Beren Camlost said:**
> Sadly, 6.30.223.248 is the latest version of the driver bundled with Ubuntu. It's fairly old.
... my own solution to the problem was to download the latest source code from [Broadcom]("https://www.broadcom.com/support/?gid=1") and compile it myself. 

It is old, but still works for many just fine. Just curious as to if you were having the exact same problem as the OP or the problem was the latest driver wasn't in the official repos? Or was it flaky wifi?

@OP: Just to make sure you are up to date with the kernel for 14.04, do these commands one after the other:

```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```	

Report any and all errors here, then run the command given by Beren Camlost above:

```
uname -r
```	

or 

```
uname -a
```	

Either will do. Also, give us the output of 'sudo lshw -C network' again, please. 

There are a number of [solutions here]("http://askubuntu.com/questions/459654/drivers-for-broadcom-bcm43142-on-ubuntu-14-04-trusty-tahr") which do not involve installing a driver which is not in the repos. The first with the [7] next to it has some interesting info, but have a dig around there. Also much to be found with a [search for your issue]("https://duckduckgo.com/?q=BCM43142+ubuntu+14"). 

Let us know how you go.

---

### Post by Beren Camlost on 2015-10-24
> **Bucky Ball said:**
> Just curious as to if you were having the exact same problem as the OP or the problem was the latest driver wasn't in the official repos?

My problem was pretty much the same as OP, frequent disconnects and general instability. The same high-end wireless PCI card works flawlessly in Windows so I do blame the Broadcom linux drivers.

Most solutions I've found involves either reinstalling the driver (which didn't do any difference in my case) or compiling the latest driver yourself. I realize that the latter is not the ideal solution for most and by all means if we can come up with a better solution for the OP, all the merrier.

I will look into setting up a PPA nevertheless as it does appear quite a lot have troubles with instability with these Broadcom chips.

---

### Post by david447 on 2015-10-24
> **Bucky Ball said:**
> It is old, but still works for many just fine. Just curious as to if you were having the exact same problem as the OP or the problem was the latest driver wasn't in the official repos? Or was it flaky wifi?

Wifi is very strong and works on all of my other devices (OSX, Windows 10, iOS etc.)

> **Bucky Ball said:**
> 
Report any and all errors here, then run the command given by Beren Camlost above:

```
uname -r
```    



```
3.19.0-31-generic
```
  

> **Bucky Ball said:**
> Either will do. Also, give us the output of 'sudo lshw -C network' again, please.
It's the same wifi driver (based on the id)

> **Bucky Ball said:**
> There are a number of [solutions here]("http://askubuntu.com/questions/459654/drivers-for-broadcom-bcm43142-on-ubuntu-14-04-trusty-tahr") which do not involve installing a driver which is not in the repos. The first with the [7] next to it has some interesting info, but have a dig around there. Also much to be found with a [search for your issue]("https://duckduckgo.com/?q=BCM43142+ubuntu+14").

I'll have to take a look at both links. 

Thank you very much Bucky and Beren! While I don't have a solution yet, perhaps I will in the near future.

---

### Post by Bucky Ball on 2015-10-24
As Beren mentions, seems some people are having some issues with this, but some are fixing without compiling the new Broadcom driver and others, as evidenced by Beren, are not and having to compile the driver.

Guess they made a few different versions of the Stream, perhaps with different components for different countries or perhaps for different versions of the machine. My model is the 11-d008 TU. I am in Australia. Wireless worked 'out of the box' but different card to yours as I mentioned in your other thread.

---

### Post by david447 on 2015-11-05
> Guess they made a few different versions of the Stream


I had suspected the same thing Bucky. It's interesting how under the hood, there is variation in manufacturing. I first became aware of this when I was considering purchasing my MacBook Pro and learned that some of the displays were manufactured from LG and some from Samsung. At the time (2012 or 2013) LG screens had an issue, but the Samsung screens did not. Getting a clean copy of the machine was not a guarantee.


Hoping to get the wifi working in a robust manner, else it will become a small typewriter :-)

---

### Post by david447 on 2016-01-18
Hi there,

So I got some time to play around with this again and still no luck getting consistent wifi. It connects, but will not consistently do so. It makes the computer fairly useless sadly. I may be forced to put Windows back on it unless someone knows a way to get this particular Broadcom wifi chip working. Any help would be appreciated!

David

---

### Post by Bucky Ball on 2016-01-18
Or buy a five or ten dollar USB that works 'out of the box', and many do, until the driver for your internal wireless card is up to scratch ...

After an update one day it will suddenly spring to life. It's happened to me in the past. :)

---

### Post by david447 on 2016-01-19
I didn't even think of that. Just purchased one for $10 that folks are saying works with Linux. Will let you know if it works. Thanks BB!

---

### Post by Bucky Ball on 2016-01-19
Yea, I generally have a few of them lying around for those 'special occasions'. I use them less and less as more cards are covered but it's always the same with very new (or very problematic) cards. If the manufacturers don't supply much, or any, Linux support, it is up to the community to grab one of the blighters, figure out how it ticks, work out a driver for it, code it, blah, blah ...

---

### Post by Leon A on 2016-12-01
> **Bucky Ball said:**
>  Guess they made a few different versions of the Stream, perhaps with different components for different countries or perhaps for different versions of the machine. My model is the 11-d008 TU. I am in Australia. Wireless worked 'out of the box' but different card to yours as I mentioned in your other thread.

I have acquired HUNDREDS of HPStream11 model11-d010wm here in USA and about half of them use BCM43142 cards and the others use RTL8723be. Sometimes the FCC wireless info stamped on the bottom doesn't even agree with the card that is installed inside! It seems that whichever card was available or cheaper the day the laptop ran down the assembly line was installed !I've found awork-around solution for linux drivers for the RTL cards but not for these BCM.

---

### Post by Bucky Ball on 2016-12-01
This thread hasn't been touched for nearly a year. You may be talking to a brickwall but thanks for sharing. ;)

---

### Post by wildmanne39 on 2016-12-02
Old thread closed.
If you have a support question please start a new thread and post the information from the wireless script in my signature.
Thanks

---

