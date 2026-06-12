---
title: "[SOLVED] driver installed, but....."
date: 2007-10-15
forum: Networking &amp; Wireless
---

### Post by mandrill on 2007-10-15
much research: much confusion...

how do I fix this?

jim@monkey:~$ ndiswrapper -l
wpn311 : driver installed
        device (168C:0013) present (alternate driver: ath_pci)

the gui for ndiswrapper says no hardware

---

### Post by indie56 on 2007-10-15
Follow the instructions in this document 
[https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3](https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3)
Proceed from installation. Hope it helps

---

### Post by mandrill on 2007-10-15
always appreciate a reply, thank you.

here is what happened, as well as my other 2 windows pc's now not on network/without permissions:

jim@monkey:~$ ndiswrapper -l
wpn311 : driver installed
        device (168C:0013) present (alternate driver: ath_pci)
jim@monkey:~$ sudo modprobe ndiswrapper
Password:
jim@monkey:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"sidewinder"  Nickname:""
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1B:2F:0E:D0:CA   
          Bit Rate:54 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=38/94  Signal level=-55 dBm  Noise level=-93 dBm
          Rx invalid nwid:102511  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

jim@monkey:~$ ndiswrapper -a 1680:0013 WPN311
ls: /etc/ndiswrapper/WPN311/: No such file or directory
driver 'WPN311' is not installed (properly)!
jim@monkey:~$

---

### Post by mandrill on 2007-10-15
> **mandrill said:**
> always appreciate a reply, thank you.

here is what happened, as well as my other 2 windows pc's now not on network/without permissions:

jim@monkey:~$ ndiswrapper -l
wpn311 : driver installed
        device (168C:0013) present (alternate driver: ath_pci)
jim@monkey:~$ sudo modprobe ndiswrapper
Password:
jim@monkey:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"sidewinder"  Nickname:""
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1B:2F:0E:D0:CA   
          Bit Rate:54 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=38/94  Signal level=-55 dBm  Noise level=-93 dBm
          Rx invalid nwid:102511  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

jim@monkey:~$ ndiswrapper -a 1680:0013 WPN311
ls: /etc/ndiswrapper/WPN311/: No such file or directory
driver 'WPN311' is not installed (properly)!
jim@monkey:~$

Can someone help?

---

### Post by openaddict on 2007-10-15
It looks like from the error message ndiswrapper is looking in /etc/ndiswrapper/WPN311/ for your wireless card drivers.  If that's the case, create that directory and put the drivers there or modify your ndiswrapper to point to the correct location.

---

### Post by Junglizer on 2007-10-15
Dump your *lspci* output just to be sure, but given the 'ath0' dev name you're using an atheros chipped card. You'll want to use the [Madwifi]("http://www.madwifi.org") Atheros drivers, to get the best results, not NDIS.

---

### Post by mandrill on 2007-10-15
02:0d.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)

Appreciate the feedback, as always. Have done research, and posted several times, however most answers are partial, or assume far too much knowledge from a noob, or are conflicting.

I follow directions well, am willing to learn, and help others when I can, so I am hoping there is a definitive and methodical way to approach this, without assuming very much foreknowledge on my part. (ie, how to change the directory, what madwifi is)

Thank you in advance (anyone) for the benefit of your knowledge and experience.

---

