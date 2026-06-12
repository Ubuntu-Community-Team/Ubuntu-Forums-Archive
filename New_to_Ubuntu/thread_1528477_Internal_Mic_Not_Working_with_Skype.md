---
title: "Internal Mic Not Working with Skype"
date: 2010-07-10
forum: New to Ubuntu
---

### Post by bcasanov on 2010-07-10
Hi,

I have an Acer Aspire One Model ZG5 with an internal microphone.  In the sound preferences of the volume applet in the panel, under the Input tab, I have "Internal Audio Analog Stereo" enabled below "Choose a device for sound input" and the input volume set to 100%.  However, the  meter does not move to indicate that it is capturing sound.  In Skype, when I do a test call, I do not hear any sound when the recording is played back to me.  In the Sound Recorder application, however, the internal mic does work.  When I have an external mic, Skype does work and the meter in Sound Preferences under Input moves to indicate that it is recording.  How can I make my internal microphone work with Skype, since I have misplaced the external mic?

---

### Post by AAOFan on 2010-07-10
Hi,
   Are you running the custom kernel developed for our AAO?  If not, I'll tell you where to get it.  This should fix the issue you're having and plus many other unknown problems you didn't know you had.

Here is a great resource for AAO owners running Ubuntu.
[http://www.aspireoneuser.com/forum/viewforum.php?f=28&sid=442edd04599593b24ebd28dc367c3001]("http://www.aspireoneuser.com/forum/viewforum.php?f=28&sid=442edd04599593b24ebd28dc367c3001")

Here is the website to get the custom kernel that works perfect on Ubuntu 8.10 and up.

[http://www.kuki.me/downloads/]("http://www.kuki.me/downloads/")

There is even a how-to for the installation located here.
[http://www.kuki.me/2009/04/how-to-install-kuki-linux-custom-kernel/]("http://www.kuki.me/2009/04/how-to-install-kuki-linux-custom-kernel/")

Enjoy the super fast boot-up times with this one!

---

### Post by bcasanov on 2010-07-10
Thank you for your kind and quick reply!  I looked through the links you provided, especially the first one (the Aspire One forum) and I have found my solution in this post: [http://www.aspireoneuser.com/forum/viewtopic.php?f=28&t=18428#p108232](http://www.aspireoneuser.com/forum/viewtopic.php?f=28&t=18428#p108232).  The solution was to install pavucontrol and unlock the input channels, muting one and leaving the other on high. I can now use my internal mic for all my apps including Skype!  I did not necessarily need to download and install a custom kernel to fix this particular problem, although some of the advantages of a custom kernel are compelling.  Thanks again for spending the time and effort in looking for the links to help me out.

---

### Post by kannank_udt on 2010-11-25
Thanks a lot !! it works !!

---

