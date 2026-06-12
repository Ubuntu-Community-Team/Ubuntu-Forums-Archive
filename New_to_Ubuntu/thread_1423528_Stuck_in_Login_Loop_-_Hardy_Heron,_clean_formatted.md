---
title: "Stuck in Login Loop - Hardy Heron, clean formatted hard drive"
date: 2010-03-06
forum: New to Ubuntu
---

### Post by MrCheeto on 2010-03-06
I have about had it with Linux. I'm starting to remember why I use MacOS, because I never pull my hair out over stuff like this.

So I've got a 50gb hard drive and I formatted it entirely to "Unallocated" with GParted.

Then I got on with installing Heron with a Live CD.

The install went fine and everything, but now it's asking me to log in. I log in, it smurfs around for about THREE MINUTES before the screen flickers and sends me back to the start like Dragon's Layer.

I can boot into Failsafe GNome, but no menu bar or ANYTHING comes up, just a desktop on which I can make new folders...yeah...

I booted into Failsafe terminal, and using what I learned from MacOS X I was able to determine that my Usr folder and its contents are all in order as they should be, so clearly the INSTALL went right.

So...now what?

The system is a 2ghz AMD Athlon with 1gb of ram.

I KNOW the disk works, because I just installed it in a VirtualBox on my MacBook Pro without a hitch.

---

### Post by stoogiebuncho on 2010-03-07
Do you have an ATI graphics card?  I found [this]("http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=863782") - but I don't know if it's related to your problem or not.

*edit* does Ubuntu boot properly when you boot from a liveCD?  (You said you installed from the liveCD, so I'm guessing it does)

---

### Post by Psumi on 2010-03-08
Login loop is most likely because you may have changed resolutions, GDM settings, video card information, or most anything related to display (Even BIOS.)

I would check everything.

This may or may not help too: [http://ubuntuforums.org/showthread.php?t=1318481](http://ubuntuforums.org/showthread.php?t=1318481)

---

