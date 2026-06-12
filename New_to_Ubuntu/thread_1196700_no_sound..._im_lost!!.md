---
title: "no sound... im lost!!"
date: 2009-06-25
forum: New to Ubuntu
---

### Post by amiacamal on 2009-06-25
im new to ubuntu so go easy on me..

right, i have a acer aspire 6935g, dual booted with vista. on vista i have full sound, on ubuntu i have none whatsoever. its an intel sound card if that helps.. i have no idea how to fix this, its wreakin my head. ohh  its ubuntu 9.04 if that matters. help plzz

---

### Post by halitech on 2009-06-25
can you open a terminal and post the results of the following commands
```
lshw -c sound
```
and
```
aplay -l
```

---

### Post by amiacamal on 2009-06-25
lshw -c sound gives:

WARNING: you should run this program as super-user.
  *-multimedia            
       description: Audio device
       product: 82801I (ICH9 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=HDA Intel latency=0 module=snd_hda_intel

aplay -l gives:
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC889 Analog [ALC889 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by halitech on 2009-06-25
your device is being seen and looks like the driver is loading properly. still in the terminal, run 
```
alsamixer
```and make sure nothing is muted (you'll see MM under it) if anything is muted, use the right arrows to go the that item, press M and then adjust the volume

---

### Post by amiacamal on 2009-06-25
still no luck. all volumes in alsamixer are up full, and nothing has m's under it...

---

### Post by halitech on 2009-06-25
what type of media are you trying to play?

---

### Post by amiacamal on 2009-06-25
songs, movies, anything! i dont even have the bongo jingle thing at login!
so confused >_>

---

### Post by halitech on 2009-06-25
the login sound should play no matter what, movies and music might need the ubuntu-restricted-extras package

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by wojox on 2009-06-25
Try going to System > Administration > Hardware Testing.

---

### Post by amiacamal on 2009-06-25
i still have nothing... i downloaded stuff b4 to make it play mp3 files ect, bt it still didnt give sound. i still have no startup bongos either.

---

### Post by amiacamal on 2009-06-25
bump >_> nooone got more ideas?

---

### Post by halitech on 2009-06-25
there is some more info here which is another sound problem I worked on

[http://ubuntuforums.org/showthread.php?t=1192529](http://ubuntuforums.org/showthread.php?t=1192529)

can you post the full output of
```
lspci
```

---

### Post by amiacamal on 2009-06-25
O_O  this means nothing to me....


00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 9600M GS (rev a1)
02:00.0 Ethernet controller: Attansic Technology Corp. L1e Gigabit Ethernet Adapter (rev b0)
05:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100

---

### Post by halitech on 2009-06-25
ok, looks like the same chipset so the info from jerry should help out. I noticed kerrie said an update just came in that resolved the problem so try checking for updates before we go any further.

---

### Post by amiacamal on 2009-06-25
now downloadin 48mb of updates >_> gimme a min

---

### Post by amiacamal on 2009-06-25
updates done and system rebooted. still nothing tho >_>

---

### Post by halitech on 2009-06-25
ok, time to follow jerrys instructions on page 2 of the link I provided

---

### Post by amiacamal on 2009-06-25
ill give it  a shot nd let ya know if it works. thx for ur help so far

---

### Post by halitech on 2009-06-25
hopefully it will work for you

---

### Post by amiacamal on 2009-06-25
still a no go im afraid

---

### Post by halitech on 2009-06-25
not sure what else to suggest at this point I'm afraid. hopefully someone else will come along and have an idea that will work.

---

### Post by goog64 on 2009-06-28
Hi,
I also have no sound for anything. I installed Ubuntu for the first time 5 days ago and I didn't even realise there was supposed to be a sound at startup!
I have followed all the suggestions in this thread to no avail. If you figure it out, I would really appreciate your letting me know.
Thanks
John

---

