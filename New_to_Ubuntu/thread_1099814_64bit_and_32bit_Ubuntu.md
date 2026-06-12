---
title: "64bit and 32bit Ubuntu?"
date: 2009-03-18
forum: New to Ubuntu
---

### Post by tricia56 on 2009-03-18
I have this daft problem.  I have a Ubuntu CD install disk with 32bit on one side and 64bit on the other.  BUT whenever I install I get a 64bit environment.  I have installed on laptop and PC and the same happens either way I do it.  I would like to totally migrate to Ubuntu but I am desperate to get boxee running and the how to on 64bit scares me...............chroot etc sounds beyond my abilities.

Anyone, what is happening here.

---

### Post by LowSky on 2009-03-18
you made a LiveCD with Ubuntu 32 bit version on one side and 64 bit on another?

isn't the answer simple, flip the CD over. If thqat doesn't work, reburn a copy of the 32bit version to use...

Otherwise use the 64 bit version those extra command are not that bad

---

### Post by tricia56 on 2009-03-18
Thanks , I have flipped the CD over of course, I know it seems daft.  But I have installed this many times and it is always 64bit version that installs.  The disc came off a Linux magazine, is there anyway of telling before you install what the version is that is being installed.

But yes I did flip the disk over.  I did!!

---

### Post by BDNiner on 2009-03-18
I say burn another copy. The disc may indeed have the 64bit version on both sides.

---

### Post by LowSky on 2009-03-18
well it seems like the CD they gave you was possibly 64 bit on both sides...

if you have high speed internet you can get the 32bit version quite easily from [www.ubuntu.com](www.ubuntu.com)

If you boot into Live CD mode open up firefox, then got to help, then go to "about firefox" and that will tell you which version you are using.

---

### Post by philinux on 2009-03-18
Just be happy with the 64 bit install it's really no different now just taking advantage of your machines capabilities.

Any terminal commands you may need are the same for both OS's

---

### Post by tricia56 on 2009-03-18
Okay guys, I will live with it.  Thanks

I am a girl and I am old but really I am not dumb
tricia

---

### Post by LowSky on 2009-03-18
Since when is being a girl  or old  equated to dumb?

Plenty of the forum is made up of women, maybe not 50/50 bt there is a good amount.

As for Boxxee those command it gave in the instructions should work just fine, any issues please post here or at the Boxee forums, as their forums might know more about Boxee then we do

---

### Post by philinux on 2009-03-18
> **tricia56 said:**
> Okay guys, I will live with it.  Thanks

I am a girl and I am old but really I am not dumb
tricia

These magazine cd's are not always 100%. I got linux format with **ubuntu** 8.04 on it. Installed it and it had installed xfce, kubuntu and gnome desktops all in the same install. Menu hell. That got the chop.

---

### Post by tricia56 on 2009-03-18
Sorry for the throwaway comment.  My misguided attempt at levity.

Maybe I should have started a new thread but I would really like to get linux and my Xbox360 working together.

I have been using Ubuntu for 2 weeks, have got it running on my PC and dual booted my laptop.  It is working like a dream.  I can't wait to jettison the unmentionable other OS forever.  

But the xbox is essential for me - I stream a lot of US TV (was there life before True Blood?) and need it working.  So I have done my research, this is what I think I know - in order to run the xbox I need a media server, controller and renderer.  

So this is what I have tried - coherence and rhythmbox - can see rhythymbox in WMP11 media sharing with no idea how to access it?  Or "throw" (non tech word) it to the xbox.

Twonky works fine but umm I have some philosophical disquiet about using that.

Mediatomb I can see in the network in the vista machine but no idea again how I use that in xbox360

Ushare worked for 2 mins and I could see that in xbox now I have lost it completely and no idea how to get it back.  Despite reading all I can on google.

So, that brings me back to boxee, I guess I need to just bite the bullet on this.  After doing all this I have no idea why I just have this fear about the how to on using it in 64bit environment.

Thanks for the help!

---

### Post by D3ath on 2009-03-18
I agree the CD's you can get sometimes I wouldn't trust I would do what everyone else tells you and get download the 32 bit or run the 64bit that it what i would do.

---

### Post by izizzle on 2009-03-18
I'm probably wrong, but perhaps the CD is defaulting to a 64-Bit Install because it wants to take full capability of your system.

---

### Post by BDNiner on 2009-03-19
With ushare you got to remember to restart the service every time you start the computer.

---

### Post by Yellow Pasque on 2009-03-19
Hi tricia, can you link to the howto you're using for Boxee on 64-bit?
Also, this command might help you:
```
sudo /etc/init.d/ushare restart
```

---

