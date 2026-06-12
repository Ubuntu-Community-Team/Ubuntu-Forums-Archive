---
title: "essid not surviving reboot"
date: 2007-07-04
forum: Networking &amp; Wireless
---

### Post by Joban on 2007-07-04
Each time i boot, i have to reconfigure my wireless slightly by typing in a terminal:
> 
sudo iwconfig wlan0 essid=myid

to get my wireless to work. which is annoying. If i don't, i get no internet, and iwconfig reads thus:
[quote="iwconfig"]
 Auto  ESSID:"any/no"  
          Mode:Managed  Frequency:2.472 GHz  Access Point: 00:11:50:6A:02:F5   
          Bit Rate=108 Mb/s   
          Power Management:off
          Link Quality:46/100  Signal level:-66 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
[/quote]

My /etc/network/interfaces reads thus:
[quote="/etc/network/interfaces"]
auto lo
iface lo inet loopback


iface eth0 inet static
address 192.168.0.2
netmask 255.255.255.0
gateway 192.168.0.1




auto wlan0
iface wlan0 inet static
address 192.168.2.5
netmask 255.255.255.0
gateway 192.168.2.1
wireless-essid myid

auto eth0
[/quote]

any ideas how i can avoid having to use the terminal everytime i boot?

---

