---
title: "Network Adapter not showing up"
date: 2018-08-22
forum: Networking &amp; Wireless
---

### Post by thenflux on 2018-08-22
Hi everyone, I am new to Lubuntu and I recently purchased an old laptop that has the specs of a 2015 Android Phone ([RedFox WIZBOOK Cloud]("https://redfox.global/product/wizbook-cloud/")), installed Lubuntu on it and ran into some problems.

Well before I proceed to the main problem, I'll give you some idea first about my situation.

[LIST]
[*]The  laptop I purchased had windows 8 installed on it. Naturally, I'd  upgrade into Windows 10, however, doing such broke the laptop and could  not (somehow) update the network drivers. What I did was restore the  laptop back to Windows 8 BUT the problem persisted. The network adapter  was not being updated.
[/LIST]
I did a  lot of sleuthing on the interwebs and made the WiFi work again by  installing Windows 10 and then installing .cab files for the **Broadcom 802.11n SDIO network adapter**. It works and now I have decided to change OSes into something lighter - Lubuntu.
When  I installed (try) Lubuntu, I saw that the WiFi would not  function. I thought maybe when I fully install Lubuntu, then the issues  would be fixed. However upon fully installing the OS, the problems still  persist.


[LIST]
[*]When I say the WiFI does not work, it's as if the network card does not exist. Entering the codes sudo lshw , sudo lspci , sudo lsusb into terminal will not show me a Network Adapter of any kind. I know it's a Broadcom 802.11n SDIO network adapter cause that's how I fixed it in Windows...

[/LIST]
Any ideas on a fix for my situation?
I  was thinking maybe, I can fix the network issue by doing something  similar to the windows10 solution - installing a specific .cab file to  make the network adapter work properly. Is there some similar solution  to this?
I'd really love to use Lubuntu and not Windows because of Lubuntu is not as resource hungry like Windows 10.
Thanks in advance!

btw this is what the pastebin showed

```
http://paste.ubuntu.com/p/tKrGmn43vH/
```

I don't know what to make of it. If you're seeing a connection, that's my phone tethered to the laptop.

---

### Post by chili555 on 2018-08-22
With your tethered connection, open a terminal and do:```
cd /lib/firmware/brcm
sudo wget https://raw.githubusercontent.com/armbian/firmware/master/brcm/brcmfmac43430a0-sdio.txt
```Reboot and tell us if the wireless is working.

---

### Post by thenflux on 2018-08-23
Holy crap that's amazing. Problem solved! Thanks!

---

