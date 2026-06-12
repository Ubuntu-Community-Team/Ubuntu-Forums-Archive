---
title: "Wireless Networks WPA secured showing up WEP secured not showing up"
date: 2007-11-17
forum: Networking &amp; Wireless
---

### Post by Zerol on 2007-11-17
Just finally got Wireless working on my Laptop again because I did a fresh install of Feisty I needed to reconfigure the Broadcom 4318 and that is kind of complicated.

After I finally succeeded I now dont see my own Network but I do see the one from the neighbours that live like 20 meters from my house. Mine isnt there at all and with WinXP I do see it and can use it also.

What is wrong? The neighbours their network is WPA secured and mine WEP. I use ndiswrapper and it worked before as well so why not now?

Im confused.

---

### Post by Zerol on 2007-11-18
Its not about the WEP or WPA.. I got the security off the network and it still doesnt show up? Whyyyyyyyy

---

### Post by Blutack on 2007-11-18
Could you run a 
sudo iwlist eth1 scanning
in a terminal please, when eth1 is your network device.  If you don't know your network device, run
iwconfig
and look for the one with wireless extensions
(for example, here is mine)

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:off/any  
          Mode:Managed  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:3  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:26515   Missed beacon:0

---

