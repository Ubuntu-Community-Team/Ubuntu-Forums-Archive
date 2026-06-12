---
title: "Help: Linksys WUSB11 v2.6 not working in feisty!"
date: 2007-11-05
forum: Networking &amp; Wireless
---

### Post by CyberCod on 2007-11-05
I've looked around for info in the forums and elsewhere, but can't find anything that is relevant.
I found another thread that mentioned this card, but they ended up focusing on v4 of this card.

I need to get the WUSB11 v2.6 wireless usb card to work in Feisty.
```

077b:2219 Linksys WUSB11 V2.6 802.11b Adapter

```

module at76_usb is loaded, and the card shows up in Network Settings, but I cannot acquire a connection.
All available connections appear to be very weak, even though my router is sitting right next to it.

Network Manager has been removed, and WiCD has been installed.
sudo iwconfig gives:
```

          IEEE 802.11b  ESSID:"SmithFamily"  Nickname:""
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:14:6C:D5:92:A4   
          Bit Rate:11 Mb/s   Tx-Power=15 dBm   
          Retry limit:8   RTS thr=1536 B   Fragment thr=1536 B   
          Encryption key:off
          Power Management:off
          Link Quality=88/100  Signal level=92/100  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

It cannot get a DHCP address from the wireless... and if I put in a static address, it claims to be connected, but it really isn't.

I know it works in Gutsy, but upgrading to 7.10 is not an option right now.

If you need any more info, I'll be glad to give it!

Any help would be appreciated, thanks!

---

### Post by CyberCod on 2007-11-06
No body has any advice for me?

Gee, I guess this is the price of popularity. 

Too much workload for volunteers to handle

---

