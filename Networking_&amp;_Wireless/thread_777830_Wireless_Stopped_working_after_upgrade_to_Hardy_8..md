---
title: "Wireless Stopped working after upgrade to Hardy 8.04"
date: 2008-05-01
forum: Networking &amp; Wireless
---

### Post by aneeshk on 2008-05-01
My Intel Pro/Wireless 3945 wireless card worked out of the box with 7.10, but stopped working after the upgrade to hardy.  Any suggestions?  The device manager does detect the card -- is it a driver issue?


Here is the output of lspci for my wireless card.

0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
        Subsystem: Intel Corporation Unknown device 1020
        Flags: bus master, fast devsel, latency 0, IRQ 4
        Memory at dfdff000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

---

### Post by number3 on 2008-05-07
I have a similar problem.  I have a inspiron 1720 and I just installed 8.04 and my wireless card was detected and I can see the wireless netowrks in my area.

However, I can't connect to my wireless network.  I put in my Passphrase, and the signal strength bars all light up but after a few seconds I get the window titled 'Wrieless network key required' and I'm do not have internet access.

I've tried both Authentication methods and I get the same results.

My wireless card is a Intel J3945 802.11a/g Mini-card.

I ran iwconfig and got the following results:

lo no wireless extensions

eth0 no wireless extensions

wmaster0 no wireless extensions

eth1 IEE 802.11g ESSID:"<my wireless name>" Nickname: ""
Mode: Managed Frequency:2.462 GHz Access Point: <my access point>
Bit Rate=54 Mb/s Tx-Power=27 dBm
Retry min limit:7 RTS thr:off Fragment thr=2346 B
Power Management:off
Link Quality=79/100 Signal level=-55 dBm Noise level=-127 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed becon:0

Any assistance would be greatly appreciated.  I'm brand new to Ubuntu so if there is additional information I can provide please let me know.  Thanks.

---

### Post by number3 on 2008-05-09
Solved my problem.

I manually configured my wireless connection and I had to switch my password type to 'WEP Key (hexadecimal)'.  I wasn't doing the second part when I was first trying.

However getting my wireless to work when it is set to roaming is still an issue I haven't figured out yet.

Another thing (and this is probably much to ask for) is that the wireless card light doesn't light up.  Even when I'm connected.  In fact since the upgrade to Hardy 8 my wireless light on my laptop hasn't turned on since.

Anyway, hope this helps out anyone with a similar problem.

---

### Post by vigyani on 2008-05-09
Please see 
[http://ubuntuforums.org/showpost.php?p=4919626&postcount=81]("http://ubuntuforums.org/showpost.php?p=4919626&postcount=81")

regards
Vig

---

