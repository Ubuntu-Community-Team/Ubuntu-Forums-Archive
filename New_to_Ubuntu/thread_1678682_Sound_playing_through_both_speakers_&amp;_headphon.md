---
title: "Sound playing through both speakers &amp; headphones"
date: 2011-01-30
forum: New to Ubuntu
---

### Post by adobrakic on 2011-01-30
I know there's already posts about this, but every thread that I've found hasn't helped. I've tried changing profiles, outputs, blah blah blah.. nothing has worked thus far. 

I have 64-bit Ubuntu 10.10. [_Here_](http://reviews.cnet.com/desktops/hp-pavilion-p6540y/4507-3118_7-34121958.html?tag=mncolBtm;rnav) are specification about my HP PC.

lspci:
```
ado@Ado-PC:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge Alternate
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:0a.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 5)
00:11.0 RAID bus controller: ATI Technologies Inc SB700/SB800 SATA Controller [Non-RAID5 mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3c)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS880 [Radeon HD 4200]
02:00.0 Network controller: RaLink RT3090 Wireless 802.11n 1T/1R PCIe
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
04:06.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev c0)
ado@Ado-PC:~$ 

```

Someone PLEASE help, I'm sick of unplugging my speakers.

---

### Post by ephexeve on 2011-01-31
I have the same problem. Really don't know how to solve it. Any help here?

---

### Post by jordsters on 2011-01-31
I have this problem on my other computer. If there is volume control on your speakers turn it completely down. My computer does it because it doesn't have speakers itself but the monitor has speakers built in.

Sorry if this was no help.

---

### Post by adobrakic on 2011-01-31
The speakers are actually built into my monitor :/ so no type of volume rocker or anything. 

@ephexeve, I've read in a few other threads that if you go to system > prefs > sound, going to hardware tab and changing the profiles at the bottom, it'll fix it. hasn't worked for me, but it's worth a shot.

---

### Post by jordsters on 2011-02-01
> **adobrakic said:**
> The speakers are actually built into my monitor :/ so no type of volume rocker or anything. 

@ephexeve, I've read in a few other threads that if you go to system > prefs > sound, going to hardware tab and changing the profiles at the bottom, it'll fix it. hasn't worked for me, but it's worth a shot.
Mine too, but it has volume control on the front. I don't know what else to recommend. :confused:

---

### Post by fabricator4 on 2011-02-01
> **adobrakic said:**
> The speakers are actually built into my monitor :/ so no type of volume rocker or anything. 

If you install the Salsa mixer, you'll see it has separate sliders for speakers and headphones.  I haven't tried it to see if works correctly on my machine as I hardly ever use headphones, but it just might do the trick for you.

Chris.

---

### Post by NightwishFan on 2011-02-01
I have a problem similar to this as well, alsa itself mutes my laptops speakers fine when I plug in headphones. If I have pulse installed, it mutes everything, and when I unmute it, it plays from both. :lolflag:

---

### Post by mikewhatever on 2011-02-01
The specs say the sound card is integrated, which probably means there are linein, lineout and headphone jacks. How do both the monitor speakers and the headphones get connected to one outlet at the same time?

---

### Post by adobrakic on 2011-02-02
> **fabricator4 said:**
> If you install the Salsa mixer, you'll see it has separate sliders for speakers and headphones.  I haven't tried it to see if works correctly on my machine as I hardly ever use headphones, but it just might do the trick for you.

Chris.

Thanks, I'll try this.

> **mikewhatever said:**
> The specs say the sound card is integrated, which probably means there are linein, lineout and headphone jacks. How do both the monitor speakers and the headphones get connected to one outlet at the same time?

There's one in the back, where the monitor speakers plug in to, and one in the front where I plug my headphones in.

---

### Post by Odisej on 2011-02-10
One more person with the same problem. Seems to be connected woth RTL8111 soundcard. I am using an Asus F5 laptop. 

Does someone have a suggestion.

I am using Kubuntu 10.10, the same issue with the latest Fedora.

Odisej:(

---

