---
title: "Nvidia driver no longer in use, xfce wonky."
date: 2011-07-17
forum: New to Ubuntu
---

### Post by babakott on 2011-07-17
Earlier I rebooted the machine, initially it said something to the effect of "can't shut down when session manager is buys". I kept trying and I finally got it to shut down.

When I logged back in, my desktop just seemed wonky. Then I got an error from Docky about needing to be composited? 

Also, my windows (browser, terminal..etc) have lost the minimize, maximize, and close buttons.

I checked Aditional Drivers, and it said my Nvidia driver was activated but not in use. I tried installing another one, then back and forth between the too. I am not sure whats going on, but it has all but rendered my desktop unusable.

So I decided to look (for the first time) at my xorg.conf file, and I see this

```
babakott@serenity:/etc/X11$ cat xorg.conf

Section "Device"
	Identifier	"Default Device"
	Option	"NoLogo"	"True"
EndSection

babakott@serenity:/etc/X11$
```

And I am guessing there should be more there. I am not even sure where to begin to fix this mess.

Any help is greatly appreciated.

Update: I tried to open my home folder using the filemanager and get this error. Failed to open directory "babakott"
Error stating file `/home/
babakott/.gvfs': Transport endpoint is not connected.

Could this be related to this [post]("http://ubuntuforums.org/showthread.php?t=1806167") 
about some security concerns I had?

---

### Post by cbowman57 on 2011-07-17
What Nvidia driver did you install?  The "driver not in use" is a bug, the driver is in use.  I installed 275.19 yesterday and things got weird, went back to 270.41.

---

### Post by babakott on 2011-07-17
> **cbowman57 said:**
> What Nvidia driver did you install?  The "driver not in use" is a bug, the driver is in use.  I installed 275.19 yesterday and things got weird, went back to 270.41.

I was using the "current version" switch over to 173 and back and forth. Nothing worked. Plus, if you read my update, I am getting some serious system issues now

---

