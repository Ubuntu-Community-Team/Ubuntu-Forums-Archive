---
title: "new install doesnt boot into gnome"
date: 2010-12-20
forum: New to Ubuntu
---

### Post by philipballew on 2010-12-20
when i install Ubuntu 10 10 on a new asus laptop it instals fine but wont shoe the regular desktop but boots into command line only. i logged in and typed startx and then the page just goes blank? anyone?

---

### Post by philipballew on 2010-12-20
ive also run such commands as "sudo service gdm start" and "sudo dpkg-reconfigure xserver-xorg" both times the screen goes blank but still glows? video card maybe?

---

### Post by Quackers on 2010-12-20
Whilst booting hold down the shift key to show the grub menu. When there press the "e" key. In the next screen navigate to the end of the line which says "quiet splash" and delete those words then type in nomodeset then press ctrl + X to reboot. If the system boots to the desktop run System > Admin > Additional drivers to load video drivers. Then reboot and hopefully it'll be good.

---

### Post by garvinrick4 on 2010-12-20
# Post what type of machine and its graphics card and such.( I am weak in graphic cards others are not)
Lot better chance of user helping out with as much info as possible.
# You can try these if you have internet. Most likely have to be wired:
At terminal:
```
sudo apt-get install ubuntu-desktop
``````
sudo apt-get install gdm
``````
sudo apt-get install xorg
```# These above will just make sure they are all installed:
# If you need to check on installed packages install this below.
```
sudo apt-get install aptitude
```Then you can run this to check on packages
```
aptitude show "package name"
``` without qoutes

---

### Post by philipballew on 2010-12-20
it still starts in cli, however, after rebooting after your changing of grub it said ubuntu is running in low graphics mode and then started cli. i rebooted and that screen wasnt there

---

### Post by philipballew on 2010-12-20
it is an asus k52f with a well i dont know the video card. how do i find this?

---

### Post by garvinrick4 on 2010-12-20
```
lspci | grep VGA 
``````
 lspci -v | less
```#first is video card
#second is all cards and drivers.

---

### Post by philipballew on 2010-12-20
philip@philip-laptop:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 18)



here is the info about my video card

---

### Post by garvinrick4 on 2010-12-21
#Intel video card but should be fine as is.
#When you run the second command, check and see if it
shows a driver. example below
```
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Int
egrated Graphics Controller (rev 07)
        Subsystem: Hewlett-Packard Company Device 306b
        Flags: bus master, fast devsel, latency 0, IRQ 28
        Memory at d0000000 (64-bit, non-prefetchable) [size=4M]
        Memory at c0000000 (64-bit, prefetchable) [size=256M]
        I/O ports at 4110 [size=8]
        Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 
Enable+
        Capabilities: [d0] Power Management version 3
        Kernel driver in use: i915
        Kernel modules: i915

```

---

### Post by garvinrick4 on 2010-12-21
Did you run the commands earlier to make sure install is complete for desktop?

---

### Post by philipballew on 2010-12-21
did you post those, if not what are they?

---

### Post by garvinrick4 on 2010-12-21
> **philipballew said:**
> did you post those, if not what are they?
Post #4 just to check they are all installed run them.

---

### Post by philipballew on 2010-12-21
those comands say there already installed. heres the lspci -v | less 


00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 18) (prog-if 00 [VGA controller])
        Subsystem: ASUSTeK Computer Inc. Device 1Be2
        Flags: bus master, fast devsel, latency 0, IRQ 11
        Memory at d0000000 (64-bit, non-prefetchable)[size=4M]
        Memory at c0000000 (64-bit, prefetchable) [size=256M]
        I/O ports at e080 [size=8]
        Expansion ROM at <unassigned> [disabled]
        Capabilities: <access denied>
        Kernel modules: i915

---

### Post by philipballew on 2010-12-21
is there a way i can re install. i tried installing again earlier and the same error was there. maybe alternitive installer ot install xubuntu then switch desktops

---

### Post by garvinrick4 on 2010-12-21
#Someone with Video knowledge hop in here please. I do not see
any drivers in use with his video card. The Intel i915 driver
but not showing in use. 
# Has all the desktop packages installed but cannot get into X.

