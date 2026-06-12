---
title: "Properly formed  /etc/network/interfaces??"
date: 2008-01-06
forum: Networking &amp; Wireless
---

### Post by can564 on 2008-01-06
I am not sure I have properly formed my /etc/network/interfaces file

I am setting up a Belkin F5D7050 ver 3000 - USB ID 050d:705a - Ralink rt73 Driver Installation from the Ubuntu Guide here [https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_(Ralink_rt73_driver](https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_(Ralink_rt73_driver))

On my Ubuntu 7.10 2.6.22-14-generic kernel.All other modules besides RT73 are blacklisted and the Ralink RT73 drivers RT73_Linux_STA_Drv1.0.4.0 compiled without errors and rtmp_def.h included my usb device {USB_DEVICE(0x050d,0x705a)}, /* Belkin F5D7050 ver 3000 */      \

In the guide it says to add to your  /etc/network/interfaces file something like this

[COLOR="SeaGreen"]# rt73 wireless network device using DHCP
iface rausb0 inet dhcp
pre-up ifconfig rausb0 up
wireless-essid MY_ESSID
# wireless-key XXXXXXXXXXXXXXXXXXXXXXXXXX       # This line for hexidecimal keys
# wireless-key s:XXXXXXXXXXXXX                  # This line for ASCII (string) keys
auto rausb0
[/COLOR]

I am setup up Auto DHCP and my access point has a essid called 802_11g with no security channel 1. I changed only the wireless-essid line to match my access point and left both key lines commented out because I am not using any security.It looks like this

[COLOR="Red"]auto lo
iface lo inet loopback

# rt73 wireless network device using DHCP
iface rausb0 inet dhcp
pre-up ifconfig rausb0 up
wireless-essid 802_11g
# wireless-key XXXXXXXXXXXXXXXXXXXXXXXXXX       # This line for hexidecimal keys
# wireless-key s:XXXXXXXXXXXXX                  # This line for ASCII (string) keys
auto rausb0[/COLOR]

My RT73 module is loading.my Belkin USB adapter is recognized.But iwconfig gives this.

[COLOR="Blue"]marge@marge-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

rausb0    RT73 WLAN  ESSID:off/any  
          Mode:Auto  Channel=1  Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
[/COLOR]

In networks tools rausb0 shows.It even shows it has transmitted and recieved packets.But it seems to not be accepting my setup.

So why [COLOR="Red"]RT73 WLAN  ESSID:off/any[/COLOR] 
[SIZE="4"]is my /etc/network/interfaces file screwed up?[/SIZE]

[SIZE="4"]Where could I look for a log file thats would show the failed attempt?[/SIZE]

dmseg simply shows 
[COLOR="Red"][  930.785624] usb 2-1: new full speed USB device using uhci_hcd and address 3
[  931.116985] usb 2-1: configuration #1 chosen from 1 choice
[  931.119926] idVendor = 0x50d, idProduct = 0x705a 
[  931.238190] rt73 driver version - 1.0.4.0
[  942.649287] rausb0: no IPv6 routers present[/COLOR]

Which would be correct if it never negoitiated  with the access point

---

