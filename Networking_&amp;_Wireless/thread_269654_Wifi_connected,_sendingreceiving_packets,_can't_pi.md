---
title: "Wifi connected, sending/receiving packets, can't ping anything but localhost?"
date: 2006-10-02
forum: Networking &amp; Wireless
---

### Post by zombie_st on 2006-10-02
I'll preface this by saying I am something of a newbie, particularly where it comes to working with wireless, but I've been researching and tinkering for over two weeks now and still haven't come up with a solution, so I finally ask you, dear forumers.

I don't have any sort of net access through my laptop (a Thinkpad R40 running Breezy Badger) whatsover at this point (I'm posting this from a net cafe's computer right now). I'm trying to access my university's wifi now (I'm going to school in Shanghai at the moment, for what it matters. I'm not fluent in any form of Chinese yet, and so don't know who the Net Admin is here, or how to contact them, or if we could communicate at all. The English-speakers I've asked here say that the network is open to all, that there is no password, and that nothing should be blocking me. My classmates running XP instantly autodetected the network and were on without any trouble or password. Asking for things like static IP addresses and encryption specs gets me blank looks from everyone I've talked to so far). For awhile I was just out of range without realizing it, but even now that I'm in range and doing an iwlist scan shows me the school's Cells, I still can't access it for some reason, and I've no idea why. DHCP connection, no key, shows it sending and receiving packets in the Network Monitor, but can't ping anything but localhost and can't open anything in Firefox.

ifconfig gives me this (it's hand written and re-typed here, so please forgive any errors in formatting):
> 
ath0     Link encap:Ethernet HWaddr 00:05:4E:40:B5:DB
         UP BROADCAST RUNNING MULTICAST  MTU:1500 Metric:1
         RX packets:156 errors:1 dropped:0 overruns:0 frame:1
         Tx packets:5 errors:0 dropped:0 overruns:0 carrier:0
         collisions: txqueuelen:200
         RX bytes:13618 (13.2 KiB) TX bytes:1710 (1.6 KiB)
         Interrupt:11 Memory:e0b80000-e0b90000

lo       Link encap: Local Loopback
         inet addr:127.0.0.1 Mask:255.0.0.0
         UP LOOPBACK RUNNING  MTU:16436 Metric:1
         RX packets:355 errors:0 dropped:0 overruns:0 frame:0
         TX packets:355 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:0
         TX bytes:30698 (29.9 Kib) TX bytes:30698 (29.9 KiB)

and my iwconfig output:
> 
lo       no wireless extensions.

eth0     no wireless extensions.

ath0     IEEE 802.11b ESSID:"shnu"
         Mode:Managed Frequency:2.437 GHz Access Point:00:60:B3:35:06:08
         Bit Rate:11Mb/s Tx-Power:18 dBm Sensitivity=0/3
         Retry:off RTS thr:off Fragment thr:off
         Power Management:off
         Link Quality=24/94 Signal level=-71 dBm Noise level=-95 dBm
         Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
         Tx excessive retries:0 Invalid misc:0 Missed beacon:0


...please note that these numbers are all from when I was sitting outside the school library earlier, where I get better reception. If I run iwconfig from my room, the signal is far weaker and I usually get some Rx invalid nwid number bigger than zero.

what I get from lspci | grep Eth, in case it helps anything:
> 
0000:02:02.0 Ethernet controller:Atheros Communications, Inc. AR5211 802.11ab N
IC (rev 01)
0000:02:08.0 Ethernet controller:Intel Corp. 82801BD PRO/100 VE (MOB) Ethernet
Controller (rev 83)


and lsmod | grep mii, same reason
> 
mii       5248  1 e100


I also don't have access to a wired connection of any sort right now. I've tried plugging in to the broadband in the school's international student center twice, but I couldn't connect then either, though I didn't have time on those occasions to try to troubleshoot before the center closed. I'm open to the idea of trying a wifi card that's guaranteed to work with Ubuntu if the problem is really an incompatibility with the hardware (I've been recommended the Belkin F5D7010), but I'd rather make sure it's not a configuration problem before I invest in that option. I also have a copy of Dapper Drake I can install if anyone thinks that may help. Please keep in mind that I also don't currently have access to a computer where I'm allowed to download files I could transfer to my laptop. I might be able to bribe someone to download some programs for me if it's really necessary, but downloading and trying out various programs in the course of troubleshooting isn't really feasible right now, though that /may/ change next week after the national holiday is over.

Sorry for the wordiness of this post, but I wanted to make sure I'd pre-empted as many questions as possible so as not to waste your time asking. And thank you to anyone who reads or has any sort of suggestion. I'm open to any and all suggestions and please let me know if there's any more info you want. Thanks again!

---

### Post by amo-ej1 on 2006-10-02
you have no ip address assigned to your ath0 interface ... perhaps you should run something like dhclient ath0 ?

---

### Post by zombie_st on 2006-10-02
Thanks for the reply! ...And for pointing out my very obvious oversight! ](*,) 

Tried sudo dhclient ath0, but ended up getting the same error as the guy in the thread below [http://ubuntuforums.org/showthread.php?t=264614](http://ubuntuforums.org/showthread.php?t=264614)
...No DHCPOFFERS received.
No working leases in persistent database - sleeping.

Went to the WirelessCardsSupported page he found [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)
and found my card (which I miscopied in my first post; it is indeed an Atheros AR5212), which should apparently be working out of the box, but obviously isn't. The thread meandered into talking about someone else's router troubles, and the original poster solved their problem following help regarding their specific card, so now I once again don't know what to do. I realize people can manually set their IP, but without dhclient responding I don't know what I should set it to, and as I mentioned before, I'm not sure how to ask the net admin. Are there other tools I might use to find an IP?

I won't be able to reply again until tomorrow.. I'll probably do a fresh install tonight to make sure nothing I did in my tinkering is preventing this from working. I think I turned of IPV6 at one point, though I'm not sure that would be causing my problems. Still open to suggestions, and thanks again amo-ej1 for pointing me in the right direction!

---

