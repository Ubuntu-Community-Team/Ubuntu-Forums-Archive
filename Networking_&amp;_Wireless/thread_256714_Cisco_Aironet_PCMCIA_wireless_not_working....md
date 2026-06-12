---
title: "Cisco Aironet PCMCIA wireless not working..."
date: 2006-09-13
forum: Networking &amp; Wireless
---

### Post by SFDD on 2006-09-13
I have a Cisco Aironet 350 PCMCIA card that I'm trying to get working in a Dapper/Dell that has the dreaded Broadcom card that never worked well. When I insert the card, its lights come on and it shows in Network Settings control panel as "Active," but I can't get a connection. "iwconfig' ouputs the following:


```
lo        no wireless extensions.

eth0      no wireless extensions.

eth2      IEEE 802.11-DS  ESSID:"DD"
          Mode:Managed  Frequency:2.442 GHz  Access Point: 00:06:25:E6:8F:27
          Bit Rate:11 Mb/s   Tx-Power=20 dBm   Sensitivity=0/65535
          Retry limit:16   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=100/100  Signal level=-28 dBm  Noise level=-96 dBm
          Rx invalid nwid:10450  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:3039   Missed beacon:0

wifi0     IEEE 802.11-DS  ESSID:"DD"
          Mode:Managed  Frequency:2.442 GHz  Access Point: 00:06:25:E6:8F:27
          Bit Rate:11 Mb/s   Tx-Power=20 dBm   Sensitivity=0/65535
          Retry limit:16   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=100/100  Signal level=-28 dBm  Noise level=-96 dBm
          Rx invalid nwid:10450  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:3039   Missed beacon:0
```

I have already tried removing the Broadcom card in case that was interfering, but it made no difference.

Any ideas?

---

### Post by selam on 2006-09-18
I have also a Cisco Aironet 350 wireless card and i have not benne successful to access internet at my home. can anybody help me? thanks

---

### Post by NetworkGuy on 2006-09-18
Which card is the broadcom and which is the Cisco?  eth2/wlan0.

Can you disable the broadcom card in BIOS or from the Gnone Networking Panel?

What does ifconfig return?

---

### Post by blkcamarozr28 on 2006-09-20
Im running Xubuntu 6.06 and was getting this error below in /var/log/messages. 

Sep 19 22:10:35 localhost kernel: [17180312.460000] pccard: PCMCIA card inserted into slot 1
Sep 19 22:10:35 localhost kernel: [17180312.460000] cs: unable to map card memory!
Sep 19 22:10:35 localhost kernel: [17180312.460000] cs: unable to map card memory!

To fix the problem I had to install these packages on my Sony PCG-XG39 laptop and added a script that I found online to automatically switch the preable to Long. Give it a try and let me know if this fixes the problem for you. I see lots of other people online having problems. :)

sudo apt-get install pcmcia-cs
sudo apt-get install pcmciautils

sudo vi /etc/network/if-pre-up.d/cisco-aironet
==============Paste Config below for Preable = Long=================
#!/bin/sh
#
# This script takes care of configuring cisco wireless
# cards using the airo driver such as 340 and 350 cards.
# It is run by ifup.

AIROPROC=/proc/driver/aironet
CONFIG=Config
SLEEP=2

#some sanity checks
if [ ! -d $AIROPROC ] ; then
        exit 0
fi

for i in $AIROPROC/* ; do
   if [ -w "$i/$CONFIG" ] ; then
       echo "Preamble: long" > "$i/$CONFIG"
   fi
done
sleep $SLEEP
============================END PASTE============================
sudo chmod 755 /etc/network/if-pre-up.d/cisco-aironet

shutdown -h now
Power back on

==Run pccardctl in terminal==
pccardctl ident
==Output from pccardctl ident==
 x@x-laptop:~$ pccardctl ident
 Socket 0:
   product info: "Cisco Systems", "350 Series Wireless LAN Adapter", "", ""
   manfid: 0x015f, 0x000a
   function: 6 (network)
 Socket 1:
   no product info available

==Goto Applications -> System -> Networking==
You should see a Wireless Card Interface now :KS

---

