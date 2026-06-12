---
title: "Wireless USB installed and recognised, doesn't find the router"
date: 2006-12-04
forum: Networking &amp; Wireless
---

### Post by OttifantSir on 2006-12-04
I have just installed my Philips SNU5600 USB dongle. Now I try to connect to the the Net through the router SNB5600.

I find my neighbour's router/network, but not mine. I took the IP, gateway and network mask off another computer (that has used this dongle and it worked) but no go on this computer.

I have pressed the reset button for about half a minute (the manual says twenty to do a full restore)

The ESSID is now: philips
IP adress: 192.168.1.100
Network mask: 255.255.255.0
Gateway: 192.168.1.2

Including the driver file I used. (Had to change from .inf to .txt to be allowed to upload it.) Only change I made to it, are the commentations (##) on the description lines. (They now read ##; as ; was there before)

Any ideas on how to solve this is welcome. Tiresome to connect the USB cable from my cable modem (not router) to the laptop all the time. (Why the USB-cable? Haven't got a network card. Too old a machine to have it)

---

### Post by OttifantSir on 2006-12-04
What info I have at the moment.

Ask for more if needed.


iwconfig
lo        no wireless extensions.

sit0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"ottinett"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:12:BF:33:38:33   
          Bit Rate:54 Mb/s   Tx-Power:-2147483648 dBm   Sensitivity=0/3  
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0/100  Signal level:-42 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

lsusb
Bus 001 Device 004: ID 0471:1236 Philips 
Bus 001 Device 001: ID 0000:0000

---

### Post by OttifantSir on 2006-12-14
Just making a reply to bump it up to the top to see if anyone can help with this problem, or may ask me some questions that I can use to get back on track.

---

### Post by FrodoB on 2006-12-14
This appears to be a zd1211b:

[http://zd1211.ath.cx/](http://zd1211.ath.cx/)

Use this instruction for another zd1211b device and it should work:

[https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_4000_%28ZyDas_zd1211b_driver%29?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_4000_%28ZyDas_zd1211b_driver%29?highlight=%28WifiDocs%2FDevice%29)

---

### Post by OttifantSir on 2006-12-14
Too late in the day to check this out now, but according to what I have read on the first link, it seems this approach will do the trick for me. Will post back the results tomorrow, or ask another question. I think the question will be: How do I disable the already-installed driver?

I have just skimmed the installation HOWTO, so it probably says so there. Just have to read it more carefully first. We'll see tomorrow.

Thank you FrodoB.

---

### Post by FrodoB on 2006-12-14
Blacklisting the existing driver is covered in the howto.

---

