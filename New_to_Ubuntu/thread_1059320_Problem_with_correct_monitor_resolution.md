---
title: "Problem with correct monitor resolution"
date: 2009-02-03
forum: New to Ubuntu
---

### Post by Inkjet on 2009-02-03
I'm a very green Ubuntu beginner with absolutely no knowledge of command lines.
I,m running Windows XP on my main computer. Recently I threw together a year old motherboard, hard drive, etc. and then installed Ubuntu 8.10 on it. I'm using this Ubuntu PC only for internet use (security). The motherboard in this setup is a Micro ATX size with on-board video. Ubuntu could only deliver 800X600 resolution to a 19 inch (non wide screen) monitor. I installed an old video card and booted up, Ubuntu now had the resolution set correctly to 1280X1024 (I got exactly the same results with two other micro ATX PCs and also with different monitors). Any one know why Ubuntu is not setting proper resolution for on-board video? This is a real problem for me since I intended to replace the Ubuntu PC's case with a very small footprint case which has no room for a video card.

---

### Post by kansasnoob on 2009-02-03
> **Inkjet said:**
> I'm a very green Ubuntu beginner with absolutely no knowledge of command lines.
I,m running Windows XP on my main computer. Recently I threw together a year old motherboard, hard drive, etc. and then installed Ubuntu 8.10 on it. I'm using this Ubuntu PC only for internet use (security). The motherboard in this setup is a Micro ATX size with on-board video. Ubuntu could only deliver 800X600 resolution to a 19 inch (non wide screen) monitor. I installed an old video card and booted up, Ubuntu now had the resolution set correctly to 1280X1024 (I got exactly the same results with two other micro ATX PCs and also with different monitors). Any one know why Ubuntu is not setting proper resolution for on-board video? This is a real problem for me since I intended to replace the Ubuntu PC's case with a very small footprint case which has no room for a video card.

I wish I had an answer for you!

I responded earlier today to one of these posts about 8.10 resolution and I even tried an old 8.04 trick that doesn't work anymore!

[http://ubuntuforums.org/showthread.php?t=1058894](http://ubuntuforums.org/showthread.php?t=1058894)

My personal suggestion is to try 8.04 (aka: Hardy) which is LTS so it's good for a long time and by then maybe there'll be a decent "how-to" on the new xorg.

Or maybe this >bump< will help.

But I see someone else added a comment to that last thread. I have no idea if it will work or not!

---

### Post by halitech on 2009-02-03
when Ubuntu installs and configures things, it looks at the chipset. If it doesn't have good drivers (SiS comes to mind here) it will default to the highest *safe* size that it thinks the video card can handle regardless of the monitor and what it can handle.

---

### Post by kansasnoob on 2009-02-03
> **halitech said:**
> when Ubuntu installs and configures things, it looks at the chipset. If it doesn't have good drivers (SiS comes to mind here) it will default to the highest *safe* size that it thinks the video card can handle regardless of the monitor and what it can handle.

The sad thing is that in 8.04 and earlier you could easily change these settings if they weren't correct.

In 8.10 I've found no way of changing these settings! In fact I've tried a few things and it always freezes "X" at gdm.

The man pages are of no help either.

---

### Post by halitech on 2009-02-03
the downside of trying to make it easier for new people coming over from windows and its not just Ubuntu doing it either as Debian Lenny is the same way. Install and pray it detects everything right cause if not its nightmare time trying to get things working properly which could cause some people to run right back to MS.

---

### Post by kansasnoob on 2009-02-03
I can't disagree with that.

I always had to add "openchrome" to the device options in 8.04.

And I built over 20 of these. In 8.10 I've been lucky and found that my unichrome crap is just recognized.

I just find it annoying to not know how to edit the auto xorg stuff in 8.10. My only answer now is to go back to 8.04!

---

### Post by halitech on 2009-02-03
I've been lucky with my systems as well, usually I use an old Nvidia card (geforce mx4 440 I think) or an old ati 9600 card but I'm not one of the folks who need/want to have compiz running, I worry more about stability then flash so I dont need 3d driver support and both cards work with the open source drivers.

hopefully someone will get a clue that is working on xorg and give a better way to configure things in the future.

---

### Post by kansasnoob on 2009-02-03
So ............... I'm thinking it should be perfectly acceptable to suggest trying 8.04 to those who can't get openchrome drivers to work in 8.10?

I'm not sure?

There's certainly nothing wrong with Hardy! It's stable and supported for a long, long time!

---

### Post by Inkjet on 2009-02-03
How can I Get Ubuntu 8.04?

---

### Post by halitech on 2009-02-03
> **kansasnoob said:**
> So ............... I'm thinking it should be perfectly acceptable to suggest trying 8.04 to those who can't get openchrome drivers to work in 8.10?

I'm not sure?

There's certainly nothing wrong with Hardy! It's stable and supported for a long, long time!

I would, latest doesn't always mean greatest

> **Inkjet said:**
> How can I Get Ubuntu 8.04?

go to the downloads and select other versions

---

### Post by HavocXphere on 2009-02-04
Setting higher Resolution & Refresh Rate:
[Use at own risk]
[http://kubuntuforums.net/forums/index.php?topic=3100136.msg161401#msg161401](http://kubuntuforums.net/forums/index.php?topic=3100136.msg161401#msg161401)
Works fine for Kubuntu 8.10...I don't see why it shouldn't for ubuntu.:KS

On an underpowered PC a high res could also make the whole thing laggy.

---

