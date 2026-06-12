---
title: "dynex wireless card issues"
date: 2008-05-18
forum: Networking &amp; Wireless
---

### Post by d4t4min3r on 2008-05-18
hh 8.04
i just bought a dynex wireless card 
dx-ebdtc and the card wont even turn on... when i turn the pc on the lights on the card dont flash or anything

network manager doesnt pick it up, i tried wireshark and wicd nothing

i installed the drivers on teh install cd with ndis nothing working there either

so right now im using  a linksys usb wifi device... wich doesnt work well either wich is why i bought the dynex :(

if it will help any here is some info

iwconfig
> d4t4min3r@d4t4min3r-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"linksys"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:18:39:FF:EA:F0   
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality=73/100  Signal level=-42 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

d4t4min3r@d4t4min3r-desktop:~$ 


nothing on lspci and
 
lsmod 
> usbcore               146028  6 ndiswrapper,rt2500usb,rt2x00usb,ehci_hcd,uhci_hcd


can someone please help me

---

