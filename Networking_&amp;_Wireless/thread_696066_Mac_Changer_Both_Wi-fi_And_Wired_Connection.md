---
title: "Mac Changer Both Wi-fi And Wired Connection"
date: 2008-02-13
forum: Networking &amp; Wireless
---

### Post by ay99 on 2008-02-13
:KS1.WI-FI CONNECTION
write  sudo  apt-get install macchanger at yr terminal.
later write  ifconfig  to see yr MAC number something like this( eth1  00:ac:12:05:c1:06)
in order to change this MAC number to anyone follow those steps:
-Disable WI-FI connection in yr  Network Manager by this command:
sudo /etc/init.d/networkingstop
-change yr MAC by this command:
sudo macchanger -m 00:01:05:ab:03:55 eth1   (P.S=eth1 can be wlan1 at yr ubuntu and written MAC number here is an example ,you can write any numbers...BUT  KEEP IN MIND DO NOT USE BEYOND A,B,C,D letters BECAUSE ETHERNET manufacturer do not  USE OTHER LETTERS.)
-enable WI-FI in Network Manager by this command:
sudo /etc/init.d/networkingstart
-USE AND ENJOY NEW MAC ADDRESS....
IMPORTANT:Whenever you open yr pc,You must FOLLOW ABOVE PRESCRIPTION.:guitar:
:confused:2.WIRED CONNECTION
DID NOT WORK ABOVE METHOD AT MY DESKTOP.
 ADVISES REGARDING WIRED CONNECTION ARE WELCOME..

---

