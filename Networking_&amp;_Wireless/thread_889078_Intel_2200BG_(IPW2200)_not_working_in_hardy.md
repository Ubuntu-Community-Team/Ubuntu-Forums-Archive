---
title: "Intel 2200BG (IPW2200) not working in hardy"
date: 2008-08-13
forum: Networking &amp; Wireless
---

### Post by Teuner on 2008-08-13
I just did a fresh install of ubuntu 8.04 LTS on my laptop the other day.
Basically everything is pretty much still at the post-installation defaults. All the latest updates have been applied.
Today i started testing my wireless connection. Unfortunately it's totally unusable at the moment.

Connecting process is very slow, once connected all seems to work fine for a while. However connection is lost quite often and it takes annoyingly long to reconnect. (Sometimes it won't reconnect at all.)

When the connection problem occurs my dmesg is flooded with these kind of errors:

ipw2200: Firmware error detected.  Restarting.

After doing some internet searching i reloaded the ipw2200 module with an extra debug option and i see stuff like this in dmesg:

[  592.037452] ipw2200: Firmware error detected.  Restarting.
[  592.037923] ipw2200: Start IPW Error Log Dump:
[  592.037928] ipw2200: Status: 0x00200020, Config: 00000342
[  592.037933] ipw2200: SYSASSERT 765250 0x0001d33c  0x00005a44  0x00000250  0x00000428  0x000000cc
[  592.037938] ipw2200: DMA_STATUS 765254 0x00027000  0x000273a0  0x01540001  0x00000000  0x00000000
[  592.037943] ipw2200: DMA_STATUS 765258 0x00028400  0x00028610  0x00540001  0x00000000  0x00000001
[  592.037948] ipw2200: DMA_STATUS 765261 0x00028000  0x00028250  0x00540000  0x9c6a4200  0x00000002
[  592.037953] ipw2200: DMA_STATUS 765265 0x00408000  0x00408000  0x30408200  0x00000082  0x00000003

This is then followed by lot's more number data being dumped.

As i'm already running the latest available ubuntu packages, which seem to contain the latests ipw2200 driver (1.2.2) and firmware (3.0), i'm slowly coming to the conclusion that a combination of hardy and 2200BG hardware is severely broken.

:cry:

This is not exactly the newest hardware anymore. Disappointing experience.
I find myself stuck with windoze if there's no cable...

---

### Post by coffeecat on 2008-08-13
> **Teuner said:**
> i'm slowly coming to the conclusion that a combination of hardy and 2200BG hardware is severely broken.

I haven't got any specific suggestions for you, but I can assure you that there is no general problem with Hardy and Intel 2200BG wireless. 2200BG works out of the box in Hardy for me on my Sony laptop - WPA and all. It's very stable, connects rapidly and I rarely have problems with it. In fact, I don't remember having a disconnection in Hardy.

Clearly there must be a specific problem with your setup and I'm sorry I have nothing constructive for you.

---

### Post by jhansonxi on 2008-08-24
I just went through some difficulty with a Toshiba laptop which uses a 2200BG.  The wireless would connect to a WPA2 network but not a WPA.  I wasted a lot of time trying to get the device to connect with both nm-applet and wpa supplicant command-line apps.  In the end it seems to be a timing or permissions problem, possibly with the Gnome password/key management system.  Opening Seahorse beforehand and granting access permissions when prompted seemed to get it working although the key didn't show up in the list until Seahorse was restarted.

---

### Post by joeinnes on 2008-08-24
The latest kernel modules update breaks wireless support for several cards, see here for more details:

[http://ubuntuforums.org/showthread.php?t=898541&highlight=latest+kernel+update+breaks+wireless](http://ubuntuforums.org/showthread.php?t=898541&highlight=latest+kernel+update+breaks+wireless)

---

### Post by coffeecat on 2008-08-24
> **joeinnes said:**
> The latest kernel modules update breaks wireless support for several cards, see here for more details:

[http://ubuntuforums.org/showthread.php?t=898541&highlight=latest+kernel+update+breaks+wireless](http://ubuntuforums.org/showthread.php?t=898541&highlight=latest+kernel+update+breaks+wireless)

If you read that thread carefully, you'll see that it is the -21 kernel/modules that is causing the problem. You have to have the proposed repository enabled to be able to get the -21 kernel. This kernel is causing problems elsewhere. This is not a specific wireless issue. This is about people enabling the proposed repository. Only enable the proposed repository if you are an experienced user willing to do QA for the package maintainers.

> 2. To offer for consideration, discussion, acceptance, or
 adoption; as, to propose terms of peace; to propose a
 question for discussion; to propose an alliance; to
 propose a person for office.
 [1913 Webster]Anything in the proposed repository is still being **considered** and **discussed** and, by definition, has not yet been **accepted**.

---

