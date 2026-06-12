---
title: "went into monitor mode on bcm43xx, went apeshit"
date: 2007-03-25
forum: Networking &amp; Wireless
---

### Post by bedake on 2007-03-25
I went into monitor mode with my wireless card in the terminal with this command:

$ sudo iwconfig eth1 mode monitor

Now, my card won't connect to anything. The network manager attempts to join the network and times out after a while.  I've tried rebooting, powering down, booting into windows, and even removing the battery. Still nothing. 

I also tried going into managed mode, auto mode, and master mode:

$ sudo iwconfig eth1 mode managed
$ sudo iwconfig eth1 mode auto
$ sudo iwconfig eth1 mode master

Regardless, my network card still behaves the same.

My iwconfig readout is as follows:

eth1      IEEE 802.11b/g  ESSID:"belkin54g"  Nickname:"Broadcom 4318"
          Mode:Managed  Frequency=2.462 GHz  Access Point: 00:11:50:33:04:EF   
          Bit Rate=1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Notice it says I'm connected to "belkin54g" with a 1Mb/s bit rate, but I don't get any traffic and I can't browse anything. Please help!

---

### Post by bedake on 2007-03-25
Ok I disabled network manager and then went back into monitor mode then back into managed mode.  Now iwconfig states:  
bedake@bedake-laptop:~$ iwconfig eth1
eth1      IEEE 802.11b/g  ESSID:"belkin54g"  Nickname:"Broadcom 4318"
          Mode:Managed  Frequency=2.462 GHz  Access Point: 00:11:50:33:04:EF   
          Bit Rate=11 Mb/s   Tx-Power=18 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=41/100  Signal level=-70 dBm  Noise level=-72 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


So it says im connected, network manager says im still not, but the same thing is still happening.









I just loaded back into windows and its the wireless internet will work but the wireless network manager will say that i am disconnected, so I am really at a loss for what happened.

---

### Post by bedake on 2007-03-26
Sorry for the triple post


Alright I just completely reinstalled Ubuntu, and reinstalled the bcm43xx drivers according to the wiki entry here: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Edgy](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Edgy)


and STILL my wireless is no longer working.  So I have a question now, when following that guide does it change the firmware on the wireless card?  After a complete reinstallation of ubuntu without a fix this leaves me worried that I may have permanetly screwed my wireless card all by going into monitor mode.

Im feeling a bit desperate now especially since the wireless in windows is also acting strangely.






EDIT:
Alright, I got wireless working via the system>>administration>>networking
but still network manager seems to not want to cooperate,

---

