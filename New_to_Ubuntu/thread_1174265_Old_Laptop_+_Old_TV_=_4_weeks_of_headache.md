---
title: "Old Laptop + Old TV = 4 weeks of headache"
date: 2009-05-30
forum: New to Ubuntu
---

### Post by wwwwolf on 2009-05-30
Hello, All;

I wonder if anyone would spare a moment to get me back on track on my little enterprise...

Basic facts:

- NEC Versa E680 Laptop
- Intel Extreme Graphics (built-in, duh)
- Component Cable (VGA > RGB)
- Sony Trinitron KV-AR29M64 TV Set

The laptop had "The OS That Shall Not Be Named" installed. While the OS was in English, the Intel Driver (user interface) was in Thai (which I can't read). Apparently the video chip allows for dual monitors and/or video out, so that is what I have been trying to do for the past 20+ days.

Using the installed driver, there was no way to send video to the old telly.
Reinstalling and upgrading produced no different result.

Booting with some Linux distros (eLive, Xubuntu, OZOS), I managed to get some promising 'flickering' on the old Sony.

I learned a *lot* these past few days by doing my homework: Googling stuff, reading about XConf parameters, Intel Chips, TV Specs, different signalling, cables etc... It's been great but now I am getting both exhausted and frustrated.

I know I must be close because last test made I could identify the mouse cursor on the TV screen; my take is I am missing or misusing some refresh rate or whatever frequency in my config.

I am hoping someone who's done this before can help.

Here's some relevant information:

xorg-conf.txt > last xorg.conf I tried
xorg-log.txt > xorg.log collected after using that conf
lspci.txt > lspci results
lsmod.txt > lsmod results
dispconf.txt > error message when trying to run displayconfig-gtk using that conf

displayconfig-gtk only started after I reset my xorg.conf using:
> sudo dpkg-reconfigure -phigh xserver-xorg

Kernels used should be fairly new. I can't really recall how many Live CDs I tried but I am sure they were all based on Hardy, Intrepid and Jaunty.

Latest reference sites I checked:
[http://linux.die.net/man/4/i810](http://linux.die.net/man/4/i810) (X config for Intel);
[http://linux.die.net/man/5/xorg.conf](http://linux.die.net/man/5/xorg.conf) (X config parameters);
[http://bbs.archlinux.org/viewtopic.php?pid=525912](http://bbs.archlinux.org/viewtopic.php?pid=525912) (Another poor soul trying some similar);
[http://ubuntuforums.org/showthread.php?t=221174&page=57](http://ubuntuforums.org/showthread.php?t=221174&page=57) (Just one of the several found);
[http://www.linuxquestions.org/questions/linux-laptop-and-netbook-25/intel-855gme-notebook-dual-monitor-310016/](http://www.linuxquestions.org/questions/linux-laptop-and-netbook-25/intel-855gme-notebook-dual-monitor-310016/) (Some similar configs, no result);

and the TV Manual, not attached but not too helpful anyway. The best information I got from it was "Your old and busted TV can receive either 525i/60Hz or 625i/50Hz Interlace signals".

By the way, S-Video (VGA > Single RCA connector) did not work at all.

Any ideas, anyone?

Thanks in advance.

Cheers

---

### Post by wwwwolf on 2009-06-04
Hello, All;

I consider the problem solved. Eventually I managed to get a 'dual monitor' configuration using an S-Video cable. As it turns out, the board allows for expanding 'Monitor 1' to 'Monitor 2' but not for 'Monitor 2' to be used as 'primary', which was what I wanted.

Since resolution on the old telly was lousy anyway, I might as well bite the bullet and spend some money on new hardware.

Cheers

--

---

