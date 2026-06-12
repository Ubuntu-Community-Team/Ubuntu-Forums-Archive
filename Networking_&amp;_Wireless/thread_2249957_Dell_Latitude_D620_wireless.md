---
title: "Dell Latitude D620 wireless"
date: 2014-10-25
forum: Networking &amp; Wireless
---

### Post by archeryrob on 2014-10-25
Having a little trouble setting up the wireless on a Dell Latitude D620. I an trying to setup this old laptop for my dad, possibly. I just did a new install of 14.04.1 LTS and its up and working fine. I can get a hardwire network connection to work great, but I need wireless also. I put in my wireless settings but it will not connect. I know its needs drivers, but can't find anything to install, but one and it did not work.

A web search pull this up and and I ran the below terminal line. It went out and found it and installed it, but I am not sure if I have the correct card.
[http://www.linlap.com/dell_latitude_d620](http://www.linlap.com/dell_latitude_d620)
> sudo apt-get install b43-fwcutter firmware-b43-installer

I went into terminal an found its the Broadcom BCM4311 wireless card 802.11 a/b/g 32 bit 33 mhz
Any ideas on where I should look for the correct driver?

I found this to help, but can't figure out where the stright up and down slash is on the keybaord to type into terminal. Yes, I am not a terminal man. :)
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx]("http://lspci -vvnn | grep 14e4")
> lspci -vvnn | grep 14e4

---

### Post by QIII on 2014-10-25
I'm wondering if the kernel contains the driver already.  I installed Fedora on my D620 without incident, using wireless from the live media.

Does the app indicator show that there is a wireless network and you are just not able to connect to it?

---

### Post by weatherman2 on 2014-10-25
> **archeryrob said:**
> 

I found this to help, but can't figure out where the stright up and down slash is on the keybaord to type into terminal.

That | is called a "pipe" in Unix/Linux land.  On your keyboard, look below the Backspace key (shift - \ ).

Broadcom wireless cards are historically difficult in Linux because of the proprietary nature of the firmware, so some parts of the driver aren't packaged with a default install of Ubuntu for some cards for legal reasons.  I almost always replace a Broadcom wireless card with an Intel card in part for that reason.  But it should be easy to get it working once you have the right recipe.  Someone else here will come along to help - stay tuned!

When I do try to get these card to work, the first thing I usually do is search for "Additional Drivers" and see if an alternative driver is suggested for your Broadcom card.  It may simply need to be activated - and being wired to the internet temporarily usually works best for that...

---

### Post by weatherman2 on 2014-10-25
You may also need to enable the card - either with a hardware toggle switch or using a function key (Fn - F2 I think on many Dells).  You might want to run the wireless script given in the "sticky" at the top of this forum to show the current state of your networking and drivers, then post the output here.

---

### Post by QIII on 2014-10-25
On the D620 there is a switch on the left side of the case.

Creating a Live USB with Ubuntu to check this out.

---

### Post by QIII on 2014-10-25
OK.  Sorry it took a bit.  Had to do something.

With a Live USB, my D620 with the same wireless hardware is connecting just fine.

So I think you need to first check that the hardware switch is on and be sure that you are entering the right credentials for your wireless network.

Failing those, please provide the results of the script as mentioned.

---

### Post by archeryrob on 2014-11-09
> **QIII said:**
> On the D620 there is a switch on the left side of the case.

Damn, talk about a rookie mistake! :oops: I'm a desktop user and hardly use a laptop and total forgot you cut switch off the wireless card!

---

