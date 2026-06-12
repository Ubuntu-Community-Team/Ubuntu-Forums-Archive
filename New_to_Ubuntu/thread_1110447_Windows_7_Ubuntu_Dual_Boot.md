---
title: "Windows 7 Ubuntu Dual Boot?"
date: 2009-03-29
forum: New to Ubuntu
---

### Post by wilwaldon on 2009-03-29
I have a little problem. I am using Windows 7 right now and would enjoy having a dual booting Win7-Ubuntu system. 

The problem is, Windows 7 takes over the bootloader and won't let me do it. Does anyone know how to do this? I'd love to switch 100% over to Ubuntu after I mess with it a little and make sure I can still get my work done with it, but for right now I'll need both.

Any help? :confused:

Thanks in advance!

---

### Post by RedSingularity on 2009-03-29
Do you currently have Ubuntu installed also?

---

### Post by InfectedWithDrew on 2009-03-29
If you install Win7, then install Ubuntu, GRUB will take over instead.

----------------
Now playing: [Lostprophets - We Are Godzilla, You Are Japan](http://www.foxytunes.com/artist/lostprophets/track/we+are+godzilla%2c+you+are+japan)

---

### Post by RedSingularity on 2009-03-29
Yeah thats the preferred way.  If you have both installed already then you need to reinstall the GRUB menu.  Follow [THIS]("http://ubuntuforums.org/showthread.php?t=224351") guide.  Its very easy with the Live CD.

---

### Post by Dejai on 2009-03-29
Windows 7 is a beta and a Microsoft Beta is sure to have all kinds of problems...
Here are some helpful threads:
[http://ubuntuforums.org/showthread.php?t=1035999](http://ubuntuforums.org/showthread.php?t=1035999)

EDIT: 
Looks like I was beaten to it :P

---

### Post by billytalent on 2009-03-29
> **Shadow121 said:**
> Yeah thats the preferred way.  If you have both installed already then you need to reinstall the GRUB menu.  Follow [THIS]("http://ubuntuforums.org/showthread.php?t=224351") guide.  Its very easy with the Live CD.

This is a great guide, helped me big time.

---

### Post by wilwaldon on 2009-03-29
Woah, LOTS of response. THANKS! 

Sorry to leave this out.

I installed Win7 first and used Wubi to install after.

I'll grab the live cd download and try the other way. I really hope it works, I soooo bad want to ditch windows!

---

### Post by wilwaldon on 2009-03-29
I tried to use this guide: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

But it kept kicking back an error...

Error 15 file not found

I did the install from within Windows. Could that be the problem?

---

### Post by InfectedWithDrew on 2009-03-29
> **wilwaldon said:**
> I tried to use this guide: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

But it kept kicking back an error...

Error 15 file not found

I did the install from within Windows. Could that be the problem?Yeah, I don't think you should use Wubi on Win7 right now.  Why don't you partition your drive and dual-boot that way?  Wubi isn't really dual-booting...

----------------
Now playing: [Green Day - Walking Contradiction](http://www.foxytunes.com/artist/green+day/track/walking+contradiction)

---

### Post by RedSingularity on 2009-03-29
Yeah i would recommend you uninstall ubuntu from the Add/Remove inside windows and then reinstall by booting the PC with the Ubuntu disk inserted.

---

