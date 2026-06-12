---
title: "Updating LInux Kernel?"
date: 2009-10-31
forum: New to Ubuntu
---

### Post by Lazy-buntu on 2009-10-31
I filed a bug report about my sound not playing (not at login, not with mp3s, not with anything...my only output it shows is dummy stereo) since upgrading from 9.04 to 9.10. 

Someone replied telling me I was on the Jaunty Kernel still, how do I upgrade to the Karmic Kernel?

---

### Post by trulan on 2009-10-31
if you upgraded to 9.10, it installed the Karmic kernel (2.6.31-14).  You select which kernel to boot at your grub menu.  What kernel number are you choosing?

---

### Post by Lazy-buntu on 2009-10-31
uname -r

2.6.28-14-generic

---

### Post by Lazy-buntu on 2009-10-31
Do I need to install Grub2 you think? Or is kernel 2.6.31.... not installed on my computer?

---

### Post by Liolikas on 2009-10-31
Grub version you can use what you like.
Use synaptic or simply:
ls /boot
to find what you already have (full collection).

---

### Post by Lazy-buntu on 2009-10-31
Hmm the new kernel is showing. You think it's a conflict with start up manager? Or /boot/grub/menu.lst?


How do I fix that?

---

### Post by Lazy-buntu on 2009-10-31
> **Liolikas said:**
> Grub version you can use what you like.
Use synaptic or simply:
ls /boot
to find what you already have (full collection).

Would it just be easier to install grub2? How would I do that?

---

### Post by Lazy-buntu on 2009-10-31
After a failed attempt of trying to install grub2, I can't boot into ubuntu for some reason. It gives me an error 15. Windows still boots fine.

Can I do a fresh install of Grub only? Basically I want grub to be how it is after a clean install. Is this possible, if so, how?

---

### Post by Zoot7 on 2009-10-31
> **Lazy-buntu said:**
> Can I do a fresh install of Grub only? Basically I want grub to be how it is after a clean install. Is this possible, if so, how?
Try this:

Boot off a live CD, preferably one with grub legacy by default, I don't think this will work with the Karmic CD.

Rename /boot/grub to something else.
Then try these commands.
```
sudo grub-install /dev/sda
(assuming /dev/sda is the hard drive that houses Ubuntu)


sudo grub

find /boot/grub/stage1
root(hdx,y) - where (hdx,y) is the output of the previous command
setup(hd0)
```

That should re-install grub to the mbr and get you booting karmic again.
If it boots be sure to remove the grub 2 packages
```
sudo apt-get --purge remove grub-pc grub-common os-prober
```

---

### Post by Lazy-buntu on 2009-10-31
I'll try it right now, thanks!

---

### Post by Lazy-buntu on 2009-10-31
Error 15 

File not found or something along those lines. :(

---

### Post by Zoot7 on 2009-10-31
> **Lazy-buntu said:**
> Error 15 

File not found or something along those lines. :(
Hmm.. I would have thought the command to install grub to the hard drive would generate the appropriate files. Strange.
The Super Grub Disk might be worth a shot to set it up again.
**[http://www.supergrubdisk.org/]("http://www.supergrubdisk.org/")**

I think your best bet at this stage might be a clean install. :( If it stuck you on Jaunty's kernel after an upgrade then something went horribly wrong. Upgrades are known for their failures.
Also this thread might be of interest to you:
**[http://ubuntuforums.org/showpost.php?p=8071880&postcount=18]("http://ubuntuforums.org/showpost.php?p=8071880&postcount=18")**
It's a guide to revert Karmic back to Grub Legacy.

---

### Post by Lazy-buntu on 2009-10-31
I guess I'll bite the bullet and do a fresh install. I've already had to do it for the other 2 of my 3 computers I manage.

Karmic has been a pain in the butt. Oh well #-o](*,)

---

### Post by markackerman8@gmail.com on 2009-11-01
Hey Guys I am having real problems with sound too after a clean install of karmic and with grug2. ARghhhhhh I have looked everywhere and tried all the troubleshooting guides with no success double arghhhhh

Everything that points to an output device only shows the"dummy" (WITH PADEVICECHOOSER or system/preferences/sound_preferences),

but when I:

ack@Titan:~$ gnome-alsamixer ... it shows "Realtec ALC268"

or
ack@Titan:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC268 Analog [ALC268 Analog]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
Subdevices: 0/1
Subdevice #0: subdevic

or
ack@Titan:~$ lspci -v
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
Subsystem: Hewlett-Packard Company Device 30cc
Flags: bus master, fast devsel, latency 0, IRQ 22
Memory at f8400000 (64-bit, non-prefetchable) [size=16K]
Capabilities: <access denied>
Kernel driver in use: HDA Intel
Kernel modules: snd-hda-intel

ANY SUGGESTIONS?????

---

### Post by markackerman8@gmail.com on 2009-11-01
I fixed it by doing a COMPLETE reformat of my home drive and root and reinstall!!

phewwwww

---

