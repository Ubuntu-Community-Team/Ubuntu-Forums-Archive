---
title: "Graphics help....."
date: 2008-12-24
forum: New to Ubuntu
---

### Post by elliottj85 on 2008-12-24
Can someone please help me with this

I had no video card support, so I registered the medibuntu thing and installed everything to do with ati (the manufacturer of my card). Then I restarted the system and it only boots up in low graphics mode, no effects etc. theres nothing listed in the hardware drivers list. I'm using intrepid and its one of the many problems I'm having.

Thanks in advance.

---

### Post by bluejay9109 on 2008-12-24
I'm having the same problems as well, and I can't figure it out either...

---

### Post by 2hot6ft2 on 2008-12-24
You'll have to give more info. If I walk into a auto parts store and say I need a starter for a ford what do you think they'll say? Sure here you go one size fits all. How about a model? I don't know it's blue.

Can I help whomever's next.

---

### Post by elliottj85 on 2008-12-24
I'm using intrepid on a sony vaio pcg-fx602 laptop
the card is an ati rage mobility, i checked the ubuntu wiki and its compatible.

I'm sorry, I'm very new at this and I've been trying to get it to work for the last three days

---

### Post by elliottj85 on 2008-12-24
bump
please help, everything I try is becoming a dead end.
I'm considering re-installing xp or trying another build, perhaps fedora.

---

### Post by nynoah on 2008-12-24
Sometimes other versions of Ubuntu will work.  This is a shot in the dark.  But try 8.04.  Sometimes graphics issues can be fixed in one distro and not the other.

---

### Post by elliottj85 on 2008-12-24
thanks, i'll give it a go
do you know if its possible to 'roll back to 8.04 or if i'll need to download another livecd?

---

### Post by igknighted on 2008-12-24
Before you do something drastic like reinstall, could you post the output of a few commands?

First: lshw -C display

Second: lspci | grep VGA

---

### Post by elliottj85 on 2008-12-24
hi there, thanks for the help

first:
WARNING: you should run this program as super-user.
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: Rage Mobility P/M AGP 2x
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 64
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=66 mingnt=8

second:
01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility P/M AGP 2x (rev 64)

---

### Post by igknighted on 2008-12-24
How old is this computer?  I don't think that card is supported anymore by ATI (at least in the official drivers).  I did a quick search on the AMD website but couldn't find it on the list of supported cards.  I would remove anything FGLRX-related and run the open-source ati driver instead.

---

### Post by elliottj85 on 2008-12-24
hi,
its a laptop and its about 6 years old. How would I uninstall the fglrx related drivers and then install the open-source ones?
thanks

---

### Post by igknighted on 2008-12-24
> **elliottj85 said:**
> hi,
its a laptop and its about 6 years old. How would I uninstall the fglrx related drivers and then install the open-source ones?
thanks

The open source drivers are part of the default install.  Run the command from the CLI: sudo apt-get remove --purge xorg-driver-fglrx

Then reboot into recovery mode and select Xfix, and then choose the ATI driver.  Continue with normal boot, and this should get you up and running.

---

### Post by elliottj85 on 2008-12-24
brilliant, thanks
that got me back into a higher resolution but I still can't get any desktop effects enabled which makes me think theres no card support.
any ideas?

---

### Post by igknighted on 2008-12-24
> **elliottj85 said:**
> brilliant, thanks
that got me back into a higher resolution but I still can't get any desktop effects enabled which makes me think theres no card support.
any ideas?

With a card that old, probably not.  You should keep searching, because there are some tweaks to make that driver work with desktop effects, but I wouldn't hold my breath.

---

### Post by elliottj85 on 2008-12-24
ok, where should i search for tweaks? as it stands i cant get it to play dvds or run google earth in the normal mode, both of which i could do perfectly well under windows xp.

---

