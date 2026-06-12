---
title: "cannot find my wireless router after upgrading to 7.10"
date: 2008-02-26
forum: Networking &amp; Wireless
---

### Post by madelman on 2008-02-26
When I was running 7.04 I did not have any problems with my wireless connection. Now after upgraded to 7.10 ubuntu finds all the wireless networks close to my home but mine. I have to type manually the network name and then it tries to find the connection, sometimes works some other times does not work, so I have to restart my router. I have checked with different devices such as iPods and other laptops connecting wireless and they work when my laptop cannot. I have a ethernet connection from other computer and that works when the wireless cannot be found. I am getting sick and tired to do this everytime the wireless is not found. 

what really bothers me is that 7.04 was working fine and now 7.10 really have a lot of problems. I upgraded several months ago and I thought there was something done with those upgrades that really screwed computers and it looks like nothing has been done to improve the upgrade.

---

### Post by pytheas22 on 2008-02-26
Upgrading can cause a lot of strange problems, mostly because the upgrade process doesn't get tested exhaustively.  Doing a clean install of 7.10 should be safer (or, at this point, wait a month and a half for 8.04).

If you want to try to fix your existing system instead of doing a new install, post the output of

```
iwlist INTERFACE scan
```

where INTERFACE = the name of your wireless interface, which is probably something like eth1, wlan0, ath0 or so on depending on your type of wireless card.

and

```
iwconfig
```

and maybe we can figure out what's wrong.

Also, are you using Network Manager to try to connect?

---

### Post by madelman on 2008-02-27
$ iwconfig
lo        no wireless extensions.


eth1      no wireless extensions.


eth0      IEEE 802.11g  ESSID:"myNet"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0C:41:71:89:A2   
          Bit Rate=11 Mb/s   Tx-Power:25 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:90/100  Signal level:-38 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



$  iwlist eth0 scan
eth0      Scan completed :
          Cell 01 - Address: 00:14:BF:72:53:81
                    ESSID:"KaviJanu"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:56/100  Signal level:-60 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 02 - Address: 00:1C:10:11:07:BD
                    ESSID:"RATPACK"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:45/100  Signal level:-67 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 03 - Address: 00:13:46:46:E6:C6
                    ESSID:"MASS"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:37/100  Signal level:-72 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 04 - Address: 00:0C:41:71:89:A2
                    ESSID:"myNet"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:87/100  Signal level:-40 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0


"Also, are you using Network Manager to try to connect?"

Yes: nm-applet 0.6.5

---

### Post by pytheas22 on 2008-02-28
> Cell 04 - Address: 00:0C:41:71:89:A2
ESSID:"myNet"
Protocol:IEEE 802.11b
Mode:Managed
Frequency:2.437 GHz (Channel 6)
Quality:87/100 Signal level:-40 dBm Noise level:-96 dBm
Encryption keyn
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
Extra:bcn_int=100
Extra:atim=0

It looks like your network is named myNet, right?  If so, the piece above indicates that your wireless card is seeing it when scanning--so it must just be that Network Manager is failing to show it for some reason.

Network Manager is notoriously buggy.  You could try purging it and reinstalling, but I can't guarantee that that would work.  A simpler option might be to try using wicd instead--you can install it from [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/) (I think that it will make you uninstall Network Manager first).  Try wicd and let us know if that works...even if you want to go back to NM later, it would at least be helpful to know if you are able to get a connection using wicd, which would further isolate the source of the problem.

---

### Post by madelman on 2008-03-14
Well I uninstalled and reinstalled  Network Manager and did not work, so I  installed Wicd. It was easy to install and configure then I had some issues to connect but I had to add a line to :

sudo vi /opt/wicd/encryption/templates/wep 

name = WEP (Hex)
author = Adam Blackburn
version = 1
require key *Key
-----
network={
       ssid="$_ESSID"
       scan_ssid=$_SCAN
       key_mgmt=NONEndi
        auth_alg=SHARED <<---- This one
       wep_key0=$_KEY
       wep_tx_keyidx=0
       priority=5
}


and that made the trick, I rebooted and Wicd connected without problems. Set it up to be automatically connected to my network using ndiswrapper in the WPA supplicatn dirver field (because the kind of wireless card)  and it finds the network without problems and connects normally. I sometimes feel like the connection is slower but I need more testing, so far it looks good and no need to type keyrings.

 I have not checked something with Wicd  that was happening with Network Manager lately. I was locking the screen and trying to work again on the computer I could see that the NM was searching for my wireless network so I had to tell it manually ehich netwok and kept asking me the passphrase several times and could not connect. Anyway it is working now and Wicd shows better reception of the signal than Network Manager.

 thank you for all your help. 


cheers.

---

