---
title: "No wireless  after trying realy hard...ready to give up"
date: 2006-12-04
forum: Networking &amp; Wireless
---

### Post by dirkca on 2006-12-04
D-Link DWL-G650 Air Plus Xtreme G, Wireless Cardbus Adapter, 108Mbp
I have this card. I have been reading and reading, trying and trying...the darn thing will not work....well it did once for a few seconds and that was it. Can someone point me toward a solution" I am running Edgy on an Acer 230 Travel Mate.

The card is blinking, left right, left right....I am using network manager...it only shows the wired connection. The router is a d-link 624.

I have run a whole bunch of commands, went through the trouble shooting guide etc. I think it comes down to the card not being associated with the router.

Anyways, any help is appreciated.

---

### Post by FrodoB on 2006-12-04
The graphical setup utility is at the following menu:

System -> Administration -> Networking


If you are using WEP you just need a record for the card in your /etc/network/interfaces file like this:

iface ath0 inet dhcp
wireless-essid My_ESSID
wireless-key XXXXXXXXXXXXXXXXXXXXXXX
auto ath0

To edit the file manually just open a terminal and type:

sudo gedit /etc/network/interfaces

To make things easier you can turn off all security in your router and remove the wireless-key XXXXXXXXXXXXXXXXXXXXXXX from the interfaces file and then reboot and it should work if you have the correct ESSID set.

---

### Post by dirkca on 2006-12-04
Thank you...there is progress.

Both lights on the card flash simultaneously....but still not working. I turned security off on router.

---

### Post by FrodoB on 2006-12-04
What happens when you use at a terminal prompt: (outputs, etc.)

iwconfig

sudo iwlist ath0 scanning

sudo ifdown ath0

sudo ifup ath0

---

### Post by PilotJLR on 2006-12-04
> **dirkca said:**
> 
The card is blinking, left right, left right....I am using network manager...it only shows the wired connection. The router is a d-link 624.


So you installed and are running gnome-network-manager? If so, you have to DISABLE the wirless connection thru System | Admin | Networking!!!

Disable the connection in this way, reboot, then left-click the network-manager icon in the upper-right of the screen.

So long as the interface is enabled in the default networking tool, it will not work in gnome-network-manager.

---

### Post by dirkca on 2006-12-04
see post below

---

### Post by dirkca on 2006-12-04
jim@jim-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"11mbCH7"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: 00:02:6F:01:C0:9B   
          Bit Rate:2 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3  
          Retry:0ff   RTS thr:0ff   Fragment thr:0ff
          Power Management:0ff
          Link Quality=15/94  Signal level=-80 dBm  Noise level=-95 dBm
          Rx invalid nwid:109  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

jim@jim-laptop:~$ sudo iwlist ath0 scanning
Password:
ath0      Scan completed :
          Cell 01 - Address: 00:13:46:CD:95:FA
                    ESSID:"home"
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality=44/94  Signal level=-51 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
          Cell 02 - Address: 00:18:3F:A9:7F:B1
                    ESSID:"tcope"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=9/94  Signal level=-86 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
          Cell 03 - Address: 00:13:10:E9:BD:70
                    ESSID:"temptemp"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=4/94  Signal level=-91 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
          Cell 04 - Address: 00:02:6F:01:C0:9B
                    ESSID:"11mbCH7"
                    Mode:Master
                    Frequency:2.457 GHz (Channel 10)
                    Quality=12/94  Signal level=-83 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
          Cell 05 - Address: 00:12:17:1A:58:47
                    ESSID:"linksys"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=6/94  Signal level=-89 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
          Cell 06 - Address: 00:0D:3A:73:D8:7F
                    ESSID:"MSHOME"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=7/94  Signal level=-88 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
          Cell 07 - Address: 00:13:46:F3:21:B0
                    ESSID:""
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=2/94  Signal level=-93 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:ath_ie=dd0900037f010100200000

---

### Post by dirkca on 2006-12-04
It wont even show in network manager whether its disabled or enabled.

---

### Post by dirkca on 2006-12-04
Any ideas as to what I can do?

---

### Post by PilotJLR on 2006-12-04
> **dirkca said:**
> It wont even show in network manager whether its disabled or enabled.

Just to confirm... you disabled the wireless interface in the Networking tool , **THEN REBOOTED THE COMPUTER**, and it still is not in gnome-network-manager>

---

### Post by stupidkid on 2006-12-04
I never liked the gui manager. Since iwlist ath0 scan lists the networks, it means your card is working.

Try 

dhclient ath0 

to see if you can pick up an IP through DHCP. Normally the steps I use to connect are:

modprobe ath_pci
iwconfig ath0 essid <essid>
iwconfig ath0 key <wep key>
dhcpcd ath0 (or pump -i or dhclient).

---

### Post by dirkca on 2006-12-04
> **PilotJLR said:**
> Just to confirm... you disabled the wireless interface in the Networking tool , **THEN REBOOTED THE COMPUTER**, and it still is not in gnome-network-manager>

Yes. I even re-installed network manager...no difference. Just the wired connection shows up.

---

### Post by dirkca on 2006-12-04
jim@jim-laptop:~$ dhclient ath0 
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
can't create /var/lib/dhcp3/dhclient.leases: Permission denied
Can't create /var/run/dhclient.pid: Permission denied
drop_privileges: could not set group id: Operation not permitted

---

### Post by dirkca on 2006-12-04
I have been getting this message before. Any thoughts?

jim@jim-laptop:~$ iwconfig ath0 essid <home>
bash: syntax error near unexpected token `newline'
jim@jim-laptop:~$

---

### Post by dirkca on 2006-12-04
> **dirkca said:**
> Yes. I even re-installed network manager...no difference. Just the wired connection shows up.

Ok, I did what you suggested...twice...and now its showing....very weired. I am using a neighbors signal right now....having trouble with my own though.

Anyways, thank you very much for helping. I nade progress today.

Dirk

---

### Post by FrodoB on 2006-12-05
You need to use sudo:

sudo dhclient ath0

---

### Post by stupidkid on 2006-12-05
> **dirkca said:**
> I have been getting this message before. Any thoughts?

jim@jim-laptop:~$ iwconfig ath0 essid <home>
bash: syntax error near unexpected token `newline'
jim@jim-laptop:~$

Btw the <> should be omitted. so
sudo iwconfig ath0 essid home

---

### Post by LinuxInLibraries on 2006-12-06
This article may be of use: [http://ubuntuforums.org/showthread.php?t=293230](http://ubuntuforums.org/showthread.php?t=293230)

---

