---
title: "Two tiny problems I'm having with 9.04"
date: 2009-07-14
forum: New to Ubuntu
---

### Post by TheFloridiot on 2009-07-14
Neither of these problems did I have when using Intrepid Ibex

The first is a problem with basically anything flash on the Internet. Anything that uses flash runs quire slowly, even to the point of freezing up. This isn't an incredibly huge problem, but it does get annoying when I want to play a flash game :(

The second would be concerning screen saver and the desktop effects. I believe they're related, though I could be wrong. Regarding screen savers, I cant run them at all. No matter how simple it is, it lags a lot. I suppose it could very well be related directly to my computer, but I'm drawn from that idea because when I was on Intrepid Ibex, I could run a good chunk of them (as long as they weren't too complex) with no problem at all. Regarding the desktop effects, I have the option to turn them on via the Visual Effects tab on the Appearance Preferences window, but I haven't any customization options with them. I remember in Intrepid Ibex, I could go through the menus and find what I think was called Compiz and customize them to my liking, but no such option exists that I can tell.

I'm fairly new to Ubuntu, so can anyone help me out with this? Would be much appreciated.

---

### Post by nhasian on 2009-07-14
i bet you have an intel video card right?  intel video drivers were blacklisted because they were causing lockups so they were disabled by compiz.  if you have an intel card you can un-blacklist it.  this issue is already fixed in Ubuntu Karmic.

please give us the output of the following terminal commands:

```
lshw -C display
```

```
uname -a
```

---

### Post by TheFloridiot on 2009-07-14
> **nhasian said:**
> i bet you have an intel video card right?  intel video drivers were blacklisted because they were causing lockups so they were disabled by compiz.  if you have an intel card you can un-blacklist it.  this issue is already fixed in Ubuntu Karmic.

please give us the output of the following terminal commands:

```
lshw -C display
``````
uname -a
```Ah, you're right it is intel. Here, for the first.

> WARNING: you should run this program as super-user.
  *-display:0 UNCLAIMED   
       description: VGA compatible controller
       product: 82852/855GM Integrated Graphics Device
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
  *-display:1 UNCLAIMED
       description: Display controller
       product: 82852/855GM Integrated Graphics Device
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0And for the second, 

> Linux john-laptop 2.6.28-13-generic #45-Ubuntu SMP Tue Jun 30 19:49:51 UTC 2009 i686 GNU/Linux

Well, if they were causing lockups, wouldnt it be a bad idea to unblacklist it? Or was the problem actually fixed?

---

### Post by lovinglinux on 2009-07-14
[Jaunty Intel Graphics Performance Guide](http://ubuntuforums.org/showthread.php?t=1130582)

[Tips: Things that might improve Jaunty performance](http://ubuntuforums.org/showthread.php?t=1152095)

[**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567)

---

### Post by nhasian on 2009-07-15
now that we know you indeed do have an Intel video adaptor, copy/paste this terminal command and then reboot.  you will be able to enable the desktop effects in system->preferences->appearance
```

mkdir -p ~/.config/compiz/ && echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager
```

---

