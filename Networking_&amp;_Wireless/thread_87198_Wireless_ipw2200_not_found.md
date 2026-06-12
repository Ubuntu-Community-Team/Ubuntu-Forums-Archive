---
title: "Wireless ipw2200 not found"
date: 2005-11-07
forum: Networking &amp; Wireless
---

### Post by Vertical on 2005-11-07
Hello

I compiled my own kernel in ubuntu 5.10 (centrino laptop)

everything works ok, exept my ipw2200 - the wlan interface doesn't present in system

Elsewhere, I think WEP modules for my wireless must be loaded but I don't see them

Output of lsmod:

```

Module                  Size  Used by
ehci_hcd               33416  0
8139too                24320  0
rfcomm                 37276  0
l2cap                  23812  5 rfcomm
bluetooth              43908  4 rfcomm,l2cap
cpufreq_powersave       1664  0
cpufreq_performance     1792  0
cpufreq_ondemand        5404  0
cpufreq_conservative     6436  0
ipv6                  254336  6
pcspkr                  3424  0
rtc                    10936  0
ipw2200                71080  0
ieee80211              21192  1 ipw2200
ieee80211_crypt         4484  1 ieee80211
8139cp                 18560  0
mii                     4864  2 8139too,8139cp
yenta_socket           25100  0
rsrc_nonstatic         12288  1 yenta_socket
snd_intel8x0           31072  3
snd_ac97_codec         95356  1 snd_intel8x0
snd_ac97_bus            2048  1 snd_ac97_codec
snd_pcm_oss            51104  1
snd_mixer_oss          17792  2 snd_pcm_oss
snd_pcm                84488  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              22404  1 snd_pcm
snd                    48612  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
snd_page_alloc          8712  2 snd_intel8x0,snd_pcm
psmouse                37252  0
parport_pc             22980  0
lp                      8772  0
parport                21440  2 parport_pc,lp

```

What's wrong? Maybe I fogot something (kernel parametr or anything else)? kernel 2.6.14

My kernel config is here
[http://cabbage.nm.ru/config.txt](http://cabbage.nm.ru/config.txt)

---

### Post by mips on 2005-11-07
What laptop do you have and why did you compile your own kernel ?

---

### Post by Vertical on 2005-11-09
Fujiysu P7010
Centrino1.1GHz/855GME Chipset

'cause my own kernel is just faster :)

---

### Post by ming0 on 2005-12-26
I've got the exact same problem :(

I'm on an Asus W3V... I'm using kernel-image-2.6.14

:confused::confused::confused:

---

### Post by Lambert on 2005-12-26
Did you build the ipw2200 driver into your kernel?

If not you have to build a LKM module for your driver for the ipw2200. 

You can get source for the ipw2200 driver here.

[http://ipw2200.sourceforge.net/](http://ipw2200.sourceforge.net/)

After you download and untar the file look for an install file for instructions.

---

