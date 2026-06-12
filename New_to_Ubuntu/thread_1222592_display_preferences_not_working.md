---
title: "display preferences not working"
date: 2009-07-25
forum: New to Ubuntu
---

### Post by andrewbe on 2009-07-25
Got Ubuntu this afternoon for the first time.
sorry if this is a over asked noob question...
i think it could be something to do with my hardware. 
everytime i go to system/preferences/display, everything lags up heaps.
the window comes up but stays blank, everything else remains massively slowed down.

i have a ATI Radeon HD 4670.

if i go system/administration/hardware drivers

there is only one driver on the list. ATI/AMD proprietary FGLRX graphics driver.

any ideas?

thanks!

---

### Post by zeroseven0183 on 2009-07-25
> i think it could be something to do with my hardware

Could you give us more information about the system you're using?

Download the Hardware Driver in the list and restart your machine.

---

### Post by Mark Phelps on 2009-07-25
> ... there is only one driver on the list. ATI/AMD proprietary FGLRX graphics driver.

Have you already installed this driver? If not, install it.  If so, it may be an older version.  Go to the AMD/ATI site and download the latest driver -- I think it's up to Catalyst 9.7 now.

---

### Post by andrewbe on 2009-07-31
sorry, yeah i got it working. i dunno how, it just started working after a few resets.
thanks anyway!

---

### Post by betaparadogma on 2009-08-17
still not working here. Tried it several times. 

**System**

[LIST]
[*]Dell Optiplex 755 w.
[*]ATI Radeon HD 2400 XT
[*]2 x Samsung SyncMaster 910t
[*]Ubuntu 9.04 32bit
[*]Proprietory ATI driver installed
[/LIST]
**Issue**

Sometimes the Display Preferences Windows is showing the outer borders only and sometimes it shows contents, but

It allways slows my system down to hell, when trying to open Display Preferences. There is definitely something fishy it. 

Even tried installing for and back the whole operating system. But well: 

it just dont work. 

**Hint**s
Has anybody any hints how to manually add dual screen support to a configuration file.

<edit>
Seems like it is the same issue like here: [https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/366757](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/366757)
</edit>

<edit 2>
issue solved. for further reference go here and download the updates: [https://edge.launchpad.net/~xorg-edgers/+archive/ppa/+build/1149337](https://edge.launchpad.net/~xorg-edgers/+archive/ppa/+build/1149337)
</edit>

---

