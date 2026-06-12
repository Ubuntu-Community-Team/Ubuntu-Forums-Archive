---
title: "Upgrade to Ubuntu (no sound)"
date: 2010-06-10
forum: New to Ubuntu
---

### Post by FerrySabb on 2010-06-10
Hello everyone,

Two days ago, I've upgraded my HP Pavillion d4990y from Windows 7 to Ubuntu 10.04.  Before the updates, I didn't hear any sounds.  So thinking that I needed to upgrade, I did and nothing changed.  I have a Realtek ACL1200.  I have been back and forth to all the Ubuntu related forums especially this one and followed the troubleshooting instructions to the T.  To be honest, it was hard because I'm a newbie.  

Can anyone help me, please?  Thanks alot!

---

### Post by Mr. R on 2010-06-10
I also have an HP pavilion (different model), and it works directly from the the sound port, but I'm not very experienced with Linux. Do you have the speakers in that port or are you using a separate sound card?

---

### Post by FerrySabb on 2010-06-10
I have a Bose speaker hooked on the back of the CPU and I tried unplugging it to see if that was it but no such luck.  What do you mean it works directly from the sound port? 

Sorry guys Im a noob...  Gotta hold my hands a little bit.  Bear with me, pls.

---

### Post by nnamdi on 2010-06-10
hey how are welcome to ubuntu linux it is the right OS for humans lol

open u terminal undr application i.e the command line interface and run thise command 
```

lspci

``` 

then aste the result probably your sound card driver

---

### Post by FerrySabb on 2010-06-10
This is what I got.  How do you paste this in my sound card?  

> 00:00.0 Host bridge: Intel Corporation 82P965/G965 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82P965/G965 PCI Express Root Port (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82566DC Gigabit Network Connection (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HH (ICH8DH) LPC Interface Controller (rev 02)
00:1f.2 RAID bus controller: Intel Corporation 82801 SATA RAID Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G86 [GeForce 8400 GS] (rev a1)
02:00.0 PCI bridge: Creative Labs [SB X-Fi Xtreme Audio] CA0110-IBG PCI to PCIe Bridge
03:00.0 Audio device: Creative Labs [SB X-Fi Xtreme Audio] CA0110-IBG
04:01.0 FireWire (IEEE 1394): Agere Systems FW322/323 (rev 70)


---

### Post by nnamdi on 2010-06-10
[http://blog.gmane.org/gmane.linux.alsa.user/month=20100301](http://blog.gmane.org/gmane.linux.alsa.user/month=20100301)

this link might be useful ok

---

### Post by FerrySabb on 2010-06-10
Sorry tried everything on that site and still nothing.  I was reading something about the kernel being wrong.  I have 2.6.32-22.  Does anyone know if I have the right one?

---

