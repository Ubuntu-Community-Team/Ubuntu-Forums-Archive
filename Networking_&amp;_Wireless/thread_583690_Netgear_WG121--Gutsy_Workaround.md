---
title: "Netgear WG121--Gutsy Workaround?"
date: 2007-10-20
forum: Networking &amp; Wireless
---

### Post by ShahBucks on 2007-10-20
[SIZE="2"]I just recently installed 7.10- Gusty on my Dell Dimension 4600C.
I ran into a few problems enabling my Netgear WG121 wireless setup. I followed a good bit of the instructions on the help page - 

[https://help.ubuntu.com/community/WifiDocs/Device/WG121](https://help.ubuntu.com/community/WifiDocs/Device/WG121) with a few exceptions-

**1. I blacklisted p54usb & p54pci as well.**
**2. I used synaptic package manager to install ndsiwrapper instead of following step 3 on the page.**
[B]3. I downloaded the drivers directly from Netgear's site and continued on with the subsequent steps. When cheking via the command ndiswrapper -l i get:
netwg121 : driver installed
        device (0846:4210) present (alternate driver: p54usb)[/B]

**4. I continued on with the steps in the how-to, re-started and noticed that the netgear was a no-go. So... I took p54** out of the blacklist. All I got was a green light but no signal. The only way I could get any use out of it was to continually run the command sudo modprobe ndiswrapper even though I had followed the step in "Establishing a lasting connection" in the how-to**

I'd have to run the modprobe command everytime I booted up... 
Finally I just changed the name of the **'wireless'** directory in **/lib/modules/2.6.22-14-generic/ubuntu** to '**wireless_old**' so it wouldn't conflict with ndiswrapper. That seems to work fine so far. If anyone else has a better fix, pls. let me know! Thanks![/SIZE]

---

### Post by Ken101 on 2007-11-06
This work around solution worked for me too - also needed to reinstall the Netgear driver and reboot.

---

