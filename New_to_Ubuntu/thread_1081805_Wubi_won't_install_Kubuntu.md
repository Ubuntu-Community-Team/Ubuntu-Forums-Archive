---
title: "Wubi won't install Kubuntu"
date: 2009-02-26
forum: New to Ubuntu
---

### Post by Chan on 2009-02-26
I hope this is the right place.  After trying perhaps a dozen different ways, I'm not able to install Kubuntu by using Wubi.  I apparently can install Wubi, because on the restart, I'm given the choice of selecting Vista or Kubuntu.  But the next screen goes black, with just a blinking underscore cursor.  After waiting more than ten minutes, with no Kubuntu, I'd go thru the whole uninstall/install routine again.  But after many different attempts, I need to get pointed in the right direction.  Any thoughts?

Thanks, Chan

---

### Post by Crafty Kisses on 2009-02-26
Hey there Chan! We might need some more information so we can point you in the right direction here. So for example what are your system specs? Is it just a blinking cursor or are you getting "BusyBox?" What version of Kubuntu are you trying to install? I'd also like to know are you trying to install 32-bit or 64-bit Kubuntu? You also might want to try running the following on Windows:
```
chkdsk /r
```Make sure you run it on the same drive where you have installed Kubuntu, shutdown cleanly and then try to boot into Kubuntu again.

---

### Post by Chan on 2009-02-27
Codename: Tnx fr the reply.  In answer to your q's, I'm using Vista Home Premium, on a Lenovo 3000 H dual core Pentium.  Memory is 2Gig.  The black screen after the reboot of Wubi shows just a single underscore character, and NO text.  I'm wondering if there may be a problem with the Grub loader not finding Kubuntu.  The Kubuntu is supposed to be 32 bit.  I'll try running chkdsk /r on the E:/ partition, but have just run Defrag there with no apparent problem.  While I do that chkdsk, I'm going to send this, to make sure it doesn't fal thru the cracks.  I can landline you if that works with you..........Chan 1527 PST, Fri 27

---

### Post by Chan on 2009-02-27
Running chkdsk /r on E: drive, where Wubi and Kubuntu are stored, showed no problems. I will now try to install Wubi again, and then Kubuntu.....C 1622 PST feb 27

---

### Post by Chan on 2009-02-27
Codename:  I'm not sure what happened, but after running chkdsk /r on the E: drive, the system took off like a big bird, and Wubi brought up Kubuntu.  There must have been a gremlin or two hiding among all the bits on that partition, and you scared 'em away!

Now, you know, I've got to learn a whole new language, as I'm a complete Newbie to Kubuntu.  In dabbling for a few minutes with Kubuntu, I can see a lot of familiarizing will be needed, but with all the problems I've had with Windoze, I think it'll be worth it.  I suspect that I'll be hanging around the newbie group for a while.

Thanks for your good suggestion about trying Chkdsk.......Chan, Auburn, CA

---

### Post by Crafty Kisses on 2009-02-28
Hey Chan! I'm really glad that I could assist you with your problem. If you have any more issues or questions please let me know and I'll be glad to help you further.

---

