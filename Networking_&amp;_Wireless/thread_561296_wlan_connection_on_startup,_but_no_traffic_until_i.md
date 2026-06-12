---
title: "wlan connection on startup, but no traffic until i change my ip"
date: 2007-09-27
forum: Networking &amp; Wireless
---

### Post by ulli.winter on 2007-09-27
hi,
i`ve got a new wlan router (fritz box phone wlan 7113) which acutally does work with my ubuntu 7.04 after i manually change the ip of my laptop after booting (in my case i alternate between 192.168.178.20<->192.168.178.33), but next time i start ubuntu, the wlan icon idicates that wlan is connected, but nothing works... even no ping reply
so i have to change the ip again....
but i dont think that it has something to do with the actual numbers of the adresses... 
rather some ip allocation problem or something like that

some facts:
WEP, router allows open system and shared key, tried dhcp and fix ips (dhcp seemed not to work at all), i tried adding open/restricted after  the wireless-key #### line in /etc/network/interfaces
...any ideas?

thanks a lot

---

### Post by noob12 on 2007-09-27
If DHCP isn't working at all, how is the initial address being assigned?

Do you dual boot the host?

Do you do any kind of adjusting to MAC address on either Ubuntu or Windows?

Can you workaround by setting an  address, netmask, and gateway statically in /etc/network/interfaces ?

---

### Post by ulli.winter on 2007-09-28
strange thing... my laptop has got a switch to deactivate wlan manually - if i do this before booting, and reactivate it after boot process wlan is working fine

wlan with dhcp is working when im changing settings from static to dhcp - but as all other wlan setting changes only for the current session, i have to change _something_ after next boot again to get it working

i dual boot: win xp wlan is working fine

no i didnt do any crazy stuff with my mac adress ;)

"Can you workaround by setting an address, netmask, and gateway statically in /etc/network/interfaces ?"
the settings there are the same as i typed them in the wlan control panel - so, with my current cofiguration i do use static settings

---

### Post by noob12 on 2007-09-28
If you are booting Windows and on Windows you are using DHCP (Acquire an address automatically), then there might be an explanation.

Let's see if we can get your DHCP working at boot normally.

I have a few suggestions:
- The behavior with the wireless switch suggests that you might need to toggle an option on a hotkey driver or the wireless driver when loading them.  Check your BIOS also to make sure your wireless device is enabled by default on boot (if there is a setting there that controls that).  What is the make and model of laptop?  and what does **lspci -nn** say for your wireless device?  

- If you are using NetworkManager, put both the wired and wireless device in "roaming mode".

---

### Post by ulli.winter on 2007-09-28
```
/etc/init.d/networking stop
rmmod ipw2100
modprobe ipw2100
/etc/init.d/networking start
```

is also a way to get it working....

my interpretation for the whole situation: the wlan "daemon" doesnt connect correctly on startup, so it has to be restarted one way or another (as above described... ;) )

but what could be the actual problem preventing wlan connecting correctly while booting?

---

### Post by noob12 on 2007-09-28
Yeah.  Sounding familiar. Send me the laptop make and model.

---

### Post by ulli.winter on 2007-09-28
sorry... missed your last reply...

roaming mode... doesnt work with encrypted networks, does it?
anyhow it didnt work in my case

no such  bios settings

lspci -nn :
```
01:02.0 Network controller [0280]: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter [8086:1043] (rev 04)

```

as it says intel wlan 2100 (centrino)
the laptop is a acer travelmate 291LMi

---

### Post by noob12 on 2007-09-28
Roaming mode and encryption work fine together.  You will get prompted for the key and the key is stored in the keyring.

This HOWTO thread [http://ubuntuforums.org/showthread.php?t=541953](http://ubuntuforums.org/showthread.php?t=541953)  applies to a similar laptop with the 2200 card.  You can follow the same HOWTO but _skip_ the section titled "**Load ipw2200 with led=1 option**".

Read the sections on setting up **acerhk** and particularly the last section on **Setting the wirelessled state manually via procfs at boot**.   That last part is what you are missing.   If you intend to keep the wireless in roaming mode always, the very last bit of the page provides a really easy way to do it.

---

### Post by ulli.winter on 2007-09-28
hmhm
didnt change anything without ipw2200 lines

tried with "Load ipw2200 with led=1 option" part but changed 2200 to 2100...
messed everything up :((

but after deleting the line and doing "sudo update-initramfs -usudo update-initramfs -u" again i'm where i've started - except that tha manual switch doesnt help anymore (since the roaming mode try i think)

;/

---

### Post by ulli.winter on 2007-09-28
uhm
i was just shutting down ubuntu.... und read the apearing status messages from boot process....
"starting wifi-radar   [OK]"
dont know when / why i set that to start automatically

anyhow i've deleted wifi-manager - and wlan works! fine! directly after booting...

sorry for taking up your time noob12, and thanks a lot for your engaged support!

1 2, i ubuntu! ;)

---

### Post by noob12 on 2007-09-28
You were supposed to skip the section on the 2200.  Everything else would have applied.

I'm curious: did you add the loading of the acerhk module and the script or are you running without them?

---

### Post by ulli.winter on 2007-09-29
i tried without and with the 2200 section, but didnt work;
after uninstalling wifi-radar wlan worked;
then i undid the changes from your howto - and it still works

wifi-radar really seems to be the problem in my case

---

### Post by noob12 on 2007-09-29
OK.  Thanks for the feedback.

---

