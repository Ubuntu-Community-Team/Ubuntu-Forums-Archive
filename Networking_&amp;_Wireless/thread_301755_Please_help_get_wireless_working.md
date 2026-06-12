---
title: "Please help get wireless working"
date: 2006-11-17
forum: Networking &amp; Wireless
---

### Post by Elvish Legion on 2006-11-17
jduvall@jduvall-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ath0      IEEE 802.11b  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   
          Encryption key:0606-1712-7847   Security mode:restricted
          Power Management:off
          Link Quality:100/100  Signal level:-94 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

My card is detected properly, just, neither of the network managers I've dried )gnome network manager and ubuntu's default) seem to let me configure it properly...

Any help?

---

### Post by rvickers on 2006-11-17
This troubleshooting how-too helped me.

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

Also, what worked for me:
1 - sudo ifconfig eth1 down
2 - sudo nano /etc/network/interfaces
3 - wipe out everything except
     auto lo
     iface lo inet loopback
4 - configure your wireless through System->Administration->Networking

Good luck......

---

### Post by FrodoB on 2006-11-17
Try this test script to see where you stand. For testing turn off all security in the access point router.

Cut the following script and paste it into the Text Editor and save it as test.sh and then use chmod, so the process will be:

$ chmod 755 test.sh


#!/bin/sh
/sbin/iwconfig ath0 essid "My_Essid"
/sbin/iwconfig ath0 mode "Managed"
#/sbin/iwconfig ath0 rate 11M auto 
#/sbin/iwconfig ath0 key "XXXXXXXXXXXXXXXXXXXXXXX"
#/sbin/iwconfig ath0 key "s:XXXXXXXXXXXXX"
#/sbin/dhclient ath0 


You probably already know, the "#" is the comment character for shell scripts. So all you need to try at first is to connect to your Access Point in managed mode. 

With the script in your current directory just type:

$ ./test.sh

You should see nothing happen until you give an iwconfig command and it hopefully shows you access point name and the MAC identifier of your ap.

If you get that far you could uncomment the dhclient line and let it try to get an address. Please give us the output of iwconfig and iwlist after you have run the script. Once this works you will be able to make the final configuration with confidence.

---

