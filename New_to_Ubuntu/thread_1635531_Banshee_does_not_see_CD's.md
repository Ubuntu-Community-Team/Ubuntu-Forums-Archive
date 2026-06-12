---
title: "Banshee does not see CD's"
date: 2010-12-01
forum: New to Ubuntu
---

### Post by John Peschken on 2010-12-01
I just did a fresh install of 10.10,  After that, I installed Banshee.  I insert a CD in my drive, and it does not appear for ripping in Banshee.

What I know:

[LIST]
[*]The CD appears on the Gnome desktop
[*]The CD appears in Rhythmbox
[*] In the Banshee "extensions" section, "Audio CD Support" is checked.
[*]When I try to "Open Location" in Banshee with the CD, I get the message: "DBus error org.freedesktop.DBus.Error.ServiceUnknown: The name :1.263 was not provided by any .service files"  That seems not normal.
[*]Banshee worked as expected with 10.04
[*]I have tried uninstalling and reinstalling Banshee with no effect.
[/LIST]
What;s the deal here?  How can I fix it?

---

### Post by tuppe666 on 2010-12-03
I don't know if its any help, but banshee 1.6 had a double race condition in the .NET DBus implementation!? which sounds likely to be related to your problem. 1.9 is out now. Banshee does seem to be the mover and shaker of the 3 pane music player right now.

Follow the instructions on [http://www.omgubuntu.co.uk/2010/09/banshee-1-8-0-released/](http://www.omgubuntu.co.uk/2010/09/banshee-1-8-0-released/)

1.9.0 has been released, but does not contain the community extensions, but I have been using it over the past few days and its fantastic.

---

### Post by John Peschken on 2010-12-03
> **tuppe666 said:**
> I don't know if its any help, but banshee 1.6 had a double race condition in the .NET DBus implementation!? which sounds likely to be related to your problem. 1.9 is out now. Banshee does seem to be the mover and shaker of the 3 pane music player right now.

Follow the instructions on [http://www.omgubuntu.co.uk/2010/09/banshee-1-8-0-released/](http://www.omgubuntu.co.uk/2010/09/banshee-1-8-0-released/)

1.9.0 has been released, but does not contain the community extensions, but I have been using it over the past few days and its fantastic.

I solved this the old fashioned way ... I reinstalled Ubuntu.  I doubt it was version related, because I had been running an up-to-date version of Banshee the day before and it worked.  Also, the reinstall of the same disk that failed before solved the problem, so it was more likely a random installation error of some kind.  I was hoping someone could suggest a package to reinstall or settings to change, but I got impatient.  Since I had very little invested in the current installation, it wasn't that traumatic to blow it away and start again.

Of course now I have a different problem.  The mute and volume function keys on my laptop (Fn F6,F7 and F8 have stopped responding for some reason.  Weird.  They worked on the previous install with this same disk, 10.04, and with Mint.  Time to start messing with that when I get home tonight.  OS installations are loaded with fun.  No wonder so many Windows users are still running XP.

Yes, Banshee does seem to be the coming thing for Ubuntu.  I believe I read that it is destined to replace Rhythmbox as the default player in Ubuntu.  It's very nice, and I prefer to use it,  but I have had a few weird hiccups like this with it.  It does not do as good a job finding the track information for my somewhat obscure CD collection as Rhythmbox does.  Rhythmbox has been dead reliable for me.  Some folks are unhappy with the fact that it is based on something called "Mono", but I don't really know what that's all about.  Here's hoping they can improve the track lookup and reliability before it becomes the Ubuntu standard.

---

### Post by John Peschken on 2010-12-03
> **John Peschken said:**
> I solved this the old fashioned way ... I reinstalled Ubuntu. ...
Of course now I have a different problem.  The mute and volume function keys on my laptop (Fn F6,F7 and F8 have stopped responding for some reason.  Weird. ...

Okay, the CD's stopped appearing in Banshee again.  Pretty frustrating and mysterious.  On the bright side, the function keys are back!

So, I'm still looking for ideas on what's going on with Banshee.

---

### Post by madmaxo on 2010-12-29
I'm having the same problem, even after upgrading to 1.9.1. CD doesn't appear on the left.

---

### Post by John Peschken on 2010-12-29
> **madmaxo said:**
> I'm having the same problem, even after upgrading to 1.9.1. CD doesn't appear on the left.
 
Yes, it is a weird one.  Everything works on a fresh install, but then disappears.  That tells me it is probably an option I am setting somewhere, or a program I am installing that is messing things up, but I can't seem to isolate it.  I just have no idea.

---

### Post by donarntz on 2011-03-23
I'm having this problem too.  It's pretty frustrating.

---

### Post by directhex on 2011-03-24
If there's no bug filed, it doesn't exist

---

### Post by N2G(bn#7+ on 2011-04-30
I think this issue has already been filed as a bug in Launchpad:
> [Bug #761034 - Banshee does not load audio CD]("https://bugs.launchpad.net/ubuntu/+source/banshee/+bug/761034")

and it's just been listed upstream from there to bugzilla:
> [gnome-bugs #648968]("https://bugzilla.gnome.org/show_bug.cgi?id=648968")

---

### Post by therieb on 2011-05-13
For what it's worth, this problem is also present in Natty running Banshee 2.0.

---

