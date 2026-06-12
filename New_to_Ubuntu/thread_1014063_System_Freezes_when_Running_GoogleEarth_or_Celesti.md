---
title: "System Freezes when Running GoogleEarth or Celestia"
date: 2008-12-17
forum: New to Ubuntu
---

### Post by Roger Allott on 2008-12-17
This has happened twice to me recently, and as I can't tell what sort of problem it is, I thought it best to ask in this forum rather than one of the specific ones. In any event, I've only been using Ubuntu for a few weeks so I'm a beginner anyway.

When I try to run either Celestia or Googleearth, the program launches but the graphics are shot to bits - a bit like getting a bad reception on a digital TV. I'd like to show a screenshot of what it looks like, but my screenshooting abilities aren't available when those progs run for some reason.

When I tried to run Googleearth a few minutes ago after a recent reinstall of it, I not only got the bad graphics but my system completely died on me.

On Windows, one has the option of Ctrl-Alt-Del to force closure of individual progs and processes. Is there a Linux alternative to do this? The only option I had, as far as I could tell, was to switch off the PC to force shutdown and cold reboot, which I think isn't particularly good for the long term health of my system.

As both Celestia and Googleearth are quite graphics-intensive, is there a problem with my graphics card and/or drivers, or is it more likely to be a memory management problem? Could someone walk me through a diagnostic check to see what my problem is and how I could fix it?

---

### Post by overdrank on 2008-12-18
Hi and if you could give us some info like the graphics model and the version of Ubuntu you are using we can try to help. :)

---

### Post by bwang on 2008-12-18
How dead did your system go? If the X server crashes, use the magic sysrq keys. Visit this site for more info: [http://fosswire.com/2007/09/08/fix-a-frozen-system-with-the-magic-sysrq-key](http://fosswire.com/2007/09/08/fix-a-frozen-system-with-the-magic-sysrq-key)

---

### Post by Roger Allott on 2008-12-18
> **overdrank said:**
> Hi and if you could give us some info like the graphics model and the version of Ubuntu you are using we can try to help. :)

Ah, good point. I'm running Ubuntu 8.10 on a Fujitsu-Siemens Amilo Pi 2512 laptop with dual Core Duo processors (I might have got the terminology wrong there) and 2Gb of RAM. As far as I know it has no seperate graphics card.

I got both Googleearth and Celestia from the Synaptic libraries' metadata things. I was quite surprised that the version of Googleearth that it got was 4.2 as opposed to 4.3 that Google is pushing on its website.

I'm v happy to provide whatever else might be needed about my system set-up, but I'm not sure how I get the info from my system without rebooting into Vista.

---

### Post by Liviu-Theodor on 2008-12-18
If you install from Synaptic, you could get also the 4.3 beta version. I did so and it works.

---

### Post by Roger Allott on 2008-12-18
> **bwang said:**
> How dead did your system go? If the X server crashes, use the magic sysrq keys. Visit this site for more info: [http://fosswire.com/2007/09/08/fix-a-frozen-system-with-the-magic-sysrq-key](http://fosswire.com/2007/09/08/fix-a-frozen-system-with-the-magic-sysrq-key)

Now THAT'S a bloody useful tip! Thanks.

Although with a laptop keyboard I think I'm going to need to grow a third arm. Or learn how to type with my toes!

---

### Post by handydan918 on 2008-12-18
Post the output of ```
lspci
```

That will tell us what your video adapter is.

---

### Post by Roger Allott on 2008-12-18
> **Liviu-Theodor said:**
> If you install from Synaptic, you could get also the 4.3 beta version. I did so and it works.

Yes, but I elected to go the metapackage route in the belief that it's the safer option.

I have a feeling that my problem probably exists as a result of being a tad overenthusiastic when I first installed Ubuntu. I updated the system as required then skipped off to Synaptic to see what goodies I could find. And I found a lot, obviously!

I think it's not at all impossible that I saw some package that I didn't understand but were described in a way that looked like they might be useful, and turned out to be some graphics or sound driver that conflicts with my hardware.

---

### Post by Roger Allott on 2008-12-18
> **handydan918 said:**
> Post the output of ```
lspci
```

That will tell us what your video adapter is.

Here's the output:

```
stuart@stuart-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
04:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)
```

---

### Post by Roger Allott on 2008-12-19
As a clue possibly for anyone who might have any ideas for me on this problem, note that I installed the medibuntu version of flahplayer (adobe-flashplugin) at the same time that I installed Googleearth on Wednesday. That app conflicts with flashplugin and with flashplayer-mozilla, so these got removed as part of the install.

I've just noticed that another problem has surfaced, perhaps related to the problem I had with Googleearth & Celestia or perhaps not. I can no longer watch vids on the BBC website, although as far as I can tell, they are flash vids.

What happens is that when I load a page that has an embedded vid on it, my PC temporarily freezes and the screen darkens, then after a few seconds it unfreezes and brightens back to normal settings, but the embedded vid is stuck showing .... well, here's a screenshot.

[http://62.233.105.201/screenshots/Screenshot-BBC-flashplayer.png](http://62.233.105.201/screenshots/Screenshot-BBC-flashplayer.png)

Confusingly, for me anyway, if I go to youtube I can see flash videos just fine.

---

### Post by Roger Allott on 2008-12-21
Have I provided all of the information necessary for someone to suggest a solution? If not, please let me know and I'll do my best to respond with something sensible.

---

### Post by Roger Allott on 2008-12-22
Pretty please?

Anyone with any ideas would be most welcome!

---

