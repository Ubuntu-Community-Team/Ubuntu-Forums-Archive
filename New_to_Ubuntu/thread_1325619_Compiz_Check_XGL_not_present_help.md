---
title: "Compiz Check XGL not present help"
date: 2009-11-13
forum: New to Ubuntu
---

### Post by myadav on 2009-11-13
Dear Senior members,
I seem to have somehow managed to activate desktop effects however still have not been able to use compiz.
In the terminal when I type compiz, it reads
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1366x768) to maximum 3D texture size (4096): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: present. 
running under gnome seesion, checking for gnomecompat
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

What do you think is wrong here?
What steps should I take to fix this error?

---

### Post by 909-1 on 2009-11-15
I had the same problem after doing a custom minimal install.

I installed simple-ccsm. This wasn't enough.

Installing the 'compiz' package from Synaptic fixed it for me.

---

### Post by coldReactive on 2009-11-15
> **909-1 said:**
> I had the same problem after doing a custom minimal install.

I installed simple-ccsm. This wasn't enough.

Installing the 'compiz' package from Synaptic fixed it for me.

User already has compiz, hence why the user gets that message.

XGL won't work on ATI nor Intel.

---

### Post by myadav on 2009-11-16
during my previous install it was working and I manged to get compiz working, I don't really know how but it did.
I am sure there is a process or something that I seem to be missing.
Would somebody please help!!

---

### Post by jocko on 2009-11-16
> **myadav said:**
> during my previous install it was working and I manged to get compiz working, I don't really know how but it did.
I am sure there is a process or something that I seem to be missing.
Would somebody please help!!
Don't mind the "XGL not present" message. Xgl was only needed on the old proprietary ati driver, before they managed to get compositing support in the driver.

To get any help with your problem, you need to give us at least two pieces of information:
What graphics card do you have?
Which driver does it use?

---

### Post by Kevbert on 2009-11-16
I get that message, but can use compiz-fusion fine. In most cases compiz is compatible with Intel, Nvidia and ATI graphics. Please enter the following in Applications-Accessories-Terminal and post back the reply
```
lshw -C display

```
Please also take a look at [[COLOR="Red"]this[/COLOR]]("http://forlong.blogage.de/entries/pages/Compiz-Check").

---

### Post by myadav on 2009-11-16
> **jocko said:**
> Don't mind the "XGL not present" message. Xgl was only needed on the old proprietary ati driver, before they managed to get compositing support in the driver.

To get any help with your problem, you need to give us at least two pieces of information:
What graphics card do you have?
Which driver does it use?

Thank you Sir, I really appreciate your kind gesture  
 in taking out time to help me out.

My graphic card is GMA 500
I used the guide to install the Poulsbo drivers, I guess which is the right driver.
[http://ubuntuforums.org/showthread.php?t=1229345](http://ubuntuforums.org/showthread.php?t=1229345)

---

### Post by myadav on 2009-11-16
> **Kevbert said:**
> I get that message, but can use compiz-fusion fine. In most cases compiz is compatible with Intel, Nvidia and ATI graphics. Please enter the following in Applications-Accessories-Terminal and post back the reply
```
lshw -C display

```
Please also take a look at [[COLOR="Red"]this[/COLOR]]("http://forlong.blogage.de/entries/pages/Compiz-Check"). 

Dear Sir,
In terms of your instructions, I executed the command and the result is 
you should run this program as super-user.
  *-display               
       description: VGA compatible controller
       product: System Controller Hub (SCH Poulsbo) Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 07
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=psb latency=0 module=drm

---

### Post by myadav on 2009-11-16
laptop:~$ sudo lshw -C display
[sudo] password for madhur: 
  *-display               
       description: VGA compatible controller
       product: System Controller Hub (SCH Poulsbo) Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 07
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list
       configuration: driver=psb latency=0 module=drm

---

### Post by Kevbert on 2009-11-17
Myadav. That post you tried looks like the right one. There seems to be a few problems with the GMA500 and it's unlikely that it will work without problems when using compiz. Out of interest have you got CompizConfig Settings Manager installed (under System-Preferences) ? If not, you can install it by going into terminal and typing
```
sudo apt-get install compizconfig-settings-manager

```
Best of luck, but I don't think you'll be able to use compiz.

---

### Post by myadav on 2009-11-17
> **Kevbert said:**
> Myadav. That post you tried looks like the right one. There seems to be a few problems with the GMA500 and it's unlikely that it will work without problems when using compiz. Out of interest have you got CompizConfig Settings Manager installed (under System-Preferences) ? If not, you can install it by going into terminal and typing
```
sudo apt-get install compizconfig-settings-manager

```
Best of luck, but I don't think you'll be able to use compiz.


I have compizconfig Settings manager.
I was able to successfully install compiz earlier but I used to freeze at times, so I thought that probably with a fresh install and since I have learned the procedure now I will be able to have a better install, but with this install, I can't even get compiz working.

---

### Post by Kevbert on 2009-11-17
Unfortunately the screen freezing is a typical problem with the GMA500.
Have a look at this [[COLOR="Red"]bug[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-psb/+bug/393290"), especially post #9.

---

