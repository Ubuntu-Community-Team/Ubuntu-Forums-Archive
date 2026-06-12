---
title: "Ubuntu 6.10 + BCM4306 Wireless"
date: 2007-03-18
forum: Networking &amp; Wireless
---

### Post by SavageNick on 2007-03-18
Hey guys - thought I'd finally do the 100% swap to a linux distro and erase my doze partition. I've had alot of experience with things in linux over the years, but not since I installed my wireless card. What a nightmare! I thought setting up X to use 2 monitors was a pain!

Anyway, in a attempt to check that "everything" is supported on my system I've been trying to get the Live CD boot of ubuntu to work with my wireless card - to no avail.

As i've said in the post, lspci says i have a Broadcom BCM4306 wireless network card - and from boot it appears as eth2 in my network devices list. Clearly at least a kernel module has been loaded...

I believe my main problem is something to do with the firmware - but by installing the fw ubuntu packages and also using the fwcutter on downloaded firmware (separate tries and boots obv) it just freezes my system when gnome goes to update the settings after i've enabled the card with the ssid etc. Is it possible that this is just not possible using the Live CD and I need to install my system properly first?

Also, am I going about this the correct way? I seriously don't like the idea of using ndiswrapper (too many things to go wrong) but if thats the only way to do it thats fine...

Would really appreciate the help guys - any1 else manage to get a BCM4306 card working under 6.10 AMD64???


Thx in advance.
Nick

---

### Post by SavageNick on 2007-03-18
> **Deepsea said:**
> Hello . I just came here   to annouce that, we are looking for some good forumers and good banner makers to start off our new GFX Community. There's hardly any rules, it's a fun community and it's 3 days old. You'll be amazed on some stuff, sorry for our gay *** skin, we are trying to find the perfect one.


(Register Here)
[GFXforums](http://z6.invisionfree.com/GFXInvision/)

Thanks,
Deep   :guitar:
As lovely as that sounds - that in no-way helps me with my problem does it?

---

### Post by Falados on 2007-03-18
Might want to try here:

[http://bcm43xx.berlios.de/](http://bcm43xx.berlios.de/)

Broadcom is one of those companies that don't like to release their specs, so drivers for their hardware are hard to come by unfortunately =\

On that note, the site actually links to this Wiki page relating specifically to Ubuntu:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

### Post by goldfrop on 2007-03-18
I couldn't get my BCM4306 working with the live cd at all. I had to do full install. Once installed, I  had great results with the combo of  fwcutter, the windows driver, ndiswrapper, and network manager. The only weird snag seems to be a difficulty in connecting to open wifi. Secured networks, no problem. Open network, can't seem to connect! Still working on that...

---

### Post by SactoBob on 2007-03-19
Goldfrop is right that you will have a much easier time once Linux is installed, but he made an important error.  The links above his contain the correct information.

Goldfrop's post makes it sound like you can use BOTH ndiswrapper solution and bcm43xx solution plus firmware.  This is wrong.

You have to decide whether to take the bcm43xx plus firmware approach OR the ndiswrapper approach.  You can only use one of those approaches - otherwise you have two drivers fighting over the same device.

By default, Ubuntu expects you to use the bcm43xx solution, since it loads that driver for you.  However, for legal reasons, Ubuntu does not provide the firmware you need - hence the need for fw_cutter etc.  This solution works fine - I have used it for my 4306, but speed is limited to 11 mps.  Falados gave you the right links.

A better performing solution is to blacklist the bcm43xx module (so it does not grab the wireless first) and use ndiswrapper with your windows driver.  It is also easy, and I think that all 4306 chips work with it.  Just make sure that you have ndiswrapper and the latest tools from the repository, and that you have blacklisted the bcm43xx module.  There is plenty of documentation for ndiswrapper, and it works great with this chip.

---

### Post by SavageNick on 2007-03-19
Brilliant! Thanks alot to all that posted replies - I wondered why ubuntu didnt actually come with the firmware in the first place...

Thats pretty much all my questions answered in one go hehe. I'll give a full install a go and hopefully it will all work out fine :)

Thanks guys

---

### Post by SavageNick on 2007-03-20
Sorry, posted this in the wrong place... Duh!!!

---

### Post by SavageNick on 2007-03-20
Hey guys - got my wireless card working (after some advice from u lot) - thx again for that! My main problem now is graphics.

I created my own ati driver package from the ati website and the tutorial from here (using module assistant). That all installs correctly etc and my card is recognised properly (X1950 Pro). After a bloody annoying AGP GART error which I fixed (needed to set the aperture size in my bios under the "hidden" BIOS settings), I now have some new errors (wonderful).

Firstly, I got:

```
 (EE) AIGLX error: dlsym for __driCreateNewScreen_20050727 failed 
(/usr/lib/dri/fglrx_dri.so: undefined symbol: __driCreateNewScreen_20050727)
(EE) AIGLX: reverting to software rendering
```

After some searching around the net I added the following lines to my xorg.conf:

```
 Section "ServerFlags"
	Option "AIGLX" "off"
EndSection
```

and the error disappears (however, I was pretty sure that AIGLX is needed for Beryl etc which is kind of the whole point of this). However, a new error appears in its place:

```

error opening security policy file /usr/lib/xserver/SecurityPolicy

```


I'll be honest here - my knowledge of linux has been exhausted. Various outputs would imply that its working properly:

```

nick@savage:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1950 Series
OpenGL version string: 2.0.6334 (8.34.8)

```

Although Beryl (and Cedega) are convinced that summat's not right (Cedega says hardware rendering failed and Beryl does absolutely nothing). I'm using 64 bit 6.10 ubuntu with a Nvidia Nforce 3 (250) mobo and an ATI Radeon X1950... Any ideas guys? Is it the drivers not working or the programs?

Thx in advance...

---

### Post by Falados on 2007-03-21
ATI is known for having very spotty linux support. Have you tried the FOSS 'ati' driver instead of fglrx?

---

