---
title: "Someone help!"
date: 2009-02-17
forum: New to Ubuntu
---

### Post by megaJuice on 2009-02-17
I found xorg.conf.failsafe and I think that'll fix my problems if I switch it with xorg.conf

How would I do that? Probably some sudo code that I have no idea how to do.

---

### Post by JustANewb on 2009-02-17
What are your problems?

---

### Post by megaJuice on 2009-02-17
Tried to install some ATI drivers, didn't work so I gave up. Now I can't get my generic card that came with my computer to work right. Stuck in low graphic mode.

All I want to do is change my xorg.conf and have it replaced with xorg.conf.failsafe

---

### Post by punx45 on 2009-02-17
```

cd /etc/X11

sudo cp xorg.conf xorg.conf.backup

sudo cp xorg.conf.failsafe xorg.conf


```

then i think you need to restart GDM

```

sudo /etc/init.d/gdm restart

```

someone correct me if im wrong, i havent used GUI in a while.

if you arent getting anywhere you can also reconfigure X
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by cariboo on 2009-02-17
You can accomplish  what you want 2 ways

1.

```
sudo cp /etc/X11/xorg.conf.failsafe /etc/X11/xorg.conf 
```

2.

Start in recovery mode, at the menu select xfix, once it is finished select resume and continue booting to the desktop.

Jim

---

### Post by megaJuice on 2009-02-17
These will replace xorg.conf with xorg.conf.failsafe right? I don't want to mess anything else up.

---

### Post by punx45 on 2009-02-17
> **megaJuice said:**
> These will replace xorg.conf with xorg.conf.failsafe right? I don't want to mess anything else up.

yes, and my version backs up xorg.conf first.

---

### Post by megaJuice on 2009-02-17
punx I did what you suggested, and almost everything is fine now. I'm out of low-graphics mode, but I can't open and of my games that run anything 3D (Toribash, Alien Arena,etc.) any ideas?

---

### Post by megaJuice on 2009-02-17
BUMP: Any ideas on how to get my 3D games to work? They won't even open. Pretty lame. Especially since that's all I really do, besides graphic design.

---

### Post by punx45 on 2009-02-17
my guess is failsafe mode is generic drivers, no 3D support.   you will have to install the drivers for your hardware.   im guessing that is what got you here in the first place?

---

### Post by megaJuice on 2009-02-17
Well no, not exactly. When I would try to use my computer with the ATI card it would be fine until I get to my desktop, after I login. It looked like my screen was split into a lot of different diagonal stripes, and I couldn't do anything. 

But now I've given up on that card, and am using the generic card my computer came with. I don't know what it is. Or anything about it, but it worked well enough for what I need it for.

---

### Post by megaJuice on 2009-02-17
Ok, so here's the deal now. I need to get 3D support back. It's driving me nuts. I'm using xorg.conf.failsafe so I'm not in low-graphics mode, but still no 3D support. Is there any way that I can fix this?

---

### Post by halitech on 2009-02-17
knowing what video card you have would help us out :)

open a terminal and post the output of
```
lspci
```and```
lshw -C video
```and then post the output back so we can help you

---

### Post by kansasnoob on 2009-02-17
Uh, maybe your hardware won't support 3D.

---

### Post by megaJuice on 2009-02-17
My hardware definitely does support 3D, at least games such as Alien Arena, Toribash, stuff like that, but it won't now.

results from lspci:

00:00.0 Host bridge: VIA Technologies, Inc. VT8753 [P4X266 AGP] (rev 01)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
00:08.0 Communication controller: Ambient Technologies Inc HaM controllerless modem (rev 02)
00:0e.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8233A ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 23)
00:11.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 23)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 40)
01:00.0 VGA compatible controller: ATI Technologies Inc Rage 128 PF/PRO AGP 4x TMDS

Results from lshw -C video:

WARNING: you should run this program as super-user.
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: Rage 128 PF/PRO AGP 4x TMDS
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list
       configuration: latency=32 mingnt=8

I don't think my crappy card I'm trying to use is an ATI, but I don't know. I do know that the other card I was trying to use is.

