---
title: "Edgy Server Wireless... Where is it?"
date: 2006-11-18
forum: Networking &amp; Wireless
---

### Post by moomoo on 2006-11-18
I just did a fresh install of Edgy Eft Server. During the install, I configured my wireless card (using ath0) and it connected to my router. The install went just fine.

Now I've booted, logged in, and see no evidence that there's even a wireless card in my system. Am I asking too much to think that it might be configured if I configured it during install? :confused: 

I assume that the necessary software is there, or at least on the install cd. I just don't know how to go about making it work. Could anyone please help?

For the record, I've got a WG311T PCI adapter from NetGear.

Thanks!
Tim

---

### Post by exjinn on 2006-11-18
I'm having somewhat of the same issue.

I have a Netgear WG311T, it worked in Dapper. once upgraded to Edgy the card is shown but no connection. 

ifconfig yeilds Ath0 and wifi0 (for mad wifi I think)

I cannot connect to my wireless router unless I run the following: 

sudo ifconfig ath0 up
sudo ifconfig ath0 mtu 1500
sudo wifi-radar

I can then choose my network and connect. I don't know if this helps and I would love to find a permanent solution. :)

---

### Post by moomoo on 2006-11-18
exjinn,

I feel your pain, but I'm not even at the point where I can see an ath0 or wifi0 when I have booted from the hard disk. If I boot from the install cd and choose the 'repair' option then I can configure wireless using ath0.

Maybe someone knows which modules I need to install... Anyone? :) In fact, exjinn, you might be able to tell me since you've got the same adapter. I'm not sure how to do this either... :(

Tim

---

### Post by exjinn on 2006-11-18
if you run 

```
dmesg
```

do you see the words WIFI or ATHEROS in last few lines?

example

```
[17179593.468000] wlan: 0.8.4.2 (0.9.2)
[17179593.568000] ath_rate_sample: 1.2 (0.9.2)
[17179593.700000] ath_pci: 0.9.4.5 (0.9.2)
[17179593.700000] ACPI: PCI Interrupt 0000:04:01.0[A] -> GSI 17 (level, low) -> IRQ 177
[17179593.988000] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[17179593.988000] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[17179593.988000] wifi0: turboG rates: 6Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[17179593.988000] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
[17179593.988000] wifi0: mac 5.6 phy 4.1 radio 1.7
[17179593.988000] wifi0: Use hw queue 1 for WME_AC_BE traffic
[17179593.988000] wifi0: Use hw queue 0 for WME_AC_BK traffic
[17179593.988000] wifi0: Use hw queue 2 for WME_AC_VI traffic
[17179593.988000] wifi0: Use hw queue 3 for WME_AC_VO traffic
[17179593.988000] wifi0: Use hw queue 8 for CAB traffic
[17179593.988000] wifi0: Use hw queue 9 for beacons
[17179594.008000] parport: PnPBIOS parport detected.
[17179594.008000] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
[17179594.416000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[17179594.428000] wifi0: Atheros 5212: mem=0xdfaf0000, irq=177

```

---

### Post by moomoo on 2006-11-18
No mention of wifi0 or ath0 anywhere in the output of dmesg. :(

Does anyone know if I need madwifi? Or something else?

Thanks!

---

### Post by exjinn on 2006-11-18
This card uses the Atheros drivers which should, at least in my case detect the card under ubuntu.

I did some searching and it should be covered by the madwifi stuff.

Maybe this will help.

[MadwifiDriver]("http://doc.gwos.org/index.php/MadwifiDriver")

---

### Post by sonasi on 2006-11-18
madwifi is included in the linux-restricted-modules

I too just installed edgy server.  You get the "server" kernel installed (do uname -a).  You will find that you will not find the restricted modules built for the "server" kernel.  I went ahead and installed a "generic" kernel so I could use available restricted modules.  Of course, if you really want to keep the "server" kernel you can always download and build from madwifi.org

Hope this helps.

---

### Post by sonasi on 2006-11-18
I forgot to mention that you may need to revise your /etc/apt/sources.list to include packages from edgy universe and do an update so the restricted modules are available to you.

---

### Post by moomoo on 2006-11-26
sonasi - Thanks for the tip. That certainly did the trick. :)

---

