---
title: "Network Manager Key Indey Help"
date: 2007-08-15
forum: Networking &amp; Wireless
---

### Post by ssc351 on 2007-08-15
Hey Everyone,

So I know Network Manager has a bug if you use any other that key index 1 on your WEPs.  However, I found a couple of posts where some users where able to work around... Here are two of the things that have worked for some people:

All set-up in /etc/network/interfaces
1.)  auto eth1
iface eth1 inet dhcp
        wireless-essid my_essid
        wireless-key2 my_second_key
        wireless-defaultkey 2

2.)auto eth0
iface eth0 inet static
address your_ip
netmask 255.255.255.0
gateway your_gateway
wireless-essid your_essid
wireless-key/1,2,3,4/ your_key
wireless-defaultkey /1,2,3,4/

---

### Post by ssc351 on 2007-08-15
> **ssc351 said:**
> Hey Everyone,

So I know Network Manager has a bug if you use any other that key index 1 on your WEPs.  However, I found a couple of posts where some users where able to work around... Here are two of the things that have worked for some people:

All set-up in /etc/network/interfaces
1.)  auto eth1
iface eth1 inet dhcp
        wireless-essid my_essid
        wireless-key2 my_second_key
        wireless-defaultkey 2

2.)auto eth0
iface eth0 inet static
address your_ip
netmask 255.255.255.0
gateway your_gateway
wireless-essid your_essid
wireless-key/1,2,3,4/ your_key
wireless-defaultkey /1,2,3,4/


Sorry, accidently hit enter and posted...anyway, I can't get this to work on my computer, my work uses a WEP key index of 3 and I have tried both of these as well as a combination.  I am running network manager...but I don't think i need to uninstall it because the people from previous posts got it working with NM.  Here is my iwconfig:

lo        no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"linksys"  Nickname:"linksys"
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:19 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/94  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:687  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.





Let me know what you guys think and if you need anything else like a dmesg! Thanks!

---

### Post by ssc351 on 2007-08-15
anyone anyone?

---