---

### Post by halitech on 2009-02-17
it definately is an ATI card according to this info.

I know the newer ATI drivers are not going to support this card for 3D. There was a thread on the older ATI cards that might help.

---

### Post by Kinetic Being on 2009-02-17
> **megaJuice said:**
> My hardware definitely does support 3D, at least games such as Alien Arena, Toribash, stuff like that, but it won't now.

results from lspci:

00:00.0 Host bridge: VIA Technologies, Inc. VT8753 [P4X266 AGP] (rev 01)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
00:08.0 Communication controller: Ambient Technologies Inc HaM controllerless modem (rev 02)
00:0e.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8233A ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 23)
00:11.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 23)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 40)
01:00.0 VGA compatible controller: ATI Technologies Inc Rage 128 PF/PRO AGP 4x TMDS

Results from lshw -C video:

WARNING: you should run this program as super-user.
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: Rage 128 PF/PRO AGP 4x TMDS
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list
       configuration: latency=32 mingnt=8

I don't think my crappy card I'm trying to use is an ATI, but I don't know. I do know that the other card I was trying to use is.


Run both those commands with 

```
sudo
```

in front of them. That will giver you superuser (root) access. That's all the sudo does, give that process root privliges. it stands for **S**uper **User** **DO**, meaning that the superuser is "doing" what is after sudo.

Install the restricted-extras package to get the proprietary drivers for your computer (including flash, mp3, dvd, etc, support.)

Ubuntu won't let you write the xorg.conf by hand (not that you would want to with your back-knowledge of linux), but the default (Debian) autoconfiguration works pretty much perfectly out of the box. (but if I'm wrong I'll be glad to post my xorg.conf that uses the fglrx (propietary) ati driver...

Sounds like all you needed for the ATI card to work was to install the restricted-extras package, or the ati opensource driver.

---

### Post by halitech on 2009-02-17
> **Kinetic Being said:**
> Run both those commands with 

```
sudo
```

in front of them. That will giver you superuser (root) access. That's all the sudo does, give that process root privliges. it stands for **S**uper **User** **DO**, meaning that the superuser is "doing" what is after sudo.

sudo isn't needed to run those commands, output is the same either way.

---

### Post by megaJuice on 2009-02-17
Yeah, no idea what I should do next.

---

### Post by halitech on 2009-02-17
go here and check if the card will handle 3D (ie. compiz)

[http://forlong.blogage.de/entries/pages/Compiz-Check](http://forlong.blogage.de/entries/pages/Compiz-Check)


if that works then we will look at getting 3D running but to be honest with only 4meg of video ram, I wouldn't hold my breath

---

### Post by megaJuice on 2009-02-17
I'm not trying to get Compiz running. All I want is to play a game. and I know this card can do it, because it did before I tried to install the new one.

---

### Post by halitech on 2009-02-17
Compiz uses 3D stuff so if it will run compiz, it should do your games but if it won't do compiz then it won't do games. A search on here doesn't look good on getting that age of a card to work for 3D but YMMV

---

### Post by megaJuice on 2009-02-17
Alright I ran the compiz-check and it says no, i can't use compiz with this card, but I knew that, and don't care. I don't want compiz. I know for a fact that my card CAN play the games I'm trying to play, because I've played them on this machine before! (4 days ago) Then I tried to install my new card, messed around with some stuff, forgot to back anything up, now I'm running off of xorg.conf.failsafe which apparently doesn't do anything 3D at all. Pretty much all I want to do is play Toribash, but it won't even open, nor will any other 3D type game (Alien Arena, glTron, etc)

Is there a way to install the driver for my card? That's all I want to know.

---

### Post by megaJuice on 2009-02-17
Any answers? Any ideas? Anyone? Anywhere?

---

### Post by halitech on 2009-02-18
you can try envy but I don't think it will work but willing to have you prove me wrong

---

### Post by punx45 on 2009-02-26
maybe...

> **punx45 said:**
> 

if you arent getting anywhere you can also reconfigure X
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

