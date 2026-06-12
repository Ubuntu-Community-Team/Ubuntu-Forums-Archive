---
title: "VGN-B1XP Vaio Sound not working on Ubuntu 8.10 or 8.04"
date: 2009-01-21
forum: New to Ubuntu
---

### Post by escozul on 2009-01-21
I own a VGN-B1XP VAIO laptop where I've installed the 8.10 version of ubuntu and my sound card refuses to function. All other features work like a charm, however the sound card does not.

I looked at a few threads like: [http://ubuntuforums.org/showthread.p...vgn-b1xp+sound]("http://ubuntuforums.org/showthread.p...vgn-b1xp+sound")  where I was instructed to run:
> sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
and
> sudo apt-get install linux-sound-base alsa-base alsa-utils

which lead to a complete system crash and I had to reinstall ubuntu. that second time I tried to use the 8.04 version just in case I could make things work but the problem persisted.

when I run the lspci command I get the following:
> escozul@escozul-VAIO:~$ lspci | grep Audio
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)

Which looks right but just not works.

I also have the windows installation that came with the laptop on, and sound works there. Here are some device manager screens from windows:
[[IMG]http://www.imageshack.gr/files/egbvky0icldg08oq0o2m_thumb.jpg[/IMG]](http://www.imageshack.gr/view.php?file=egbvky0icldg08oq0o2m.jpg) [[IMG]http://www.imageshack.gr/files/mzlr3tif5jel7hmsha9m_thumb.jpg[/IMG]](http://www.imageshack.gr/view.php?file=mzlr3tif5jel7hmsha9m.jpg) [[IMG]http://www.imageshack.gr/files/1c7vmm26izi9zvxadxc1_thumb.jpg[/IMG]](http://www.imageshack.gr/view.php?file=1c7vmm26izi9zvxadxc1.jpg)
They are thumbnails... just click on them... ;) (just so that they don't take the whole screen)

I also tried to create this thread : [http://ubuntuforums.org/showthread.php?t=1041398]("http://ubuntuforums.org/showthread.php?t=1041398") but I was not so specific and I abandoned it.

I've also tried this solution but didn't work: [http://ubuntuforums.org/showthread.php?t=997506&highlight=sound+VAIO]("http://ubuntuforums.org/showthread.php?t=997506&highlight=sound+VAIO")

Also I found that one: [http://idyllictux.wordpress.com/2008/10/29/alsa-instead-of-pulseaudio-for-ubuntu-810-intrepid-a-non-destructive-way/]("http://idyllictux.wordpress.com/2008/10/29/alsa-instead-of-pulseaudio-for-ubuntu-810-intrepid-a-non-destructive-way/"). Should I try this one as well?? I'm a little reluctant...

Please some help. I'm getting frustrated.

Edit: Ah! BTW I also installed KUbuntu 8.10 on the same Laptop and I get no sound there either... However I haven't tried anyhting to fix that yet. First I will fix the main installation and then I will fix the K ver.

---

