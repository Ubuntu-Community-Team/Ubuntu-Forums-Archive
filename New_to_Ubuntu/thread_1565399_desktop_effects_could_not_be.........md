---
title: "desktop effects could not be........"
date: 2010-08-31
forum: New to Ubuntu
---

### Post by charlier653 on 2010-08-31
Did a search, and found not much for 10.04. Most I found dealt with earlier distros, and were no help due to things not being where and what was suggested.

Have downloaded compiz-check, results:

```
Gathering information about your system...

 Distribution:          Ubuntu 10.04
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc RV535 [Radeon X1650 Series] (rev 9e)
 Driver in use:         radeon
 Rendering method:      None

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: No rendering method in use (AIGLX, Xgl or Nvidia) 
```

So how do I go about enabling a rendering method?

I have tried to use aticonfig, as suggested in system>preferences>ati catalyst control center. I get error: no supported adapters detected.

The error text from ATI CCC: 

```
There was a problem initializing Catalyst Control 
Center Linux edition.  It could be caused by the following.

No ATI graphics driver is installed, or the ATI driver 
is not functioning properly.
Please install the ATI driver appropriate for you ATI 
hardware, or configure using aticonfig.
```

From this, it might be safe to assume that Lucid knows that I have an ATI graphics adapter, just doesn't know what it is past that. 

No idea what to do about this situation.

---

### Post by silverglade00 on 2010-08-31
System - Administration - Hardware Drivers. Install the fglrx driver it should be offering.

---

### Post by charlier653 on 2010-08-31
Not offering one. Says no proprietary drivers are in use on this system.

Will see if I can get it with apt-get.

Quick update: no go, 

Results:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
fglrx is already the newest version.
fglrx set to manually installed.
```

---

### Post by alphacrucis2 on 2010-08-31
> **charlier653 said:**
> Not offering one. Says no proprietary drivers are in use on this system.

Will see if I can get it with apt-get.

Quick update: no go, 

Results:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
fglrx is already the newest version.
fglrx set to manually installed.
```


ATI dropped support for those older cards about eighteen months ago. The catch is that older versions of fglrx that do have support for the older cards don't work in Lucid (or Karmic for that matter). You need to stick with the default OSS driver. The OSS ATI drivers are under heavy development and it may be that the 3D support for you card is being done but hasn't made it to the Lucid repos yet. Hopefully someone will be along who can advise if there is a PPA for the OSS driver that had 3D support fro your card.

---

### Post by charlier653 on 2010-08-31
Thanks for that info.......didn't know I had an "old card", as I just purchased it a few months ago, new in box.

What I have right now is the xserver-xorg video radeonhd AMD/ATI r5xx r6xx display driver.

According to the more info page, this is what is supposed to be running this card.

So in essence, xgl, AIGLX, etc. will not start on my system, correct?

---

### Post by alphacrucis2 on 2010-08-31
> **charlier653 said:**
> Thanks for that info.......didn't know I had an "old card", as I just purchased it a few months ago, new in box.

What I have right now is the xserver-xorg video radeonhd AMD/ATI r5xx r6xx display driver.

According to the more info page, this is what is supposed to be running this card.

So in essence, xgl, AIGLX, etc. will not start on my system, correct?

One way to tell for sure on the support question is to go to ATI/AMD's website and go to the download graphics driver section. Enter the details of your card and OS and it will offer to download the latest version of the driver for your card. If it offers Catalyst 10.8 then you know your card is still supported by the latest fglrx. If it only offers Catalyst 9.3 then you know you are out of luck for using the proprietary driver with Lucid.

---

### Post by andrewthomas on 2010-08-31
> **charlier653 said:**
> 
What I have right now is the xserver-xorg video radeonhd AMD/ATI r5xx r6xx display driver.


Delete the radeonhd and use xserver-xorg-video-radeon

---

