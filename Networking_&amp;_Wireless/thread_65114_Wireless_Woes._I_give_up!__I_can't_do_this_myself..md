---
title: "Wireless Woes. I give up!  I can't do this myself."
date: 2005-09-13
forum: Networking &amp; Wireless
---

### Post by ububu on 2005-09-13
I have gone through the HOW-TO; ipw2200 +WPA about 10 times now and can't get beyond a certain point.  My laptop, a panasonic W4, seems to be able to see other APs and sends and receives OK but doesn't give me a signal level indication and doesn't "associate."  All I want is to be able to go to one of those free-wifi internet coffeehouses and get connected to the internet.  I can connect to the internet with no problems using the wires that come out of the wall at work and eth0.  Also, my computer connects wireless pretty effortlessly when I have booted up Windows (which I'm trying to get away from).a  My wireless chip (or is it a card) is an Intel Pro/Wireless 2915 ABG.  There is a lot of terminology that I don't quite understand yet.  I find that a lot of the books that I am pouring over aren't written for newbies and the ones that are don't seem to give enough information about setting up individual systems.  I am not sure what I am supposed to do when I want to connect to the internet.  I have found three menus items at the top of the screen that seem to have something to do with the network but I don't know when I am supposed to use them and the Ubuntu guide doesn't help me.  I am not even sure how to test to see if the wireless is working.  Anyway, I'm going to post what I see other people post when they ask for help and see what happens.  Thank you if you have the time to respond.  I don't understand essid and ssid and psk  so I just made up somethings (Ubuntuqualia and 7Ubuntuqualia7) in the /etc/wpa_supplicant.conf file:

ctrl_interface=/var/run/wpa_supplicant

network={
       ssid="Ubuntuqualia"
       scan_ssid=1
       proto=WPA
       key_mgmt=WPA-PSK
       psk="7Ubuntuqualia7"
}

sh-3.00# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:"Ubuntuqualia"
          Mode:Managed  Channel=0  Access Point: 00:00:00:00:00:00
          Bit Rate=0 kb/s   Tx-Power=20 dBm
          Retry limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

sh-3.00# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0B:97:30:52:A4
          inet addr:128.218.129.83  Bcast:128.218.255.255  Mask:255.255.255.0
          inet6 addr: fe80::20b:97ff:fe30:52a4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12078 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2959 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:3241706 (3.0 MiB)  TX bytes:637929 (622.9 KiB)
          Interrupt:19 Base address:0x3000

eth1      Link encap:Ethernet  HWaddr 00:12:F0:67:75:49
          inet6 addr: fe80::212:f0ff:fe67:7549/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2988 errors:0 dropped:25 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:21 Base address:0xe000 Memory:b0101000-b0101fff

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:30810 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30810 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:10176499 (9.7 MiB)  TX bytes:10176499 (9.7 MiB)

sh-3.00# dhclient eth1
Internet Systems Consortium DHCP Client V3.0.1
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth1/00:12:f0:67:75:49
Sending on   LPF/eth1/00:12:f0:67:75:49
Sending on   Socket/fallback
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 17
No DHCPOFFERS received.
Trying recorded lease 192.168.0.8
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.

--- 192.168.0.1 ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms

No working leases in persistent database - sleeping.

In the /etc/init.d/wifi_wpa.sh file this is what I entered:

#! /bin/sh
# wifi: wpa_supplicant init
echo " * [Wifi]: Enabling WPA supplicant..."
if [ -x /usr/sbin/wpa_supplicant ]; then
    /usr/sbin/wpa_supplicant -B -i eth1 -c /etc/wpa_supplicant.conf -D ipw -w
fi

exit 0

---

### Post by knappen on 2005-09-13
ssid is the name of the network you are trying to connect to. You cant just make one up. same goes for psk etc.

Do they use WPA or WEP?

---

### Post by ububu on 2005-09-13
Thanks for your reply.  I want to be able to connect to wireless APs at public places like coffee houses.  I don't seem to need to know the ssid or WEP or WPA keys when I use windows.  Is my computer supposed to automatically insert these when the wifi is being offered for free at places like that?  What should I set the ssid and psk to in such cases?  By the way, I did try to configure eth1 using my neighbor's ssid and WEP key.  My computer saw their signal (iwlist scan results positive), but still saw no signal strength in the connections properties window and I was not able to connect to the internet through my browser.

---

### Post by knappen on 2005-09-14
Are you running the preview release of ubuntu?

---

### Post by mlomker on 2005-09-14
> I don't seem to need to know the ssid or WEP or WPA keys when I use windows.

Sure you do.  Windows cannot connect to a secure access point without you putting in the keys (WEP/WPA).  You don't always need to know the SSID in linux, either.  The system will automatically connect to the strongest/closest access point.  The problem is that might not be yours...it might belong to your neighbor. 

