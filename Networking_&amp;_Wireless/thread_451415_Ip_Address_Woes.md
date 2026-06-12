---
title: "Ip Address Woes"
date: 2007-05-22
forum: Networking &amp; Wireless
---

### Post by davetarmac on 2007-05-22
HI all, I am wondering if you cna help me.

Ihave a fresh install of Feisty on a new partition. I have a WIFI card using the ACX111 chipset and the encryption on my network is WEP. I have checked the wiki and apparently my network card (D-Link Airplus G+ G520+) should work with Ubuntu 'out of the box'.

When I try to access the network using the network icon on the top bar, Ubuntu can see the network and I can apparently connect to it, although I do not get assigned an IP via DHCP, thus I cannot access teh Internet or any other network based things.

I have tried to set a static IP, only to suffer the same fate.

Please bear in mind that I am very new to this as I am looking for a way to phase out Windows.

Thanks and I look forward to reading your replies.

---

### Post by blazercist on 2007-05-22
please do "sudo iwconfig" in console and paste the output here.

---

### Post by davetarmac on 2007-05-22
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b+/g+  ESSID:""  Nickname:"acx v0.3.36"
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power=15 dBm   Sensitivity=1/3  
          Retry min limit:7   RTS thr:off   
          Encryption key:off
          Power Management:off
          Link Quality=39/100  Signal level=14/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

After booting in to Ubuntu, it found a network and connected (apparently, but I was still unable to browse the internet).

On looking at the above, I can see that it is not connected to any ESSID.

How can I fix this?

---

### Post by davetarmac on 2007-05-22
I've just tried booting back in to Ubuntu but none of my network configuration was saved - is there a reason for this?

Also, I can no longer get connected to the network using the same details as before, I just get the little spinning icon in the top bar and nothing.

So much for 'just works'...

---

### Post by blazercist on 2007-05-22
Try turning of WEP on your router and then try to connect.

You have no ESSID but you do have a nickname which is weird, you are saying that your router uses WEP but it seems that you have no WEP key stored.  It may be an issue with you driver or network-manager or the combination which is causing the issue, it seems to me that you can see the router but cant get an IP because your not giving it a WEP key.

If turning of WEP works then I will assist u further.

---

### Post by davetarmac on 2007-05-23
I remembered I had an Atheros card card in another machine so I ganked that and have stuck it in my system.

Booted in to Feisty and the network works like a dream (even if the signal isn't too great...)

Thanks for your help anyway, Blazercist.

---

