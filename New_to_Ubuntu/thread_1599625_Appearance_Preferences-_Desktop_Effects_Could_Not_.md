---
title: "Appearance Preferences- Desktop Effects Could Not Be Enabled"
date: 2010-10-18
forum: New to Ubuntu
---

### Post by xXNI4NI on 2010-10-18
After setting up 10.04 to my liking and going through the rigamarole of installing drivers I came to compiz.
Downloaded from the software center
Turned my settings on
Then went to turn on Desktop effects and was told it could not be enabled.
After a full day's searching through countless threads and trying countless options I'm now certain I've done more harm then good.
I'm sure the first question (as I've seen in all the threads) is going to be post your lspci, so here it goes...
> ni4ni@gpc:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
ni4ni@gpc:~$ 

Desperately needing help to put the last touches on my system. PLEASE. :D

---

### Post by mastablasta on 2010-10-18
it could be that the drivers are not good enough to support effects. you card is an intel onboard card. intel doesn't have very good driver support.

---

### Post by xXNI4NI on 2010-10-18
Thank you for your quick reply and time!
I thought the hardware might be a little weak at first too, while doing my digging I came across a youtube video of someone showing off their set-up in 10.04 w/ the exact same integrated graphics 
"http://www.youtube.com/watch?v=WgxazcIf5JM" 
I'm not dead set on having compiz but it is a nice tough :P.
I've also tried going about updating my drivers and haven't found a successful way of doing that.

---

### Post by xXNI4NI on 2010-10-18
Update: Whenever I clicked to enable the effects, the window would go gray (like it was loading/lost focus) and then tell me that it could not be enabled. 
        Now another window pops up and says, "Searching for drivers" after awhile that window disappears and it tells me that my effects could not be enabled.

---

### Post by lifeSum on 2010-10-18
Your video card may be blacklisted. What is the output when you run compiz in a terminal?

```
compiz
```// landon

---

### Post by xXNI4NI on 2010-10-19
Heya Landon,
```
compiz: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory

```
I found in a "Compiz Check" thread where someone had the same output, unfortunately it was followed up w/ > There's obviously something seriously wrong with your driver.
How did you install it?
This was back in '08 so who knows now. Other than installing 10.04 I haven't done anything to update/install new video drivers. I am fairly certain however that the problem lies w/ them.

---

### Post by Quackers on 2010-10-19
It's old but may still work
[http://ubuntuforums.org/showthread.php?t=799070](http://ubuntuforums.org/showthread.php?t=799070)

---

### Post by xXNI4NI on 2010-10-19
Thanks for the reply.
I've tested that and had a few Fails. Again not too sure if it's current but Forlong noted that if any were 'OK' then i am most likely able to run compiz. I'm almost certain this is driver related but in any chance I'll post the output of compiz-check here.```
Gathering information about your system...

 Distribution:          Ubuntu 10.04
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
 Driver in use:         intel
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [FAIL]
 Checking for non power of two support...          [FAIL]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [FAIL]
 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: Unable to detect maximum 3D texture size 

```

---

### Post by Alcarcalimo on 2010-10-19
> **lifeSum said:**
> Your video card may be blacklisted. What is the output when you run compiz in a terminal?

```
compiz
```// landon

Hi! I had the exact same problem. I placed this "compiz" in my terminal and this all she said:


```
Backend     : ini
Integration : true
Profile     : default
Adding plugins
Initializing core options...done
Initializing move options...done
Initializing resize options...done
Initializing place options...done
compiz (core) - Error: Couldn't load plugin 'decoration'
```


This is what happened after I Compiz-checked it:

```
 Gathering information about your system...

Distribution:          Ubuntu 10.10
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation C61 [GeForce 6150SE nForce 430] (rev a2)
 Driver in use:         nvidia
 Rendering method:      Nvidia

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]
```

I'm not sure what's wrong as I was able to do compiz since Jaunty with this Video Card.

---

### Post by xXNI4NI on 2010-10-19
Yours should work, how did you install Compiz?

---

### Post by lhb1142 on 2010-10-19
> **xXNI4NI said:**
> After setting up 10.04 to my liking and going through the rigamarole of installing drivers I came to compiz.
Downloaded from the software center
Turned my settings on
Then went to turn on Desktop effects and was told it could not be enabled.
After a full day's searching through countless threads and trying countless options I'm now certain I've done more harm then good.
I'm sure the first question (as I've seen in all the threads) is going to be post your lspci, so here it goes...

Desperately needing help to put the last touches on my system. PLEASE. :D

Go into the Synaptics Package Manager and search for ccsm, If that's not installed, install it.

That should solve your problems.

I hope it helps.

---

### Post by xXNI4NI on 2010-10-19
> **lhb1142 said:**
> Go into the Synaptics Package Manager and search for ccsm, If that's not installed, install it.

That should solve your problems.

I hope it helps.

