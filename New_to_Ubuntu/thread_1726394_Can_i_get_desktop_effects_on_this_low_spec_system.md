---
title: "Can i get desktop effects on this low spec system?"
date: 2011-04-11
forum: New to Ubuntu
---

### Post by ni ni on 2011-04-11
Hi all,

I'm a beginner at UBUNTU.  this is my laptop.

Intel Celeron M processor 1.60GHz
1.59GHz, 448 MB RAM
VIA/S3G UniChrome Pro IGP
X86-based 

It's got Nvidia :-(  with proprietary drivers.

My question is: is the spec too low to have fancy desktop effects?   when i try to enable them under appearance it says "desktop effects could not be enabled".  I got compizConfig settings manager, but i'm not sure what to do with that (obviously, if they can't be enabled i can do nothing!)

---

### Post by whitethorn on 2011-04-11
Could you tell us what kind of graphic card you have? Paste this into terminal and please post the results.

```
lspci
```

I think it should be possible you might need different graphic drivers.

---

### Post by ni ni on 2011-04-11
thanks for your reply.

```
niamh@niamh-laptop:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. CN333/CN400/PM880 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. CN333/CN400/PM880 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. CN333/CN400/PM880 CPU Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. CN333/CN400/PM880 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. CN333/CN400/PM880 Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. CN333/CN400/PM880 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:06.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)
00:09.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: VIA Technologies, Inc. CN400/PM800/PM880/PN800/PN880 [S3 UniChrome Pro] (rev 02)
niamh@niamh-laptop:~$
```

---

### Post by crispy_420 on 2011-04-11
Last time I check the VIA Unichrome hardware was not capable of running any gui effects. I think they lacked the proper 3D drivers at the time. I even had difficulty running certain games in Wine (mainly Peggle).

Maybe things have changed, been about a year since my last try.

---

### Post by ni ni on 2011-04-11
How do I check the VIA Unichrome hardware? :-S

---

### Post by bodhi.zazen on 2011-04-11
You can probably get some effects with xfce (xubuntu), has a built in composite manager, xcompmanager, or cairo-compmanager.

[http://cairo-compmgr.tuxfamily.org/](http://cairo-compmgr.tuxfamily.org/)

It will not be the full range of effects you might want, and it may be slow. You can improve performance if you turn off some effects.

If you want a full range of desktop effects you will need to upgrade your hardware.

---

### Post by crispy_420 on 2011-04-11
Some of the Enlightenment desktops have some decent visual effects as an option as well.

---

### Post by bodhi.zazen on 2011-04-11
> **crispy_420 said:**
> Some of the Enlightenment desktops have some decent visual effects as an option as well.

Good point. It would be nice to see a stable maintained distro that uses Enlightenment. Elive is probably closest.

Bodhi looks interesting , I tried to boot it, but it does not boot in vbox, which is, IMO, poor forum considering the vbox video drivers are open source and easy to install. Or the vesa drivers =)

---

### Post by crispy_420 on 2011-04-12
> **bodhi.zazen said:**
> but it does not boot in vbox

Haven't tried it in VirtualBox but it is running fine in VMWare Player for me. Sorry little off the original topic but it does show something relevant. I have decent visual effects with Bodhi and I never loaded the proper drivers.

---

