---
title: "Increasing Performance on Unbuntu 8.10"
date: 2008-12-22
forum: New to Ubuntu
---

### Post by beastrace91 on 2008-12-22
So I was using KDE3.5 but due to some issues that kept popping up with it I have decided to give Gnome a try... how ever one thing I am noticing is that most of my apps seem to running slower in Gnome than they where in KDE3.5... Is there anything I can do to get slightly better performance out of my system? (Like extra things running that I can turn off or change settings on ect.)

Any advice would be great.

~Jeff

---

### Post by cariboo on 2008-12-22
You could go into System-->Preferences-->Sessions and turn off services you don't need. If you don't need any of the services Assitive Technologies offers you can turn of AT SPI Registry Wrapper and Visual Assistance. If you don't need Bluetooth Manager, turn it off. Definitely turn off Tracker and the Tracker applet.

Jim

---

### Post by nhasian on 2008-12-22
what are your system specs?  Sometimes a small upgrade can make a big difference:

```
lshw -C display,cpu,memory
```

---

### Post by beastrace91 on 2008-12-23
The system itself is semi decent (Although I am upgrading towards the end of the week waiting for new laptop to get here in the mail) atm I am running and AMD64 bit Dual Core 1.9giz with 2 gigs of ram and a ATI HD2600 Mobility GFX card.

I will try disabling some of those services and see if that helps at all thanks.

~Jeff

---

### Post by jrusso2 on 2008-12-23
> **beastrace91 said:**
> The system itself is semi decent (Although I am upgrading towards the end of the week waiting for new laptop to get here in the mail) atm I am running and AMD64 bit Dual Core 1.9giz with 2 gigs of ram and a ATI HD2600 Mobility GFX card.

I will try disabling some of those services and see if that helps at all thanks.

~Jeff

I am running 8.04 on a lot worse hardware then that and the performance is fine and I am running KDE 3.5.

---

### Post by beastrace91 on 2008-12-23
Performance isn't exactly poor I simply said Gnome was running worse that KDE3.5 was... I disabled some of those services but have been at work all day so haven't checked to see if it helped at all yet.

~Jeff

---

### Post by 67GTA on 2008-12-23
Just do a google search for "Ubuntu speed tweaks" or Speed up Ubuntu". That should keep you busy for a couple of days:)

---

### Post by albinootje on 2008-12-23
> **beastrace91 said:**
> So I was using KDE3.5 but due to some issues that kept popping up with it I have decided to give Gnome a try... how ever one thing I am noticing is that most of my apps seem to running slower in Gnome than they where in KDE3.5... Is there anything I can do to get slightly better performance out of my system? (Like extra things running that I can turn off or change settings on ect.)


Are you using any KDE apps in Gnome ? 
Those are a little slower than when run in KDE.

Nautilus can be pretty sluggish when opening directories with a lot of files.

I've also read that the default icon theme for Ubuntu slows things down a little, and after customizing the theme i found it to be a little faster indeed.

And.. while searching for "ubuntu speed tweaks" this url
[http://forums.whirlpool.net.au/forum-replies-archive.cfm/660504.html](http://forums.whirlpool.net.au/forum-replies-archive.cfm/660504.html)
came with the interesting and useful :

> 
Have a look over in [www.ubuntuforums.org](www.ubuntuforums.org) - it's a veritable mine of info about what you can do...
	
anchor
posted 2007-Jan-11, 8am AEST

;-)

---

### Post by northern lights on 2008-12-23
> **albinootje said:**
> Are you using any KDE apps in Gnome?
This was my thought as well.

Try finding gtk+ alternatives for your Qt4 apps.
And make sure to install gtk variants of those apps that exists as either version.

---

