---
title: "Installation woes"
date: 2008-12-06
forum: New to Ubuntu
---

### Post by dissonance28 on 2008-12-06
Hello everyone!
I used to run Ubuntu a long time ago, I got rid of it for a few games I was playing at the time that didn't support it.  Now I've been wanting to reinstall.

I've tried several tiems over the past year to get myself Ubuntu Enabled again, only to fail at a similar place each time.  The last time I tried to install I would get as far as the orange bar filled most all of the way up (there would be about 2 "ticks" of it yet to go).  I tried passing many paramaters (everything I could find from searching, I honestly can't remember them all) to no avail.

This time I can get Ubuntu installed if I load into "Try Ubuntu without making any changes to your computer".  I try to reboot from there, and it will hang on a brown screen, I've tried a couple of keypresses there (crtl-alt-f1, and another combination that I forget) to no avail, it will just stay at the brown screen, taunting me.

I've enabled onboard video (Geforce 6100 chipset), tried 2 video cards (ATI X1900, and NVIDIA Geforce 7600) with the same end result, a brown screen staring me in the face.

I've also tried installng through windows, and with Wubu (I believe that is what it's called, a program I found on SourceForge that would let you install multiple Linux distros).

As i've been typing this (a slight update) now I can get to a logon screen, and it straight locks up.

Frankly, I'm flat out of ideas, if anyone has anything else to try, or needs more info to help out, I will try pretty much everything.

Thanks for all your time and help!

---

### Post by 2hot6ft2 on 2008-12-06
Did you try the OEM Install or the Alternate cd?

---

### Post by dissonance28 on 2008-12-06
This time it's the standard install CD, downloaded from Ubuntu.com, burned as an ISO.  I have tried the alternate install CD (last time I went through this) to the exact same point.

---

### Post by dracayr on 2008-12-06
what about starting the recovery mode?

dracayr

---

### Post by dissonance28 on 2008-12-06
recovery mode will do it's thing about half way through, then it will pop up something to the effect of there's no recover point, and that it's continuing as normal, to the same stop point.  (I'll get the actual message, it if will still give it to me, and editit in here in a moment)  Here we go, it's "Attempting to load recovery image" .  then "No recovery image, continuing with normal boot".

---

### Post by 2hot6ft2 on 2008-12-06
How about system specs like RAM since the livecd does require a minimum amount of RAM that could be an issue. That's why I mentioned the OEM installation method or the alternate cd as they both require less RAM since you're basically skipping the live part.

Does it take you to an xserver option?
Sometimes you have to wait a little and I've read that some people hold the ctr key down for a while and it has resumed for them, beats me how that worked but some said it did.

---

### Post by dissonance28 on 2008-12-06
I have a gig of ram, it will run the install just fine this time around (both through windows, and with a reboot to the cd).  Let me fire it up again and poke around some more.  I don't remember any XServer options, but I may just have never noted them.  Will also try the Crtl key trick that you mentioned.

I selected "Try to repair XServer" from the safe-boot menu.  It appeared to be sucessful (scrolled by a little too quicly for me to track down exactly what it all said, and now I seem to be able to reliably get to a login screen.  Unfortunately, once there I have no keyboard or mouse control.

By the way, I would like to say thank you to everyone thusfar (and still to come).  You at least give me things to try, so I'm not banging my head in exactly the same place all the time!

---

### Post by 2hot6ft2 on 2008-12-06
> **dissonance28 said:**
> 
As i've been typing this (a slight update) now I can get to a logon screen, and it straight locks up.

Thanks for all your time and help!

If you can click on the Options in the lower left at that point before it locks up and select "Gnome Failsafe" I think it was, it should finish then once you get it up and running log out selecting restart but next time go to Options and select "Gnome" the normal one I think you'll be in.

It worked for me once, but I don't recall exactly what they were named since it's been a long time.

Being able to log in even in "Failsafe mode" seems to create the image for the next boot. My guess, but it worked.

---

### Post by dissonance28 on 2008-12-06
I wish I could do that, however I do not have control of my mouse or my keyboard.  I get at most one cursor blink before everythign stops responding.

---

### Post by 2hot6ft2 on 2008-12-06
> **dissonance28 said:**
> I have a gig of ram, it will run the install just fine this time around (both through windows, and with a reboot to the cd).  Let me fire it up again and poke around some more.  I don't remember any XServer options, but I may just have never noted them.  Will also try the Crtl key trick that you mentioned.

I selected "Try to repair XServer" from the safe-boot menu.  It appeared to be sucessful (scrolled by a little too quicly for me to track down exactly what it all said, and now I seem to be able to reliably get to a login screen.  Unfortunately, once there I have no keyboard or mouse control.

By the way, I would like to say thank you to everyone thusfar (and still to come).  You at least give me things to try, so I'm not banging my head in exactly the same place all the time!

No mouse or keyboard oh man now that sux. Just have to ask though. You are using a wired mouse and keyboard, not wireless right?

---

### Post by kelean on 2008-12-06
A couple of things that come to mind as I read this.  
 1.  Do you have the correct version as in 32bit or 64bit.
 2.  Is the disk burned correctly.  Burn at the slowest speed for best results.
 3.  If you start the install make sure you remove the partitions and make them again.  That has helped me in the past.
 4.  Also once you start the install you can push Alt + F4 then you will be able to read what is going on during the install.  Might give you a clue as to what is going wrong.  Alt + F1 to get back to the install screen.

Good luck Kelean.

---

### Post by 2hot6ft2 on 2008-12-06
Don't know if this will help but here it is. Having a similar issue there where it freezes just before the login screen.
> **caljohnsmith said:**
> So if you do a cold start, does Ubuntu boot OK? If Ubuntu only has problems booting after you restart from Windows, you might try doing a Ctrl-Alt-Del at the Grub menu before booting into Ubuntu so that Grub reboots; then see if you can boot into Ubuntu OK.
And you said that "I've enabled onboard video (Geforce 6100 chipset), tried 2 video cards (ATI X1900, and NVIDIA Geforce 7600) with the same end result, a brown screen staring me in the face."

You did disable the onboard video when you installed the other cards right?

Sometimes we forget the details. Looking for ideas

This sounds like a good possibility [http://ubuntuforums.org/showthread.php?t=998851](http://ubuntuforums.org/showthread.php?t=998851)

Try a search for "Login freeze" and you'll find others with similar problems.

---

