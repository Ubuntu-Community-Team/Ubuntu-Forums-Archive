---
title: "wireless network is not connecting"
date: 2008-06-09
forum: Networking &amp; Wireless
---

### Post by LPi on 2008-06-09
hello everybody ...
I try to connect to the wireless network that i subscribe to , but unfortunately nothing happens .
the network is unencrypted ,using static IP address , and the authorizing is through the mac address of the wireless adapter ,wireless access point , etc . 
I tried to change the mac address to another to see if the admin. block mine , but the same .
when I use windows its working fine .
I configure the connection manually , using the commands from this thread : [http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)

I hope I can find the solution .

---

### Post by rlzyoner on 2008-06-09
What equipment are you using ?
Builtin wireless or an external wireless card.

Also, which version of ubuntu are you using, gutsy, hardy etc.

---

### Post by LPi on 2008-06-09
I'm using external adapters:
senao Engenius atheros 5523 arapter ( i installed it manually ) ,
and reltek ( or whatever) RTL8187 wireless lan adapter which is automatically installed .
the version of ubuntu is 7.10 gutsy gibbon .

---

### Post by rlzyoner on 2008-06-09
Ok so try this

iwconfig (to get the name of your wireless adaptor)
now try
sudo ifconfig ath0 up (this enables adaptor ath0 [change this if necessary])

Now run iwlist scanning (This will scan for available AP's - wireless access points)

OR alternatively run 

nm-applet and use the network manager gui to select a network to connect to.

---

### Post by LPi on 2008-06-09
i can see the network , but i can't connect to it :( 
thank you for your helping

---

### Post by LPi on 2008-06-09
i can see the network , but i can't connect to it :( 
thank you for your helping

---

### Post by rlzyoner on 2008-06-09
Is the network encrypted (wep, wpa) ?
Sometimes its handiest to configure the connection manually rather than rely on network manager to do it.
If the network is WEP encrypted.
Do the following from a terminal

sudo ifconfig ath0 down
sudo dhclient -r ath0
sudo ifconfig ath0 up
sudo iwconfig ath0 essid "PUT_YOUR_ESSID_HERE"
sudo iwconfig ath0 key PUT_THE_ENCRYPTION_KEY_HERE
sudo iwconfig ath0 key open  
sudo iwconfig ath0 mode Managed
sudo dhclient ath0

*Note that the essid is placed within the inverted commas*

---

### Post by LPi on 2008-06-09
thenetwork is unencrypted ( unsecured ) .
the security key is off , the only way to authorizing the connection is through the Mac address

---

### Post by rlzyoner on 2008-06-09
Right, my bad 

Type this instead

sudo ifconfig ath0 down
sudo dhclient -r ath0
sudo ifconfig ath0 up
sudo iwconfig ath0 essid "PUT_YOUR_ESSID_HERE"
sudo iwconfig ath0 mode Managed
sudo dhclient ath0

This should work for an unencrypted network.

Also, run iwconfig and confirm that the MAC Addy is exactly as it should be (just to be sure)

---

### Post by LPi on 2008-06-09
ok , i'll try 
thank you for your helping my friend

---

### Post by rlzyoner on 2008-06-09
No bother brother,

---

### Post by Jim BruceJ8PM9 on 2008-06-09
I am using Ubuntu 8.04 on an Acer Aspire 3680 laptop.  When on 7.10 I had no problems with the wireless disconnecting.

Now I have occasional disconnects when I am asked to re-enter my WEP key.  I do that and that usually solves the problem.  However if my wife or daughter log on they almost always start from disconnect, and I have trouble connecting them unless I logon with my admin logon and password.

We have a Dell laptop running under windows, it doesn't have the disconnect problem. 

I have a "RALINK WIRELESS G PCMCIA WIFI CARD VISTA/LINUX/MAC OS X"
wireless card.  


 ifconfig gives me:
wlan0     Link encap:Ethernet  HWaddr 00:0f:ea:85:d0:03  
          inet addr:192.168.1.69  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:eaff:fe85:d003/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:38127 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23836 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:17233026 (16.4 MB)  TX bytes:5783268 (5.5 MB)

iwconfig gives me:
____________
jim@jim-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

eth1      IEEE 802.11g  ESSID:""  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

wmaster1  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"a8a00563"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1A:C4:ED:FD:01   
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality=57/100  Signal level=-75 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

jim@jim-laptop:~$ 

__________________________

When I get asked for the wep key I enter it and use
64bit openwep key hex.


I was having problems with the card occasionally running slow.  I found out how to use:

"iwconfig devX rate 11M"

That solves the problem  

Jim

---

### Post by LPi on 2008-06-09
rlzyoner : 
i tried what you did post , nothing new :(

Jim :
thank you for your coment , its even not connecting :(

I'll try to use ubuntu to connect from the other pc ( using D-link G520 Wireless card ) and see if the same problem or not .

thank you again for your helping my friends.

---

