---
title: "Wireless on Ubuntu 8.04 Hardy"
date: 2008-10-05
forum: Networking &amp; Wireless
---

### Post by MattTeddy on 2008-10-05
Hi all, I'm new to the world of linux here and I am interested in getting to know this OS alot better. I installed Ubuntu two days ago and I am having difficulties setting up the wireless for my laptop.

I have been reading through alot of threads to no avail. I recently stumbled upon wieman01's thread ([http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539)) and it looks like it will work...

Although I'm having difficulty at the first step! Here is what I get when I type "iwconfig" into the terminal:
> teddy@teddy-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


If I am correct, my network should be showing up there. I am using WPA2 and a hidden SSID.

Any help greatly appreciated.
Matt

---

### Post by nixscripter on 2008-10-06
That means your card -- wlan0 -- **is** showing up. Proceed with the guide.

---