##phillipballew hold on for a couple of minutes and lets see if this video driver
    can be fixed.  If get right user in this thread will be fixed. Need a video card user that
    knows whats going on here. Seems like should be simple if driver not in use.

---

### Post by philipballew on 2010-12-21
i agee, a simple apt-get command is most likely exactly what is needed here once the exact items needed are figured out

---

### Post by Quackers on 2010-12-21
Have you tried both of the i915 modeset boot prompts?

---

### Post by philipballew on 2010-12-21
i changed from quiet splash to  nomodeset and its still set as that and after all this its not workin

---

### Post by Quackers on 2010-12-21
I believe there are 2 that you could try.
i915.modeset=0
i915.modeset=1
You can try them one at a time. They should replace the quiet splash

---

### Post by philipballew on 2010-12-21
so where it now says either quiet splash" or nomodeset i put those in, trying each one befor the other?

---

### Post by Quackers on 2010-12-21
nomodeset should be gone! It's only there for one boot at a time.
Yes, delete the quiet splash and type in one of those options then ctrl + X toreboot

---

### Post by philipballew on 2010-12-21
i ran both. no luck, this is odd because it ran fine under the live cd

---

### Post by philipballew on 2010-12-21
and yes  nomodeset was gone

---

### Post by philipballew on 2010-12-21
i logged in via recovery mode and failsafe graphics mode. i am on the desktop. what do i do now to insure i can get on in regular mode?

---

### Post by garvinrick4 on 2010-12-21
#Thanks Quackers: Stick with OP this is notes I have found:
This is from Ubuntu release notes: From 10.04 and up: 
[https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Working%20around%20bugs%20in%20the%20new%20kernel%20video%20architecture](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Working%20around%20bugs%20in%20the%20new%20kernel%20video%20architecture)
```

Ubuntu 10.04 LTS enables the new kernel-mode-setting (KMS) technology 
by  default on most common video chipsets.  
While this is a major step  forward for the graphics architecture in 
Ubuntu, in some rare cases KMS  will prevent your 
video output from working correctly, or from working  at all.  
If you need to disable KMS, you can do so by booting with 
the nomodeset option.  You can also save this setting so that 
it's applied at every boot by adding it to your grub config 
(for GRUB 2: edit /etc/default/grub and add nomodeset to 
GRUB_CMDLINE_LINUX, then run sudo update-grub

[CODE]gksudo gedit /etc/default/grub
```add nomodeset to GRUB_CMDLINE_LINUX
Hit save.
open terminal:
```
sudo update-grub
```[/CODE]

---

### Post by Quackers on 2010-12-21
You can see if graphics drivers are available if you run System > Admin > Additional drivers.

---

### Post by philipballew on 2010-12-21
no propitery drivers are in use on this system and there is no download options

---

### Post by philipballew on 2010-12-21
should i try the grub trick?

---

### Post by Quackers on 2010-12-21
If you are referring to garvinrick4's post it's certainly worth a try. I am concerned though that no boot prompt option worked.

---

### Post by philipballew on 2010-12-21
i am to, and in that case im unsure what to do

---

### Post by theasprint on 2010-12-21
Hi,

Er this should be the second time I attempted to try solve INTEL graphics problems. *I prefer Nvidia

From what I know, someone told me that Ubuntu's xorg file actually does support Intel better than Nvidia.

But if you want to try my steps, then 

1. Get the latest driver from intel.com ( RMB to get Linux version)

2. Then turn off your gdm
```
sudo service gdm stop
```

3. Then install your Intel Graphics.
```
sudo bash <your Intel driver's directory>
```

4. After finishing installation, turn on gdm
```
sudo service gdm start
``` 

* Here is a link where people succeeded with Nvidia graphics
[http://ubuntuforums.org/showthread.php?t=1648734](http://ubuntuforums.org/showthread.php?t=1648734)

Good Luck :D

---

### Post by garvinrick4 on 2010-12-21
> **philipballew said:**
> should i try the grub trick?
Not a trick is from Ubuntu's website for running in nomodeset which
is what I believe Quackers was saying. Is that right Quackers or did
I misunderstand your intentions. I was just stating how to install it to
run at every boot from Ubuntu's own instructions.
#Can always remove and go back to original grub.cfg no big deal.

---

### Post by philipballew on 2010-12-21
i just updated kernels and things seem to run fine

---

