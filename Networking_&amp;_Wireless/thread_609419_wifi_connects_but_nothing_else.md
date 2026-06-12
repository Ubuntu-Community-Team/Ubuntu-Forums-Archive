---
title: "wifi connects but nothing else"
date: 2007-11-10
forum: Networking &amp; Wireless
---

### Post by dlbrando on 2007-11-10
Ok, with no tinkering by me, 7.10 saw my routr and let me put in a access key to get the internet.  But the internet still says it cant connect.  Whats up.  There doesent seem to be a problem in the networking area.  It just doesnt give me a confirmation that it accepted the key.

---

### Post by spd106 on 2007-11-12
I think we're going to need a bit more information.

Can you open a terminal and run these commands, then post the results here.
```
lspci -nn
sudo lshw -class network
```

We only need the wireless specific parts, so you can crop the rest.

Also please check that you are entering the correct key, with the right key type and that your AP/router is set to broadcast it's SSID.

---

### Post by dlbrando on 2007-11-12
Ok I gotta get some stuff set up. I am hardwired to it now, and I get a nice fast internet, I can connect to other wireless connections, it is just when I try to go with the secured connection, the computer freezes and the caps key blinks.  I am using the roam mode and can switch between several free networks

---

### Post by dlbrando on 2007-11-12
ok, output from the first code:

00:14.0 Bridge [0680]: nVidia Corporation MCP51 Ethernet Controller [10de:0269] (rev a3)

06:09.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller [10ec:8185] (rev 20)

---

### Post by dlbrando on 2007-11-12
and the output from the second:

 *-network               
       description: Wireless interface
       product: RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 9
       bus info: pci@0000:06:09.0
       logical name: wlan0
       version: 20
       serial: 00:c0:a8:b8:e1:bd
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8180 latency=64 maxlatency=64 mingnt=32 module=r8180 multicast=yes wireless=802.11b/g



I am entering the same key that I set up on my fiance's laptop running windows, as well as my roomates.  I have reset the router to only be wep instead of the more secure setting.  I think it would work if I set it to unsecured, but I want to keep the neighbors out as I live in an apartment.  

When It asks me for the key, I have it set as a 128 bit passphrase, I can enter the key or the passphrase, in either the shared key or the open system options and get the same result of the system freezing up

---

### Post by spd106 on 2007-11-12
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/ndiswrapper/+bug/158176](https://bugs.launchpad.net/ubuntu/+source/ndiswrapper/+bug/158176) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				There are quite a lot of bugs with similar symptoms to yours, though the one I've linked to seems to be the closest match.

I'm not sure what to suggest, you could try using ndiswapper or maybe switch to WPA.

---

### Post by dlbrando on 2007-11-12
Yea, I talked to a buddy and he said he never could get a secured connection to work, He looked into it and saw that the driver search and build would be a pita.  So I left the wireless connection secured for my roomate and fiance, and I took one of the 6 mile long cat5 cables I have and ran it around the room to the couch and I just hardline in now.

I tried WPA and It wont work either

---