Installed it and restarted, still have the error. :(

---

### Post by lhb1142 on 2010-10-19
> **xXNI4NI said:**
> Installed it and restarted, still have the error. :(

I think you have a more serious problem than I can help with. But try this:

In Synaptics Package Manager, search for and install BleachBit.

After installation, do a restart.

Go into Applications and find Bleachbit (I forget where it installs by default; I moved mine to System Tools). You will see two BleachBits - one just plain BleachBit and the other BleachBit (as root).

Run BleachBit (as root) first. You will have to configure it prior to first use. Under General I have ONLY Overwrite files to hide contents checked. The other two options should be unchecked.

Then go down the list and check off everything - EXCEPT where it says This option may be slow, This option will remove your bookmarks, or This option may cause problems.

Then run it.

Now instead of just running the plain Bleachbit, go into your Terminal and type sudo bleachbit (just that way). Enter your password, configure this BleachBit just as you did the first one, then run it.

These two programs will 'wipe' everything untoward from your computer (except, of course, for any errors you may have inadvertently created).

(I use both BleachBits routinely at the end of every computer session.)

Then shut down the computer and restart it. See if, at that point, you can effect the changes you wish via CompizConfig Settings Manager and Simple CompizConfig Settings Manager (both of which you will find under System -> Preferences).

If this doesn't work, I hope there is someone else who can suggest a solution. The only other thing that I could suggest (assuming cleaning your computer fails) would be to effect a complete fresh reinstall of Ubuntu (which is not as hard as you may think). Just make certain that you have all of your Documents, Music, Pictures, and Videos backed up to an external hard drive.

Good luck!

---

### Post by xXNI4NI on 2010-10-19
> **lhb1142 said:**
> 
See if, at that point, you can effect the changes you wish via CompizConfig Settings Manager and Simple CompizConfig Settings Manager (both of which you will find under System -> Preferences).


Thanks for the reply, I will try this when I get home. To make sure I understand what it is you're having me do in a sort of lament terms. Bleachbit will purge ubuntu of un-necessary/broken files. Is there any risk that after running something may be accidentally removed or is rather safe? I will follow the directions you provided so I assume it will go good as planned.

I do have another question though. When you say to check out the simple compizconfig settings manager, I must first enable Desktop Effects correct?

---

### Post by xXNI4NI on 2010-10-19
at any rate I ran this and still wasn't able to enable desktop effects.

---

### Post by hell_rider on 2010-10-20
I managed to get compiz running just this morning. (I am a total newbie myself)

In my case it was as simple as making the following edit in /etc/X11/xorg.conf
Option "Composite" "Enable" in the "Extensions" section.

and 2 other edits specific to my hardware.

Mind you, my hardware is different (ATI. using fglrx)

Since the hardware is different, the exact same might (will obviously) not work.  Still I guess it pays to look at the obvious entries in the xorg.conf file. For eg. the Composite option was set to O in my case.

I got my solution here.
[https://help.ubuntu.com/community/RadeonXpress](https://help.ubuntu.com/community/RadeonXpress)

At least it has some standard checks to verify your hardware capabilities, which you can still do to begin with.

You should find a similar page for your specific hardware.

Wishing you Good luck.

---

### Post by xXNI4NI on 2010-10-20
Thanks for the reply.

I've checked all the ubuntu threads I could find regarding my hardware (intel GM965). Your ATI just recently started getting support for compiz so I understand the challenges you had to face to get yours working. Intel was supposed to have open source (which from their driver site they are) yet the compiz seems to have my model on blacklist. Okay so ```
gksudo gedit /usr/bin/compiz
``` to remove blacklist right? No, > "gedit has not been able to detect the character encoding.
Please check that you are not trying to open a binary file.
Select a character encoding from the menu and try again."
Damn okay well no threads, as of yet, fix that.
Okay howabout the workaround from the terminal, oh but wait 
> error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory

It would be nice if it told me where it was looking so i could ln it. The current libGL.so.1 is currently located int usr/lib/mesa.
But back to the original problem, when I attempt to enable desktop effects, it scans for drivers for about 15 seconds and then tells me the effects cannot be enabled. So drivers eh? As far as I know I've reinstalled all of them directly from Intel's site and packaged them myself w/ Alien. I'm out of options. Should I just give up?

---

### Post by Yellow Pasque on 2010-10-20
You driver is screwed up. First off, if you've tried to install nvidia or ATI proprietary drivers (yes, I've seen plenty of intel users do this unwittingly while following some random guide), purge them: [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)
Now, we'll reinstall appropriate packages
```
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
```
Reboot or log out to restart X. If you're still getting the libgl error (or a different one), post /var/log/Xorg.0.log

---

### Post by trikster_x on 2010-10-20
Hi, I'm having the same problem on Maverick, and it seems to have been caused by a recent update to openGL.  I have a 945 GME controller on an aspire one.  seems like their are a lot of threads about compiz suddenly not working and no solutions offered for the problem yet.  I hope this changes in a near future update.

---

### Post by xXNI4NI on 2010-10-20
> **Temüjin said:**
> You driver is screwed up. First off, if you've tried to install nvidia or ATI proprietary drivers (yes, I've seen plenty of intel users do this unwittingly while following some random guide), purge them: [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)
Now, we'll reinstall appropriate packages
```
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
```
Reboot or log out to restart X. If you're still getting the libgl error (or a different one), post /var/log/Xorg.0.log

First, thank you very much for helping. I've made sure that the video drivers I was installing was only the intel drivers relevant to the GM965. Back to the libgl problem, some progress, maybe, I was getting the libgl errors when running compiz in the terminal. When I entered compiz after re-installing the packages and logging out I recieved this.> WARNING: Application calling GLX 1.3 function "glXCreatePixmap" when GLX 1.3 is not supported!  This is an application bug!
Starting gtk-window-decorator
WARNING: Application calling GLX 1.3 function "glXDestroyPixmap" when GLX 1.3 is not supported!  This is an application bug!



Is there a way to confirm, just to be safe, that I've only installed intel drivers? I know compiz-check would display the drivers being used but not the version.

---

### Post by xXNI4NI on 2010-10-20
I didn't have a chance to check it earlier but whatever ```
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
``` did it fixed it. THANK YOU SO MUCH! I'll much sure to change this to solved. AANNDD if any other passer-byers are scanning through threads, and have been receiving the libGL error in 10.04 give the above a shot. Not too sure if it pertains to a certain driver or GPU.
Thanks again I really appreciate it:popcorn:

---

