---
title: "8189 Realtek Wireless on Ubuntu 64-bit Hardy Heron"
date: 2008-07-16
forum: Networking &amp; Wireless
---

### Post by athianos on 2008-07-16
Hello!


I have a Packard Bell Easynote SJ-51-B-088 Laptop

I have installed Ubuntu studio with 8.04 Hardy Heron 64-bit kernal 2.6.24-19-rt

I have successfully installed my webcam [http://ubuntuforums.org/showthread.php?p=5390696#post5390696]("http://ubuntuforums.org/showthread.php?p=5390696#post5390696")

The Packard Bell Easynote SJ-51-B-088 comes with an inbuilt Realtek wireless card - or so it seems- 
lsusb returns:
> 
Bus 004 Device 004: ID 0846:6a00 NetGear, Inc. WG111 WiFi (v2)
Bus 004 Device 003: ID 5986:0130 Bison 
Bus 004 Device 002: ID 0bda:8189 Realtek Semiconductor Corp. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 046d:c51b Logitech, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

iwconfig returns
> 
lo        no wireless extensions.

eth0      no wireless extensions.

wlan1     802.11b/g  Mode:Managed  Access Point: Not-Associated   
          Bit Rate:11 Mb/s   
          Retry:on   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

wlan2     802.11b/g  Mode:Managed  Access Point: Not-Associated   
          Bit Rate:11 Mb/s   
          Retry:on   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


The sticker on the laptop tells me it has ATHEROS wireless.

I have scoured the forums and tried a number of options including ndiswrapper, rtl8187 drivers, rtl8187b drivers with cuervo's patch - the works. My netgear wg111v2 wifi has worked for a short time before crashing. 

I have also tried network manager and have replaced it now with wicd - which seemed to sort out the WEP problems.

I'm concerned that my attempts at different driver options may have caused some confusion behind the GUI!   

I am now without wireless and without a clue!

I would like help to:

Tidy any driver confusion in the kernal.
Install the appropriate drivers for the inbuilt wireless (ideal)
Get the wg111v2 dongle working in a stable way. (second best)

Many thanks for your time!

A

---

### Post by athianos on 2008-07-17
[http://sudan.ubuntuforums.com/showthread.php?t=838706](http://sudan.ubuntuforums.com/showthread.php?t=838706)

has helped me to reach this point.
:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan1     802.11b/g  Mode:Managed  Channel=6  
          Access Point: Not-Associated   Bit Rate:11 Mb/s   
          Retry:on   Fragment thr:off
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

:~$ sudo iwlist wlan1 scanning
wlan1     Scan completed :
          Cell 01 - Address: 00:16:CF:31:91:1D
                    ESSID:"Livebox-CBE8"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:1
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54 
                    Quality:16  Signal level:0  Noise level:78
                    Extra: Last beacon: 380ms ago

Connection established

---

### Post by athianos on 2008-07-17
the laptop sees the router but I cannot connect. 

Any help, much appreciated!

---

### Post by athianos on 2008-07-17
iwlist wlan1 scanning
wlan1     Scan completed :
          Cell 01 - Address: 00:16:CF:31:91:1D
                    ESSID:"Livebox-CBE8"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:1
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54 
                    Quality:16  Signal level:0  Noise level:91
                    Extra: Last beacon: 474ms ago
          Cell 02 - Address: 00:90:96:F3:0D:A5
                    ESSID:"BTVOYAGER2100-A5"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:1
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54 
                    Quality:15  Signal level:0  Noise level:32
                    Extra: Last beacon: 582ms ago

---

### Post by athianos on 2008-07-18
removed ndiswrapper
returned all the files I had changed to back how they were.
removed what drivers I could find. I honestly don't know what driver is running now. 
When I rebooted and typed

sudo ifconfig wlan0 up

iwconfig returned that I did indeed have wireless. I was able to connect to my livebox only by deactivating the security key through this [website:]("http://configuration.adsl/")
login admin
password admin

configuration>advanced>wireless>no security

Network manager was then able to connect to the livebox.
Network manager is also able to see my USB dongle WG111v2 and connect to the internet through this. 


When I rebooted, wireless disappeared. I searched some forums and found I needed to do this:

sudo gedit /etc/network/interfaces
> 
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface

auto wlan0


Inserting auto wlan0 in this file automatically turns on the wireless card at boot. I have had no more problems. The connection is steady.

I would like to see Network Manager sort out the WEP problems. I feel a little open as a network now!

Still, WIRELESS connection with stable access achieved on 64-bit!

I hope this helps other people find some clarity on what needs to be done. Good Luck!

---

### Post by athianos on 2008-07-26
SOLVED! 

I installed this little package in synaptic and I can use WEP without a problem. 

Network manager even shows me an accurate signal bar!

hostapd

I found the solution here.

Thanks gstamp!:guitar:

[http://ubuntuforums.org/showthread.php?t=75017]("http://ubuntuforums.org/showthread.php?t=75017")

---

