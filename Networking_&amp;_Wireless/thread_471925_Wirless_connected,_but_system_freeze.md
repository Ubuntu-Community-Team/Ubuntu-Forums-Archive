---
title: "Wirless connected, but system freeze"
date: 2007-06-12
forum: Networking &amp; Wireless
---

### Post by Kesty on 2007-06-12
Hello,

I'm new to ubuntu and linux.

I was trying to install ubuntu 7.04 yesterday for the first time and I had some problems.
I was able to solve most of the problems but the wirless connection one.

The wirless card I use came with the  motherboard Asus (88W8310 and 88W8000G).

(I should have installed also a Lynksys-N WMP300N, but I had problem with that card also in windows, and with lspci the only 802.11g that is shown is  the asus one)

The card wasn't working. And  after some google, i've tryed to use ndiswrapper

I've installed ndiswrapper 1.38 (the .deb files I've found in the repository), and the WinXP drivers in the CD (NDISwrapper list them as ok).

Following some instructions I've found, i've blacklisted bcm43xx

Then I've installed the drivers.

```

ndiswrapper -l 
mrv8ka51 : driver installed
             device (11AB:1FA7) present

```

I've used the command "sudo modprobe ndiswrapper".

Iwconfig seem fine and iwlist wlan0 scan show all the wirless connection.

Then with network manager I conntected to the network.

He ask me for the WEP key (64 bit Hex), and then he ask me "Enter password for default keyring to unlock" and I enter my WEP passkey.

Everything seem fine and Network Menager say is connected.

But when I try to use Internet (with Firfox) or just after a little bit the system e freeze.

I'm sorry for the bad english, I hope that you can understand my situation.

Tell me if you need more informations

---

### Post by Kesty on 2007-06-12
While the network is connected I've tryed to ping 192.168.1.1 and it works

I've also tryed to ping other websites (google, ubuntu, ecc..) and everything works fine.

So the connection is there. The problem is that after 4 or 5 minutes doing only ping or just after trying to open firefox or another application the system freeze.

Could be a Driver problem ?
Or maybe I should try to connect with somethin dgifferent than Network Manager ?

---

### Post by dardack on 2007-06-12
Ok couple things maybe.  Before you connect, disable the wireless in network-manager, then open firefox.  Does the system still freeze?

If not try the updated winxp drivers from the manufactureers website (i had to use those for my WUSB11 over the CD ones).  If that still doesn't work you can uninstall Network-manager and connect manually (i've personally had issues with NM, not freezing but my connection droppping all the time, once i uninstalled NM and connected manually everything now works).

I'm not an expert, just giving some ideas that have worked for me.

---

### Post by Kesty on 2007-06-12
Yes Firefox works if I'm not connected.

But is not just firefox, almost every application i try to run while connected freeze the system.

I've tryd to uninstall Network Menager to try and install wicd, but I think I've done somthing wrong :(

I've unistalled network menager with the Add/remove application, but then if I try to install the wicd.deb it say it can't be installed because network menager is already installed. 

If I llok the applications it seem not installed. How can I completly uninstall it ?
Edit: I uninstalled with apt-get remove, I will try with wicd now.


or any help on a guide to connect manually ?

This is my firs linux installation, so I'm sorry if I'll ask all this newbie questions, or I do stupid mistakes.. ;)

---

### Post by dardack on 2007-06-12
yea i'm not an expert myself.  Ok to uninstall i went to System->Administration->Synaptec (something) i'm at work and not at home so can't remember exact wording.  Let that come up click search and type in network-manager.  Right click it and click remove complete or whatever it is.  Than for mnaul install open a terminal.  (um application-> first chose->terminal)

Than in terminal type these out (if they dont' work post your results, also is your router using any security like WEP, and is it broadcasting your SSID?)

sudo iwconfig (this should give you the device that is wireless, like wlan0, ath0, just replace wlan0 in next commands with your device)
sudo iwlist wlan0 scan (hopefully if your router is broadcasting it will list the ESSID of your router)
sudo killall dhclient
sudo iwconfig wlan0 essid "your ESSID without quotes" mode managed enc off
(if your using WEP than do this: sudo iwconfig wlan0 key "your WEP key without quotes"
sudo dhclient -d wlan0

Ok post those results if that doesn't work for you.

---

### Post by Kesty on 2007-06-12
I've tryed what you sayd but the system freeze and I had to cold reboot for the n time.

Same probem as before, network works (I was able to ping and everything seemed fine), but after a bit, or trying to open an application it freeze-

I was able to copy paste everything in a txt file (not the last part after the dhclient -d wlan0, but I've copied by hand) and I'll upload everything here.
```
enrico@enrico-desktop:~$ sudo iwconfig
Password:
lo        no wireless extensions.

eth0      no wireless extensions.

enrico@enrico-desktop:~$ sudo modprobe ndiswrapper
enrico@enrico-desktop:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b  ESSID:"Linksys_AP"  
          Mode:Managed  Frequency:2.432 GHz  Access Point: 00:18:39:90:11:DC   
          Bit Rate=54 Mb/s   Sensitivity=-200 dBm  
          RTS thr=2346 B   Fragment thr=2346 B   
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

enrico@enrico-desktop:~$ sudo iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:18:39:90:11:DC
                    ESSID:"Linksys_AP"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.432 GHz (Channel 5)
                    Quality:18/100  Signal level:-84 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 02 - Address: 00:18:39:23:EB:84
                    ESSID:"Linksys_N"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.442 GHz (Channel 7)
                    Quality:17/100  Signal level:-85 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

enrico@enrico-desktop:~$ sudo killall dhclient
dhclient: no process killed
enrico@enrico-desktop:~$ sudo iwconfig wlan0 essid Linksys_N mode managed enc off
enrico@enrico-desktop:~$ sudo iwconfig wlan0 key ########3#
enrico@enrico-desktop:~$ sudo dhclient -d wlan0
Internet Systems Consortium DHCP Client 3.0.4
Copyright 2004-2006 Internet System Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:13:d4:11:14:fd
Sending on LPF/wlan0/00:13:d4:11:14:fd
Sending on Socket/fallback
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.12 -- renewal in 33651 seconds.

```

---

### Post by dardack on 2007-06-12
Hmmm i'm at a lose.  Wish i could help you out, maybe someone with more knowledge can.

---

### Post by Kesty on 2007-06-13
Thanks for your help, it didn't work but I appreciate the kindness.

I was trying to use the latest ndiswrapper version, but I couldn't get to compile the source right.

Since I really don't want to return to windows I will try to get a supported ubuntu wirless card from[ this list ]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported") and hope that everything will work fine, since other than the wirless problem everything else seemed to work fine.

Any advice to give me on what card to buy will be appreciated.

---

### Post by aberry5555 on 2007-06-13
I have the same problem as you and Ive compiled the new ndiswrapper myself; simply doesnt work at all unfortunately... What I want to try to find is the older driver as I seemed to remember that worked on edgy. Do you happen to have the original driver CD, if so try that driver and PLEASE let me know so I can somehow get it off you too as I've lost mine and cant find the older driver anywhere :S
<-- EDIT --> 

I've found the older driver on another post, here [http://ubuntuforums.org/showthread.php?t=288341&highlight=mrv8ka51](http://ubuntuforums.org/showthread.php?t=288341&highlight=mrv8ka51) try downloading that one and using it with ndiswrapper it might solve the problem

---

### Post by Kesty on 2007-06-13
I have the original CD and I've tryed with both the driver downloaded from the asus website  and the original CD drivers.

I will try with the driver you linked tonight, since now I am at work and i can't test it.

---

