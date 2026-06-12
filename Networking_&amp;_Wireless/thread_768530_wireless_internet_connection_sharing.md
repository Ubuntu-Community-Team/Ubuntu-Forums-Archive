---
title: "wireless internet connection sharing"
date: 2008-04-26
forum: Networking &amp; Wireless
---

### Post by sasham on 2008-04-26
Hi, I have a problem with setting up a wireless connection between a Ubuntu 7.04 desktop PC and MSI670 Debian Lenny laptop.
Desktop is connected to the internet through adsl router, and I want it to share internet connection with the laptop over the wireless connection.
 My computers can see different wireless networks but I cant manage to ping one from another no matter what combination I try. It seems to me that GUI that I use are not so useful ( I have wifi radar on both and network manager too). I think the solution is to use console but I am not very skilled in that. Can someone help me please? I checked out different how tos but failed, some detail I miss I am sure but cant find out what is wrong. 


ifconfig says:

ra0       Link encap:Ethernet  HWaddr 00:11:50:14:13:A6  
          inet addr:192.168.3.57  Bcast:192.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::211:50ff:fe14:13a6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:789445 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:31577800 (30.1 MiB)
          Interrupt:20 Base address:0x8000 

iwconfig says:
a0       RT2500 Wireless  ESSID:""  
          Mode:Managed  Frequency=2.412 GHz  Bit Rate:11 Mb/s   Tx-Power:0 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-120 dBm  Noise level:-212 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by dutchman72 on 2008-04-26
Since this is 2 pc's your trying to connect wireless, it has to be an ad-hoc network, not managed.

To change this by console its "sudo iwconfig a0 mode ad-hoc", the same thing will need to be done to the other pc, but change the "a0" for its wireless interface name.

---

### Post by sasham on 2008-04-26
I just succed for the first time to share the connection on the terrible "other" system, and oh what a stupid thing that was.I just had to disable sharing/share again the shared internet connection :(  how stupid...

But now I want really to do this in the linux enviroment. I need to learn how and why. Its not tolerable that I can do something in win and not on Gnu Linux :)

@dutchman72 
Yes I tried to make them both ad hoc with wi fi radar and it didnt work. How can I do it by using console? Another question , I see the settings change back to original settings whenever I restart the computer.

---

### Post by sasham on 2008-04-26
posted twice the same message, sorry

---

### Post by sasham on 2008-04-26
I would also prefer to have a static IP adress (because my system is dual boot so I dont have to change settings when I reboot in the other system).
I have found this manual:

[http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)

WPA with Ra Based Chipsets

Ra cards do not require the wpa_supplicant package to use WPA. Here is how to connect from the command line with these cards:
References: [http://ubuntuforums.org/showthread.p...=serial+monkey](http://ubuntuforums.org/showthread.p...=serial+monkey), [http://rt2x00.serialmonkey.com/wiki/...owto#Using_WPA](http://rt2x00.serialmonkey.com/wiki/...owto#Using_WPA)

WPA(1)
Code:

 sudo ifconfig <interface> down
sudo dhclient -r <interface>
sudo ifconfig <interface> up
sudo iwconfig <inteface> essid "ESSID_IN_QUOTES"
sudo iwpriv <interface> set AuthMode=WPAPSK
sudo iwpriv <interface> set EncrypType=TKIP
sudo iwpriv <interface> set WPAPSK="YOUR_WPA_PSK_KEY"
sudo dhclient <interface>   



But I see it uses the dhcp, also I dont understand what other commands mean, and I should understand or otherwise I wont be able to acjust my debian laptop to the same settings.

---

