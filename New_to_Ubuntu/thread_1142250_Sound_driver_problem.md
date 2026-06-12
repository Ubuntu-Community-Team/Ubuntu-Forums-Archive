---
title: "Sound driver problem"
date: 2009-04-29
forum: New to Ubuntu
---

### Post by kevinwinner on 2009-04-29
Hi, I've been using Ubuntu 8.10 on my laptop and decided to install 9.04 on my handmade desktop.  Along with a host of other problems, I've been stumped on a problem with my sound card.

My motherboard is an MSI P6N Diamond, which has onboard X-Fi Extreme Audio.  I've tried many other bug fixes, so here's as much relevant information as I can think to provide.

Running

aplay -l

gives me back:

aplay: device list:217: no soundcards found...

lspci doesn't show anything other than products from nVidia Corporation (too many of them to post, but nothing resembling a sound card or chipset).  The onboard sound has worked perfectly for a year or two in XP/Vista, as have the speakers.  I have a pair of logitech USB speakers which I plugged in and which worked fine (for login noise and the test function) after rebooting.  Hardware drivers doesn't find anything for me, and installing/compiling ALSA and a driver I found from creative hasn't worked.

If anyone can help me with this, I would be very thankful.  Let me know if I can add any more useful information :D

-Kevin

---

### Post by kevinwinner on 2009-04-29
Here's the link to the product info page for my motherboard:

[http://msicomputer.com/product/p_spec.asp?model=P6N_Diamond&class=mb](http://msicomputer.com/product/p_spec.asp?model=P6N_Diamond&class=mb)

Historically, Creative has not supported my sound card in windows, I've had to get a driver through the MSI page.  However, neither page has listings for any kind of Linux drivers.

Oh, I'm running 32-bit ubuntu 9.04 here.

---

### Post by kevinwinner on 2009-04-29
bump

---

### Post by kevinwinner on 2009-04-29
I checked through my bios as detailed as I could and made sure I had everything configured correctly.  I made a few changes, which have added the following to my results when I run "lspci -v"

0b:00.0 PCI bridge: Creative Labs Device 7006
    Flags: bus master, fast devsel, latency 0
    Bus: primary=0b, secondary=0c, subordinate=0c, sec-latency=64
    Memory behind bridge: feb00000-febfffff
    Capabilities: [50] Power Management version 3
    Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/4 Enable-
    Capabilities: [80] Subsystem: Creative Labs Device 0010
    Capabilities: [90] Express PCI/PCI-X Bridge, MSI 00
    Capabilities: [100] Advanced Error Reporting <?>
    Kernel modules: shpchp

0c:00.0 Audio device: Creative Labs [SB X-Fi Xtreme Audio] CA0110-IBG
    Subsystem: Creative Labs Device 0010
    Flags: bus master, medium devsel, latency 64, IRQ 10
    Memory at febfc000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: [dc] Power Management version 3

However, I still have no sound cards detected when I run "aplay -l" and obviously no working sound yet.

---

### Post by kevinwinner on 2009-04-29
Per recommendations in some earlier threads, I tried installing gnome-alsamixer and using it to check sound card properties.  However, when I select sound card properties from the edit menu, I get a seg fault with the following error:

(gnome-alsamixer:4250): GLib-GObject-CRITICAL **: g_type_instance_get_private: assertion `instance != NULL && instance->g_class != NULL' failed
Segmentation fault

---

### Post by kansasnoob on 2009-04-29
Hmmm, not looking good according to this:

[http://www.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs](http://www.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs)

It shows Sound Blaster X-Fi =  [Unsupported] [PCI] Card delivered to developers. Completely new architecture. Creative have supplied a data sheet to developers. Development work has started.

Although some Soundblaster and emu based cards are supported by the alsa-firmware package in Medibuntu, but I'm doubtful:(

---

### Post by kevinwinner on 2009-04-29
That was my fear also.  Maybe someone knows of a 3rd party driver that would be worth trying?

---

### Post by kansasnoob on 2009-04-29
Have you tried installing the Medibuntu repo:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

And then:

```
sudo apt-get install alsa-firmware
```

You could then try restarting, or follow the "Do you have the sound modules installed?" instructions here:

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

and see if you get lucky and have at least some sound.

My only other suggestion is to install a cheap soundcard and wait for the new drivers to be developed.

I've used a couple of these:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16829128005](http://www.newegg.com/Product/Product.aspx?Item=N82E16829128005)
[http://www.startech.com/item-specs/PCISOUND4LP-4-Channel-Low-Profile-PCI-Sound-Card-Dual-Profile.aspx](http://www.startech.com/item-specs/PCISOUND4LP-4-Channel-Low-Profile-PCI-Sound-Card-Dual-Profile.aspx)

Nothing to brag about, but they work.

---

### Post by kevinwinner on 2009-04-29
Thank you.  The medibuntu repo didn't fix anything, I'll just pick up a new card for the time being.  Thanks again!

---

