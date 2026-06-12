---
title: "Atheros wireless not working on Acer Aspire 5050 :( Help!"
date: 2007-08-11
forum: Networking &amp; Wireless
---

### Post by chadjohnson on 2007-08-11
I've tried everything to get my Atheros wireless working on my new Acer Aspire 5050. wlan0 does not show up when I do ifconfig, and iwconfig says "No such device" for wlan0.

I downloaded the official drivers from Acer, and then I blacklisted ath_pci in /etc/modprobe.d/blacklist and ran the following:
```

ndiswrapper -i net5211.inf
ndiswrapper -m
depmod -a
modprobe ndiswrapper

```

ndiswrapper -l says the following:
```

net5211 : driver installed
        device (168C:001C) present

```

lspci says the following:
```

02:00.0 Ethernet controller: Atheros Communications, Inc. Unknown device 001c (rev 01)

```

I've tried the broadcom driver, too. Also tried the one mentioned [here]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_fireboard/func,view/id,424/catid,2/").

The LED does not come on when I flip the switch on the front. Maybe the card is turned off?

---

### Post by bwtranch on 2007-08-11
I have a damn Acer machine, too. It's a desktop, but their notebooks are known for being POS. I will try to find something out.

---

### Post by chadjohnson on 2007-08-11
Cool. It's actually a very nice computer. The only thing that isn't working is the wireless.

---

### Post by bwtranch on 2007-08-11
Actually, there are a lot of pissed off people on this one. They seemed to be all windoze users so I would not put much stock in that. 

But, how about another distro? I obviously like Ubuntu, but how bout something else? I have Mandriva on my AMD 64 and it works good. And it's the one that is the Acer) Yeah, just opinions, whatever works. You might try it, I'm definately no expert when it comes to notebooks.:)

---

### Post by chadjohnson on 2007-08-11
dmesg | grep ndiswrapper says
```

[   50.268194] ndiswrapper version 1.47 loaded (smp=yes)
[   50.342874] ndiswrapper: driver net5211 (,01/20/2006,4.2.2.7) loaded
[   50.343922] ndiswrapper (NdisWriteErrorLogEntry:192): log: C0001389, count: 4, return_address: f8daf5d4
[   50.343926] ndiswrapper (NdisWriteErrorLogEntry:195): code: 0xf5faae00
[   50.343928] ndiswrapper (NdisWriteErrorLogEntry:195): code: 0x28
[   50.343930] ndiswrapper (NdisWriteErrorLogEntry:195): code: 0xf8b0a000
[   50.343932] ndiswrapper (NdisWriteErrorLogEntry:195): code: 0xf8b0a000
[   50.343999] ndiswrapper (mp_init:216): couldn't initialize device: C000009A
[   50.344003] ndiswrapper (pnp_start_device:439): Windows driver couldn't initialize the device (C0000001)
[   50.344014] ndiswrapper (mp_halt:258): device f1e28c00 is not initialized - not halting
[   50.344022] ndiswrapper: device eth%d removed
[   50.344040] ndiswrapper: probe of 0000:02:00.0 failed with error -22
[   50.345536] usbcore: registered new interface driver ndiswrapper

```


Using the Broadcom driver, I get the following:
```

[   49.727892] ndiswrapper version 1.47 loaded (smp=yes)
[   49.755529] usbcore: registered new interface driver ndiswrapper

```

---

### Post by chadjohnson on 2007-08-11
It would be good to learn something else, but if it works on other distros it should work on Ubuntu too. So you're using Mandriva (64-bit version?) on this same model, and the wireless card works? Is this using ndiswrapper and the Windows driver or a native driver?

---

### Post by bmartin on 2007-08-11
Try [this howto]("http://ubuntuforums.org/showthread.php?t=512828") I wrote. If the script doesn't work, let me know and do it the manual way.

---

### Post by chadjohnson on 2007-08-11
Thanks, bmartin, I will try that if I don't get the madwifi drivers working.

I believe the problem is that the radio is disabled, and the wlan switch does not work
> 
This sounds very much like a situation where there is a non-active software wlan switch. When resetting from windows, the switch stays active, but if cold-booting directly into linux without any means of activating the software switch (eg, acerhk or rfswitch kernel modules) the wlan radio will be disabled, and the HAL (or whatever driver) will spew out an error message. This is not always the case, but certainly a possibility for all laptop users experiencing these sort of problems.


Could someone please help me enable the radio (and maybe get the switch working too)? I've already tried editing /usr/share/hotkey-setup/acer.hk and added
```

setkeycodes     e055    $KEY_F13        # Wireless on
setkeycodes     e056    $KEY_F14        # Wireless off

```

---

### Post by chadjohnson on 2007-08-11
OK, apparently the card is AR5005G.

On [this page]("http://nosrednaekim.wordpress.com/2007/05/28/linux-on-the-acer-aspire-5050/") someone claims they got this working with ndiswrapper.

---

### Post by chadjohnson on 2007-08-11
Holy crap, bmartin's tutorial worked!!!!!!!!!!! Amazing. I guess the computer has an AR5007EG chipset. Sweet. Thank you. Now I have the perfect (cheap, durable) laptop.

---

### Post by erfahren on 2007-08-11
hmmm... I have that same card on an Acer Aspire 5100 and I'm not using ndiswrapper (not even installed). I just have HAL enabled in the Restricted Drivers Manager (enabled as default when I installed Feisty) and am using the madwifi driver which is just part of the linux-restricted-modules.

When I was trying to get mine going I needed WPA and used the guide here: [http://ubuntuforums.org/showthread.php?t=202834](http://ubuntuforums.org/showthread.php?t=202834) --- the only other thing I had to do was create that startup script he mentions.

it was the only one that really worked well for me.

if you want to check it out, I have a copy of my /etc/network/interfaces here: [http://ubuntuforums.org/showpost.php?p=3095729&postcount=2](http://ubuntuforums.org/showpost.php?p=3095729&postcount=2)


EDIT: I guess you posted you got it running as I was posting. 

I guess I did also need to go to Administration > Network and enter my DNS servers in there.

glad you're online. 

Is you left mouse-key broken yet? mine is, but still kinda works good enough. lol !

---

### Post by chadjohnson on 2007-08-11
Well, ok. It's partially working. The wlan0 interface shows, but I can't get on the network. I tried NetworkManager, iwconfig, setting the DNS server, and setting the IP address statically -- but still no-go. It's alot better than before, though :)

I'll try a fresh Feisty install and the madwifi drivers later on if it continues not working.

iwlist wlan0 sc shows my router.

EDIT: For some strange reason, it started working when I used wifi-radar. Now I can even run dhclient wlan0, and it will obtain an IP address. Very strange. The current drivers from Acer don't work, though, but the ones mentioned in bmartin's thread do...

---

