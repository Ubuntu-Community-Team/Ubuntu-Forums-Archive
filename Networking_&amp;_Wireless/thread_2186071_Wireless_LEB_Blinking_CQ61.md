---
title: "Wireless LEB Blinking CQ61"
date: 2013-11-05
forum: Networking &amp; Wireless
---

### Post by calin_ionut on 2013-11-05
Hello Everyone! I have a  CQ61-125EQ which the wifi led is blinking when i have internet activity (which i hear is normal). 

It uses ath5k and i tried all the solutions from [http://ubuntuforums.org/showthread.php?t=1481925&page=2]("http://ubuntuforums.org/showthread.php?t=1481925&page=2") but nothing stop the led from blinking :mad: :shock:

Can someone have any ideas, please???

---

### Post by varunendra on 2013-11-06
This is usually handled by the driver itself. Unless your driver (ath5k, the newer version does include some new options, but I don't remember what) supports controlling the led mode, there is probably nothing you can do about it.

To see what options are available with your ath5k driver, post back the output of -
```
modinfo ath5k
```

---

### Post by calin_ionut on 2013-11-06
Hi varunendra!

The output is:

```

filename:       /lib/modules/3.12.0-031200-generic/kernel/drivers/net/wireless/ath/ath5k/ath5k.ko
license:        Dual BSD/GPL
description:    Support for 5xxx series of Atheros 802.11 wireless LAN cards.
author:         Nick Kossifidis
author:         Jiri Slaby
srcversion:     3A12C9F4A4AAF96D5FF235B
alias:          pci:v0000168Cd0000FF1Bsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Dsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Csv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Bsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000019sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000018sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000017sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000016sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000015sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000014sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00001014sv*sd*bc*sc*i*
alias:          pci:v000010B7d00000013sv*sd*bc*sc*i*
alias:          pci:v0000A727d00000013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000012sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000011sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000007sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000207sv*sd*bc*sc*i*
depends:        mac80211,cfg80211,ath
intree:         Y
vermagic:       3.12.0-031200-generic SMP mod_unload modversions 
parm:           nohwcrypt:Disable hardware encryption. (bool)
parm:           fastchanswitch:Enable fast channel switching for AR2413/AR5413 radios. (bool)
parm:           no_hw_rfkill_switch:Ignore the GPIO RFKill switch state (bool)

```

The ath9k has the led option parameter:

```

parm:           blink:Enable LED blink on activity (int)

```

---

### Post by varunendra on 2013-11-06
> **calin_ionut said:**
> ```

filename:       /lib/modules/3.12.0-031200-generic/kernel/drivers/net/wireless/ath/ath5k/ath5k.ko
....
....
parm:           nohwcrypt:Disable hardware encryption. (bool)
parm:           fastchanswitch:Enable fast channel switching for AR2413/AR5413 radios. (bool)
parm:           no_hw_rfkill_switch:Ignore the GPIO RFKill switch state (bool)

```

Hmm.. interesting that despite being from the newest kernel, the driver has same parameters as the one in my 3.2.0-36 has. I don't remember which option, but I'm quite sure I saw a fourth parameter in ath5k a few days ago here on the forums.

Anyway, the driver 'You' have obviously doesn't have any option to control the LED. And I don't know if there is another way to 'force' such behaviour on it, sorry.

---

