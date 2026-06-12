---
title: "Screen Resolution in Jaunty - Portege 3500"
date: 2009-09-03
forum: New to Ubuntu
---

### Post by littlematt on 2009-09-03
Hi

I recently installed Jaunty onto my Portege 3500, but the resoltion is too low and there's a black band all the way round the edge. It should be 1280 x 768, but the highest available in preferences>Display is 800x600.

This happened in a preveious version of Ubuntu, whcih I fixed by manually adding another resolution option to a line in xorg.conf. It seems that Jaunty doesn't use xorg.conf so much/in the same way becuase now when I go there there isn't as much stuff there as before, and no lines that look like resolution. When I tried creating one, the desktop didn't apear after restart and I had to revert to my backup using recovery mode.

Why won't xorg.conf work like before, and what should I do?


littlematt

---

### Post by tgeer43 on 2009-09-03
It sounds like you just need to install the correct drivers for your graphics card. Until then you are running in Vesa mode which maxes out at 800x600.

What type of graphics adapter does your machine have?

tgeer

---

### Post by littlematt on 2009-09-03
I think it's a "trident" video card, which I had never hear of until I got this laptop!

---

### Post by tgeer43 on 2009-09-03
Enter this command in a terminal:
```
lspci
```The output should contain a line identifying your exact card by model number. Post it back here and we'll see what we can do.

tgeer

p.s. Trident has been around since the dark ages but most of their cards are not exactly considered 'cutting edge'.

---

### Post by littlematt on 2009-09-03
```
matt@matt-laptop:~$ lspci
00:00.0 Host bridge: ALi Corporation M1644/M1644T Northbridge+Trident (rev 01)
00:01.0 PCI bridge: ALi Corporation PCI to AGP Controller
00:04.0 IDE interface: ALi Corporation M5229 IDE (rev c3)
00:06.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 01)
00:07.0 ISA bridge: ALi Corporation M1533/M1535/M1543 PCI to ISA Bridge [Aladdin IV/V/V+]
00:08.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:0a.0 Ethernet controller: Intel Corporation 82551QM Ethernet Controller (rev 10)
00:0c.0 USB Controller: NEC Corporation USB (rev 41)
00:0c.1 USB Controller: NEC Corporation USB (rev 41)
00:0c.2 USB Controller: NEC Corporation USB 2.0 (rev 02)
00:10.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 01)
00:11.0 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 32)
00:11.1 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 32)
00:12.0 System peripheral: Toshiba America Info Systems SD TypA Controller (rev 03)
01:00.0 VGA compatible controller: Trident Microsystems CyberBlade XPAi1 (rev 82)
matt@matt-laptop:~$ 

```

---

### Post by roger_1960 on 2009-09-03
Hi

Look at and read this post.

[http://ubuntuforums.org/showthread.php?t=806835](http://ubuntuforums.org/showthread.php?t=806835)

This worked for me - you need to copy the xorg.conf file contents into yours (which may well be empty at present)

Monkeyplus post of may 25th + my post of Nov 30th are relevant

---

### Post by littlematt on 2009-09-03
> **roger_1960 said:**
> Hi

Look at and read this post.

[http://ubuntuforums.org/showthread.php?t=806835](http://ubuntuforums.org/showthread.php?t=806835)

This worked for me - you need to copy the xorg.conf file contents into yours (which may well be empty at present)

Monkeyplus post of may 25th + my post of Nov 30th are relevant

Thanks for the link - worked great.
Everything seems so much better when your screen is twice the size....

Cheers,
littlematt

---

