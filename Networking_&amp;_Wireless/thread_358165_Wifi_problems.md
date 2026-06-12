---
title: "Wifi problems"
date: 2007-02-10
forum: Networking &amp; Wireless
---

### Post by retrohelix on 2007-02-10
I recently installed ubuntu on my laptop, and I cannot get the wireless card working properly. 
I went through the wifihowto doc, and one thing i discovered was that my laptop would only connect to my router if both my interfaces ( wifi0 and eth1) were configured for my network and my network could not have any security enabled ( eg wep) . I went through the troubleshooting guide and I pretty much had problems with router association. I went ahead and installed wifi radar and all the networks around me, including mine, shows up but whenever I try to connect ( with or without security enabled on my router) it fails to assign an IP to me. Any help is much appreciated - Aman 

btw here are some readouts

liniaman is the name of my network
iwconfig output
> lo        no wireless extensions.

irda0     no wireless extensions.

eth1      IEEE 802.11-DS  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Invalid   
          Bit Rate:11 Mb/s   Tx-Power=20 dBm   Sensitivity=0/65535  
          Retry limit:16   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=-108 dBm  Noise level=-108 dBm
          Rx invalid nwid:12738  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:111511   Missed beacon:0

wifi0     IEEE 802.11-DS  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Invalid   
          Bit Rate:11 Mb/s   Tx-Power=20 dBm   Sensitivity=0/65535  
          Retry limit:16   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=-108 dBm  Noise level=-108 dBm
          Rx invalid nwid:12738  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:111514   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.

and

etc/network/interfaces
> auto lo
iface lo inet loopback


iface eth0 inet dhcp


auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp





auto eth0





iface eth1 inet dhcp
wireless-essid liniaman
wireless-key my_wep_key

auto eth1

iface wifi0 inet dhcp
wireless-essid liniaman
wireless-key my_wep_key


---

