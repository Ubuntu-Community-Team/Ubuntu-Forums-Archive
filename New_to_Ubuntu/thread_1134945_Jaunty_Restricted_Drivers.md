---
title: "Jaunty Restricted Drivers"
date: 2009-04-24
forum: New to Ubuntu
---

### Post by spikoley on 2009-04-24
I just installed Jaunty with out an internet connect.  My usual restricted drivers are not showing up under Hardware Drivers.  How can I get Hardware Drivers to show the restricted device so I can enable them.  They are for my graphics and wireless card.

---

### Post by Peter09 on 2009-04-24
Just a Sanity Check here - are you sure that the wireless etc is not already working?

---

### Post by spikoley on 2009-04-24
> **Peter09 said:**
> Just a Sanity Check here - are you sure that the wireless etc is not already working?

The wireless card is recognized, but does not work.  It does not see any wireless networks.  I had to use a pcmcia card to get online.  The internal card is a Broadcom card which always works after I enable it in restricted drivers.  Usually my video card will show up in there too.

```
Broadcom Corporation BCM4309 802.11a/b/g (rev 03)
```
```
ATI Technologies Inc M22 [Mobility Radeon X300
```

---

### Post by Peter09 on 2009-04-24
Does this link help for your wireless connection?

[http://ubuntu-utah.ubuntuforums.org/showthread.php?p=6928676](http://ubuntu-utah.ubuntuforums.org/showthread.php?p=6928676)

---

### Post by spikoley on 2009-04-24
> **Peter09 said:**
> Does this link help for your wireless connection?

[http://ubuntu-utah.ubuntuforums.org/showthread.php?p=6928676](http://ubuntu-utah.ubuntuforums.org/showthread.php?p=6928676)

That link should work, but i want to fix the Restricted Drivers feature.  Is there any command I can run to check for devices that need Restricted Drivers?

---

### Post by Peter09 on 2009-04-24
I suspect that Ubuntu thinks it has installed the correct driver - so why look for a restricted one :)

---

### Post by spikoley on 2009-04-24
> **Peter09 said:**
> I suspect that Ubuntu thinks it has installed the correct driver - so why look for a restricted one :)

Restricted devices still show up under Hardware Drivers even when the right ones are installed.  There has to be a command to find restricted devices.

---

### Post by IceyBlack on 2009-04-24
Hi guys i have this VGA 00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03) and it works ok in ubuntu 8.04 and 8.10 no need driver or something and now after upgrade to jaunty i cannot nebale desktop effect , how can i activate the driver?Laptop Fujitsu Siemens amilo 2727.
On system >> Administration >> Hardware Drivers appear only the wifi card.
Please help .

---

### Post by Peter09 on 2009-04-24
IcyBlack - please start a new thread for this as its not considered 'polite' to jump into someone elses thread.

Howver look here
 [https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)

---

### Post by IceyBlack on 2009-04-24
Oh sorry about that i thought is the same problem for all about drivers in ubuntu jaunty.

---

### Post by Peter09 on 2009-04-24
IcyBlack - its ok - :)

---

### Post by spikoley on 2009-04-24
Back to the topic at hand.  I rebooted then went into Hardware Drivers and it started a search.  It found the Broadcom driver but not the ATI.  I know there has been a lot of work done on the ATI.  My guess is it's running on the open source driver.

---

### Post by Peter09 on 2009-04-24
There are issues with the ATI drivers, I believe some cards are not supported at present.

---

### Post by spikoley on 2009-04-24
> **Peter09 said:**
> There are issues with the ATI drivers, I believe some cards are not supported at present.

The current drivers seem fine because Compiz is working great.  Older versions use to crash.  Hats off to the developers.  Jaunty Rocks!!!

---

### Post by peakpc on 2009-04-24
I have tried fresh installs both 64bit and 32bit but neither will give me a working wireless. broadcom wireless seems to exist but not functional. will not find restricted drivers (like 8.10 did). how did you get restricted drivers to magically show up for the wireless?:confused:

---

### Post by El Zoido on 2009-04-24
Hm, this may be related:

When I installed Jaunty yesterday the restricted drivers for the graphics card didn't show up for me, too.
I first had to restart the PC before I could select them.

Have you activated all the software-repositories (including 3rd party?)

---

### Post by spikoley on 2009-04-24
> **peakpc said:**
> I have tried fresh installs both 64bit and 32bit but neither will give me a working wireless. broadcom wireless seems to exist but not functional. will not find restricted drivers (like 8.10 did). how did you get restricted drivers to magically show up for the wireless?:confused:

I did a complete shutdown, booted and then went into Hardware Drivers.  This time it automatically did a search before it opened.

---

### Post by peakpc on 2009-04-26
I figured out what was missing, so...

 I used synaptic to search "broadcom" and  load b43-fwcutter which ran immedately,
 then after a reboot the wireless started working.  

I Checked the hardware drivers and noticed that my card was listed there now:).
 All is well but an anying glitch to say the lest.:( 

I hope that this post will help others that are in the same boat.

---

