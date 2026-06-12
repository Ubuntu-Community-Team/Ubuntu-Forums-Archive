---
title: "wireless config problem"
date: 2009-07-29
forum: New to Ubuntu
---

### Post by Duke Togo on 2009-07-29
hi all trying to get my wired connectioin up and wirless
follow ing instruction fron here 
[https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo)
AI get the following:
what seems to be the issue here?
thanks

richard@richard-laptop:~$ lspci | grep Network
richard@richard-laptop:~$ 
richard@richard-laptop:~$ lspci | grep Network
richard@richard-laptop:~$  lspci | grep Network
richard@richard-laptop:~$ iwconfig
lo        no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-92 dBm  Noise level=-92 dBm
          Rx invalid nwid:22055  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

richard@richard-laptop:~$ sudo ifconfig wlan0 up
wlan0: ERROR while getting interface flags: No such device
richard@richard-laptop:~$ iwconfig
lo        no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:23011  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

richard@richard-laptop:~$

---

### Post by daimaru on 2009-07-30
ath0 should be your wlan card probably like mine its an atheros card (which rule  :) )
could you show output of 
```
lshw -c network
```
please. 

This is how i would get my network up manually ( 192.168.178.1 is my router adress .2 is one of my computers ) 
```
sudo ifconfig ath0 192.168.178.2 up
sudo ifconfig netmask 255.255.255.0
sudo route add default gw 192.168.178.1

```

---

### Post by Katalog on 2009-07-30
Atheros is a pain in the %$# on Ubuntu. Try using the solution posted in this thread:

[http://ubuntuforums.org/showthread.php?t=1191178](http://ubuntuforums.org/showthread.php?t=1191178)

Worked for me. As long as you can find the appropriate Widows drivers for your wireless card, you chould be able to sort it out.

---

### Post by mapes12 on 2009-07-31
If your wifi is Atheros you may need madwifi support to get it working:

[https://help.ubuntu.com/community/WifiDocs/Driver/Madwifi](https://help.ubuntu.com/community/WifiDocs/Driver/Madwifi)

[http://madwifi-project.org/](http://madwifi-project.org/)

A straight ```
lspci
```should show the model number.

---

### Post by lisati on 2009-07-31
With respect to other contributers, *some* Atheros is a pain - not everybody's experience is the same. My old laptop (since donated to a nephew) has an Atheros card which worked "out of the box", and I'm aware of other threads on the forums which deal with assorted Atheros cards which seem to be problematical.

---

### Post by tarps87 on 2009-07-31
> **Duke Togo said:**
> 
richard@richard-laptop:~$ iwconfig
lo        no wireless extensions.

wifi0     no wireless extensions.

**ath0**      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-92 dBm  Noise level=-92 dBm
          Rx invalid nwid:22055  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

richard@richard-laptop:~$ sudo ifconfig **wlan0** up
wlan0: ERROR while getting interface flags: No such device


Should be:
```
sudo ifconfig **ath0** up
```

> **lisati said:**
> With respect to other contributers, *some* Atheros is a pain - not everybody's experience is the same. My old laptop (since donated to a nephew) has an Atheros card which worked "out of the box", and I'm aware of other threads on the forums which deal with assorted Atheros cards which seem to be problematical.

Just what I was about to say. Well apart from instead the old laptop bit, in using one of the newer Atheros cards which worked out of the box in Ubuntu

---

