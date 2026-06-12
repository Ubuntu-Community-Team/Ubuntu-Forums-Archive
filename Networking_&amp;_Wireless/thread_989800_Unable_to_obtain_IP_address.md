---
title: "Unable to obtain IP address"
date: 2008-11-22
forum: Networking &amp; Wireless
---

### Post by tim183 on 2008-11-22
Hi all,

I am using ubuntu 8.10 intrepid ibex 32 bit.
I ahve an atheros ar5007eg wifi card with the madwifi modules installed.
I have also tried ndiswrapper and the windows drivers and the recent ath5k module. All gave me the same result. I can see the available wireless networks, but cannot connect to them (and yes, they are OPEN networks).

So in frustration today I bought a usb wireless stick.

And guess what, same result.

So it appears it's something to do with my networkmanager congiguration or something, as it doesn't work on the open home network, or my open network in my office.

I was in the madwifi irc chan yesterday trying to get some help but no luck.

can anyone help?

here is sudo iwconfig
tim@tim:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:6425  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"roffs"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by SpaceTeddy on 2008-11-22
i am by far an expert on wifi, kernel modules or drivers... but by the looks of your output, this is not a hardware issue, but probably something to do with the connection itself. 

I can see that your wlan0 (probably your internal card ?) has an essid set and also picks up the AP. So the acctualy connection should be there.
What kind of encyrption does your Wifi have have you double checked the password and have you tried to set your ip manually after connection and then looking if you can at least reach internal hosts. 

this seems a bit weird to me... anybody else got any ideas ?

---

### Post by superprash2003 on 2008-11-22
its mostly because you are getting an ip addresss. post output of ifconfig from your terminal.. what is your router's ip address??

---