> computer saw their signal (iwlist scan results positive), but still saw no signal strength in the connections properties window.

I'm not sure what tool you're using for that.  If you are using gnome then I'd recommend downloading a copy of [GTK Wifi.](http://ubuntuforums.org/showthread.php?t=34645) 

I have the same card in my machine.  First, let's verify that your driver is working.  Type this in a terminal prompt:

```

dmesg | grep ipw2200

```

I'm assuming that it's fine, but it's worth checking.

wpa_supplicant is basically a file where you list access points and their encryption key information (if they are not an open access point).  The point behind it is that wpa_supplicant will always connect to those configured points if they are in range...that way you won't automatically reconnect to your neighbors access point if it happens to have a stronger signal at the moment that you boot up.  With the bogus configuration that you currently have it isn't doing anything for you....your machine will simply connect to the strongest signal.

If I wanted to manually connect to my access point at home I'd do this:

```

ifconfig eth1 up
iwconfig eth1 essid "2409"
dhclient eth1

```

The iwlist scan command is how you find the ESSID (fancy ancronym that is really just a name) of the access points within range.

I'd recommend that you use a tool like GTK Wifi because it is graphical rather than command-line.

---

### Post by ububu on 2005-09-18
Thank you again for your reply.  I did as you suggested and downloaded GTKwireless.  I am at a friend's who has wireless set up in his home.  I have configured eth1 with his essid, wep key, ip address, subnet mask, and gateway address and still no go.  Here are some of the outputs that I got using the shell commands that you recommended:

sh-3.00# dmesg | grep ipw2200
ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.0.6
ipw2200: Copyright(c) 2003-2004 Intel Corporation
ipw2200: Detected Intel PRO/Wireless 2915ABG Network Connection
sh-3.00# ifconfig eth1 up
sh-3.00# iwconfig eth1 essid grace
sh-3.00# dhclient eth1
Internet Systems Consortium DHCP Client V3.0.1
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth1/00:12:f0:67:75:49
Sending on   LPF/eth1/00:12:f0:67:75:49
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
No working leases in persistent database – sleeping.

After I input all of the information about my friend's wireless I re-did this command:

sh-3.00# dmesg | grep ipw2200
ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.0.6
ipw2200: Copyright(c) 2003-2004 Intel Corporation
ipw2200: Detected Intel PRO/Wireless 2915ABG Network Connection
ipw2200: failed to send SCAN_ABORT command
ipw2200: failed to send CARD_DISABLE command
sh-3.00#

---

### Post by mlomker on 2005-09-18
Please post the contents of /etc/network/interfaces.

---

### Post by ububu on 2005-09-19
Please post the contents of /etc/network/interfaces:


# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

iface eth0 inet static
          address 128.218.129.83
          netmask 255.255.255.0
          gateway 128.218.129.1


# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth1

auto eth0


iface eth1 inet static
address 192.168.1.102
netmask 255.255.255.0
wireless-essid grace
wireless-key 50DDD7F895
gateway 192.168.1.1

auto eth1

---

### Post by ububu on 2005-09-19
I just tried to connect to my friend's wireless network using GTK.  It failed and gave the message that DCHP failed.  I could see that the signal strength was very strong while it was trying though.  Progress?

---

### Post by knappen on 2005-09-19
This may not apply to you, but make sure that the network accept your mac address. If your friend has activated mac restrictions and you are not in the list, you will never be able to connect.

Worth looking into becasue it is easy to forget if it is activated or not.

---

### Post by ububu on 2005-09-19
I am finding this exceedingly difficult to follow because I don't understand any of the jargon.  Does anybody know of a good primer on wireless networking that can explain to a lay person what all of the parameters that I am playing with are?  Is an encryption key something that I get from my computer or from the source of the wireless signal?  An example of a basic question that I don't really get.  Thanks.

---

### Post by mlomker on 2005-09-19
>  Is an encryption key something that I get from my computer or from the source of the wireless signal?

An encryption key is something that you program into your wireless access point and the setting on your PC has to match or they won't work.  

If you just buy an access point and plug it in then it won't have any security on it at all.  Out of the box it would be an 'open' access point (anyone can connect to it if they are within range).

---

### Post by ububu on 2005-09-20
Problem solved.  I don't exactly know what I did, but one thing that I know is that I have been thinking that eth1 was wireless and eth0 was for wired stuff and when eth0 got assigned to wireless it suddenly worked fine, both with my friend's network that requires a key and at a coffee house.  Thank you for all of your replies.  I don't exactly know how I should have known this or if making eth0 the wireless one was important.  Can anybody explain it to  me?  I thought it was supposed to be eth1 because of the way the how for installing the driver for ipw2200 was written.

---

