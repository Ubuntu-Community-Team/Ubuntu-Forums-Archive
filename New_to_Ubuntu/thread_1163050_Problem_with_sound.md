---
title: "Problem with sound"
date: 2009-05-18
forum: New to Ubuntu
---

### Post by Scarlath on 2009-05-18
Okay, straight to the problem:

The sound in my headset is very, very low, even though I've set it to max. I do not have the same problem with my speakers, although this could very well be because I have a hardware volume control for those, which I dont on my headset. I don't think I've got a dedicated sound card, I'm most likely using the built-in thingy on the motherboard (not sure though). I do not have the same problem in Windows so it's not hardware related. So... how do I increase the volume? Also, is there any way I can check if my microphone works?

Not sure what information you need so I took a few pictures of the volume control: 

[img]http://img217.imageshack.us/img217/8683/skrmbildvolymkontrollhd.png[/img]

[img]http://img217.imageshack.us/img217/8885/skrmbildvolymkontrollhdm.png[/img]

Tell me if there's anything else you need!

(just realised it's in Swedish, but oh well, pretty sure you can figure out what it means anyway)




Oh, and on a **completely** different note, does anyone know if it's possible to sort **groups** alphabetically in Pidgin?

---

### Post by Scarlath on 2009-05-18
Just found another issue; whenever I press "delete" on a file, or "move to trash bin" (by rightclicking on it) they do not show up in the trash bin! What's going on? O_o

---

### Post by Scarlath on 2009-05-18
Bumpedibump!

---

### Post by Scarlath on 2009-05-18
... and another bump! (sorry!)

---

### Post by Scarlath on 2009-05-19
Odd. Now that I rebooted my computer a whole bunch of files appeared in my trash bin, I guess that problem is solved then. Please help me with the first ones though! :(

---

### Post by Scarlath on 2009-05-19
Bump again!

---

### Post by Scarlath on 2009-05-19
Bump-bump!

---

### Post by Scarlath on 2009-05-19
Surely someone must know a solution to this problem! :(

---

### Post by paradigm2 on 2009-05-19
Hmmm.  You've done the first thing I would suggest which is to check the settings in gnome-alsamixer... To investigate further, which exact sound card have you?

Open up a terminal and run:

```

lspci

```

and cut and paste here please.

I believe there have been some fixes for the hda-audio driver recently as well, however things are working great for your speakers so that makes me hesitant to suggest a non-standard upgrade so quickly.

---

### Post by Scarlath on 2009-05-20
Here you are: 
```
ludvig@ludvig-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation NV44 [GeForce 6200 LE] (rev a1)
03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 19)
04:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
ludvig@ludvig-desktop:~$ 

```

---

### Post by Scarlath on 2009-05-20
Bump!

---

### Post by Scarlath on 2009-05-21
Bump :(

---

### Post by Scarlath on 2009-05-22
Bump.

---

### Post by Scarlath on 2009-05-22
... and yet another bump.

---

### Post by Scarlath on 2009-05-22
I refuse to give up on this thread! \\:D/

---

### Post by Scarlath on 2009-05-22
Giving it another bump before I go to bed!

---

### Post by Volt9000 on 2009-05-22
Just FYI-- it's considered good netiquette to only bump once every ~24 hours.

---

