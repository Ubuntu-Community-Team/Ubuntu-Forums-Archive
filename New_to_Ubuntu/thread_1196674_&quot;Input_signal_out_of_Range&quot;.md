---
title: "&quot;Input signal out of Range&quot;"
date: 2009-06-25
forum: New to Ubuntu
---

### Post by Tholley on 2009-06-25
Need a little help here...

I just installed 9.04 on a 3rd computer as a dual boot with XP, I was working on installing all the packages I wanted and needed, went to Hardware Devices, propriatary drivers, and installed the "recommended" one for my Nvidia GeForce 6150 LE card.

It said to reboot, so I did, and when it gets past the slpash screen, my moniter (HP f2105)
goes dark and even tho I hear the Ubuntu tone at login, then I get a little window that says "Input Signal out of Range" and the moniter goes to sleep. 

I can't adjust the settings since I can't see my way around.

Is there a way to fix this using Recovery Menu?

Thanks...

---

### Post by Divider on 2009-06-25
Yep, when you hear the ubuntu sound:

```
CTRL + ALT + F1
```
or F2 or F3...etc.

login and now you need to figure out what went wrong with your xconfig.

I don't know nvidia at all so maybe somebody more experinced can take this one over?

----
The error means the resolution is too high for the monitor to support so you will have to edit your xorg.conf.

```
 sudo nano /etc/X11/xorg.conf 
```

---

### Post by Tholley on 2009-06-25
This morning after I posted this thread, I was able to use xfix in Recovery Mode, and that un-installed the driver, but now when I go into Display I get this "It appears that your graphics driver does not support the necessary extensions to use this tool.  Do you want to use your graphics driver vendor's tool instead?" 
If I click yes I get this "You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server."

At terminal I ran gksu nvidia-xconfig, but that didn't seem to help. Well I just ran it again, and got this 

"Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'"

So restart X server means re-boot?

If anybody has any suggestions, I'll try re-booting and see what happens.

---

### Post by Tholley on 2009-06-25
That just got be back to "Input Signal Out Of Range" again. 
I don't think the resolution is too high for the moniter to support. It all works fine together in XP.The monitor Recommended Settings are 1680x1050 @60hz.

The Wallpaper and photos look fine without the Nvidia driver, but the windows and fonts all look like I'm in "safe mode"... too big.

---

### Post by Tholley on 2009-06-25
more info... When booting up, I get this... "Starting Up...  Undefined Video Mode Number: 3H Press Enter see more Video modes available."
 I press enter and I see a list of resolutions to choose, (none 1680x1050) but any one close, I still get the Input Signal out of Range.

Also it shows briefly "8254 Timer not connected to 10-ADIC" or something like that.
Not sure it that has anything to so with it or not.

I had to boot into XP now so I could type this because even tho I went into Recovery Mode and ran xfix, (like 5-6 times prior) I got he Out of Range this time.

Somebody help?..............

---

### Post by prvteprts on 2009-06-25
Try changing the refresh rate to the supported range of your monitor. Or you might want it to match the refresh rate on your XP installation.

---

### Post by Tholley on 2009-06-25
> **prvteprts said:**
> Try changing the refresh rate to the supported range of your monitor. Or you might want it to match the refresh rate on your XP installation.

Sound good, how do i do that?

Oh by the way, my wife is from Arayat/Pampanga/Philippines!

---

### Post by prvteprts on 2009-06-25
> **Tholley said:**
> Sound good, how do i do that?

I am assuming you are using the NVidia driver. Go to System>Administration>X Server Settings>X Server Display Configuration and beside the resolution drop-down list is the drop-down list for the refresh rate.

> **Tholley said:**
> 
Oh by the way, my wife is from Arayat/Pampanga/Philippines!

I would say you are a lucky man

---

### Post by Tholley on 2009-06-26
> **prvteprts said:**
> I am assuming you are using the NVidia driver. Go to System>Administration>X Server Settings>X Server Display Configuration and beside the resolution drop-down list is the drop-down list for the refresh rate.
 
Sorry for taking so long to reply, I was tired last night. Had to get some sleep.
 
I _am not_ using the Nvidia driver because like I said before, when I activate the Recommended driver,(and then reboot like it says to) it shows Input Signal out of Range and I just have a black screen before my monitor just goes to sleep.
 
The *normal setting for that monitor in XP* is 1680x1050 @60hz, but I can't get there in Ubuntu for some reason.
 
Sometimes I do get a boot up screen I think I described earlier that has a list of resolutions I can choose from, but even if I pick one lower than what it's capable of, I still get the Input Signal message.:(

---

### Post by Divider on 2009-06-26
Are you using the Restricted jaunty driver or the driver straight from nvidia and compiled yourself?

---

### Post by Tholley on 2009-06-26
The restricted "recommended" Jaunty driver.
 
I downloaded the Nvidia website driver to my desktop lastnight but didn't know how to compile.
I have some notes on that know from some other threads concerning Nvidia drivers like this one.
[http://ubuntuforums.org/showthread.php?t=1196970](http://ubuntuforums.org/showthread.php?t=1196970)

---

### Post by Divider on 2009-06-26
[http://us.download.nvidia.com/XFree86/Linux-x86/185.18.14/NVIDIA-Linux-x86-185.18.14-pkg1.run](http://us.download.nvidia.com/XFree86/Linux-x86/185.18.14/NVIDIA-Linux-x86-185.18.14-pkg1.run)

Boot into recovery mode and drop to a root shell.

```
apt-get install build-essential m4
```

it might be build-essentials not sure about the s or not.

Change to directory where package is located.

```
sh NVIDIA-Linux-x86-185.18.14-pkg1.run 
```

This worked for my buddy who had a 7600 GS.
:guitar:

---

### Post by Tholley on 2009-06-26
Thanks! 
i'll give it a try when I get back home.
It is similar to some I have printed out already.

---

### Post by Tholley on 2009-06-26
Well I think I am getting closer, but still have problems. 
I couldn't access Desktop from Rec Mode, so I was able to ctrl/alt/f1 and run the above.
But then I still get the bootup screen asking me to choose resolution, which I skip past. Then I get a window saying Ubuntu is running in Low Graphics mode. The following errors... blah blah blah.
Anyway, after going thru a bunch of crap, I was able to get back to my desktop.

Now, I activated the driver and rebooted, more Low graphics crap again, but the driver remains activated and even tho I had to choose No to use the driver going into Display (because as it say I need to run Nvidia-Xconfig as root, that did nothing. "gksu nvidia-xconfig" right?)

But I have a choice of 1280x1024 (5:4) (0hz refresh only option?)to choose from (it should be 1680x1050 16:9) and is a little better.

But also going into Appearance/Visual Effects, I can choose Normal, says could not be enabled.

So this is getting very frustrating and I'm wondering if I should just re-install and start all over again.

---

### Post by johenkel on 2010-03-25
> **Divider said:**
> 
```
 sudo nano /etc/X11/xorg.conf 
```

Wow , yepp that did it.
Just installed karmic on a Dell 8300.
Switched freqs down to 50 and 60 Hz, then booted up in higher (finally) resolution and then used browser for right max. freqs (85 / 160Hz).

Thanks !
Was big help !

---

