---
title: "Suddenly all YouTube and Totem movies are playing 5x faster"
date: 2010-04-27
forum: New to Ubuntu
---

### Post by tom66 on 2010-04-27
All videos including YouTube and Totem, but excluding VLC, are playing too fast, about 4-5x faster. There is also no sound. What could be happening? I am using the proprietary flash plugin (version 9) and open source radeon drivers for my graphics card. Same bug happens in Firefox and Chrome as well as in Movie Player. 

It was working today. I have rebooted completely twice.

Any help appreciated! I may have to reinstall to fix this, but I would like to avoid that if possible. Thanks. :)

64-bit Lucid 10.04 beta 2, hardware in signature.

---

### Post by kerry_s on 2010-04-27
> I am using the proprietary flash plugin (version 9)

version 9 ?

did you use synaptic to install?

---

### Post by tom66 on 2010-04-28
I think I did, I'm not sure. Version 9, though Chrome has Version 10 and that is also playing too fast.

---

### Post by zephyrblade on 2010-04-28
Try removing any 'flash' or 'swf' player type plugins you can find:

```

sudo aptitude purge mozilla-plugin-gnash
sudo aptitude purge adobe-flashplugin
sudo aptitude purge flashplugin-nonfree
```

And just (re)install flashplugin-nonfree:

```
sudo aptitude install flashplugin-nonfree
```

---

### Post by lovinglinux on 2010-04-28
You have swfdec installed and it is taking over the version from Adobe. You need to remove it. 

See the [[COLOR="Sienna"]**Flash Optimization**[/COLOR]](http://lovinglinux.megabyet.net/?page_id=220#Flash--Optimization-1) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by tom66 on 2010-04-28
Hmm, I run the commands, as suggested:

```

sudo apt-get remove swfdec-mozilla
sudo apt-get remove mozilla-plugin-gnash
sudo apt-get remove adobe-flashplugin
sudo apt-get install flashplugin-nonfree

```

But none of them do anything...

```

thomas@jupiter:~$ sudo apt-get remove swfdec-mozilla
[sudo] password for thomas: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package swfdec-mozilla is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 524 not upgraded.
thomas@jupiter:~$ ^C
thomas@jupiter:~$ sudo apt-get remove swfdec-mozilla
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package swfdec-mozilla is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 524 not upgraded.
thomas@jupiter:~$ sudo apt-get remove mozilla-plugin-gnash
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package mozilla-plugin-gnash is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 524 not upgraded.
thomas@jupiter:~$ sudo apt-get remove adobe-flashplugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package adobe-flashplugin is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 524 not upgraded.
thomas@jupiter:~$ sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
flashplugin-nonfree is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 524 not upgraded.
thomas@jupiter:~$ 

```

---

### Post by LowSky on 2010-04-28
524 not upgraded? You might want to fix that problem first. I would open up the update manager and do a needed download.

---

### Post by tom66 on 2010-04-28
Oops, I didn't notice that. Seems 10.04 is missing an update notifier...

---

### Post by lovinglinux on 2010-04-28
> **tom66 said:**
> Hmm, I run the commands, as suggested:

```

sudo apt-get remove swfdec-mozilla
sudo apt-get remove mozilla-plugin-gnash
sudo apt-get remove adobe-flashplugin
sudo apt-get install flashplugin-nonfree

```

But none of them do anything...

```

thomas@jupiter:~$ sudo apt-get remove swfdec-mozilla
[sudo] password for thomas: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package swfdec-mozilla is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 524 not upgraded.
thomas@jupiter:~$ ^C
thomas@jupiter:~$ sudo apt-get remove swfdec-mozilla
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package swfdec-mozilla is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 524 not upgraded.
thomas@jupiter:~$ sudo apt-get remove mozilla-plugin-gnash
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package mozilla-plugin-gnash is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 524 not upgraded.
thomas@jupiter:~$ sudo apt-get remove adobe-flashplugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package adobe-flashplugin is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 524 not upgraded.
thomas@jupiter:~$ sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
flashplugin-nonfree is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 524 not upgraded.
thomas@jupiter:~$ 

```

Could you please post the flash information from the **about*:*plugins** page? Just type **about[noparse]:[/noparse]plugins** in Firefox address bar.

---

### Post by tom66 on 2010-04-29
After installing updates overnight and rebooting, no change.

> 
Shockwave Flash

    File: npwrapper.libflashplayer.so
    Version: 
    Shockwave Flash 10.0 r45

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes


---

### Post by P4man on 2010-04-29
Just to clarify, when you say it also happens in totem, is that playing flash clips, or also playing regular avi's?

---

### Post by lovinglinux on 2010-04-29
> **tom66 said:**
> After installing updates overnight and rebooting, no change.

It seems you are using the 32bit version of flash. Install the 64bit beta version. See [this](http://ubuntuforums.org/showthread.php?t=1358591).

---

