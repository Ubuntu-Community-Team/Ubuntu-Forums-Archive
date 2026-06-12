---
title: "install FGLRX on Intrepid"
date: 2009-01-16
forum: New to Ubuntu
---

### Post by josiano on 2009-01-16
Hello !

I have an Asus A6000 laptop with an ATI Radeon 9700.

I installed Intrepid Ibex and the default video driver is **vesa**.
Of course the screen resolution is bad (800x600).
I read somewhere that with Ubuntu 8.10 **fglrx** drivers were finally working with this graphic card (since oct 2008 or so) so I downloaded them from ubuntu repository.

But now, I don't know how to "use" them...
I tried to replace "vesa" by "fglrx" in /etc/X11/xorg.conf (Device Driver line) but xorg didn't like it and I had to revert it.
I think I have seen (months ago) that some-in between steps were needed but I forgot and I can't find anything for 8.10, and as I messed up this computer a few times already, I would like to make it nice and clean this time ;)

Any help on the necessary steps would be much appreciated =)

Cheers,

_j

---

### Post by 2hot6ft2 on 2009-01-16
Ubuntu Intrepid - Clocksource Fixed, System Still Hangs, AND No Videos - FGRLX Fixes It
[http://my.opera.com/PiklesOnFire/blog/2008/12/07/ubuntu-intrepid-clocksource-fixed-system-still-hangs-and-no-videos-fgrlx-f](http://my.opera.com/PiklesOnFire/blog/2008/12/07/ubuntu-intrepid-clocksource-fixed-system-still-hangs-and-no-videos-fgrlx-f)
I think that will be what you want.

---

### Post by josiano on 2009-01-16
Thanks for the link but I already have all this installed.
I have restricted-modules activated, fglrx drivers downloaded...
If I run aticonfig --initial I have the "Segmentation fault" error...
If I go in "System->Administration->Hardware drivers", it's written "No proprietary drivers are in use on this system"...
I really don't know what to do next...
Thank you.

_j.

---

### Post by 2hot6ft2 on 2009-01-16
You could install envy-ng to see if it shows the driver as installed or not.
```
sudo apt-get install envy-ng
``` you did reboot after installing it I take it.

---

### Post by josiano on 2009-01-16
Envy tells me that I have ATI 8-5.4.3.0ubuntu 4 driver installed...

But I'm afraid that it does not make any sense to me.
I could not get it working 4 months ago, but after reading a post mentioning that fglrx was fixed for 8.10 I decided o give it a try again but so far, no luck.

Cheers.

_j

ps: ubuntu is up-to-date, so why proprietary drivers don't show up after downloading xorg-fglrx drivers ?
pps: yes I did reboot
pps: thanks for your patience

---

### Post by josiano on 2009-01-16
By the way, here is the output of lshw -C display:
```
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: RV350 [Mobility Radeon 9600 M10]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: agp agp-2.0 pm bus_master cap_list
       configuration: latency=64 mingnt=8

```

I know it's not a good sign... and weirder, the graphic card is a Mobility Radeon 9700 (and not 9600), and my 8.10 install is fresh (1 day old).

Thanks.

---

### Post by josiano on 2009-01-16
Something I'd like to understand though, before downgrading to 7.10 (again), is why no proprietary drivers come up in the "Hardware drivers" menu ??
Also, I gave a try to pure:dyne distro, (with Live CD), and natively all was perfect.
Perfect resolution, etc...
The thing is, this is my girlfriend computer and she's even more a n00b than me, so no way for her not to have a dual-boot with windows, which is kind of tricky with Pure-Dyne).
Anyway, thanks for any help.

_j

---

### Post by josiano on 2009-01-16
Ok, I found an amazing workaround, thanks to that link:
[]("http://https://bugs.launchpad.net/ubuntu/%2Bsource/fglrx-installer/%2Bbug/284408")
It didn't install fglrx but thanx to ATI open source driver, I have the correct resolution at least !
For the archives sake, here is what I did (read the linked thread for more infos):
```
sudo sh /usr/share/ati/fglrx-uninstall.sh
sudo apt-get install --reinstall xserver-xorg-driver-ati
```

Thanks for the help !

_j

---

