---
title: "idiots guide to getting wg111v2 working on edgy?"
date: 2006-11-15
forum: Networking &amp; Wireless
---

### Post by gammyhand on 2006-11-15
Can someone provide me with an easy to follow guide to getting my netgear wg111v2 working on edgy please?

In networking a wireless network thing showed up and I entered my network key in there and activated the device but I can't actually tell if it is working or not (is there a tool for that or anything?). As far as I can tell it is not as I can't browse the internet and the status light is not on.

---

### Post by FrodoB on 2006-11-15
Plug in the device and at a terminal prompt type:

user@ubuntu:~$ lsmod |grep r8187
r8187                  46596  0 
ieee80211_rtl          85640  2 r8187
usbcore               134912  8 r8187,rt73,usb_storage,libusual,ehci_hcd,uhci_hcd,ohci_hcd

If you see that the r8187 driver, things are looking good.

Run an iwconfig:

wlan0     802.11b/g linked  ESSID:""  
          Mode:Managed  Channel=1  Access Point:
          Bit Rate=54 Mb/s   Sensitivity=4/6  
          Retry:on   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

You should see the device wlan0, if you do then you are on your way.

The light does never comes on with the present driver. 

The excellent Wifi Docs are at:

[https://help.ubuntu.com/community/WifiDocs](https://help.ubuntu.com/community/WifiDocs)

In particular look at:
[https://help.ubuntu.com/community/WifiDocs/WirelessNetworking](https://help.ubuntu.com/community/WifiDocs/WirelessNetworking)

If you are using DHCP it is very easy. Just fill in the network name (ESSID) and the WEP key and then check the box on the device to start the network.

After you configure it you should see something like this. The ESSID is now your access point name and the Access Point field has a MAC identifier in it:

wlan0     802.11b/g linked  ESSID:"My_ESSID"  
          Mode:Managed  Channel=1  Access Point: 00:50:36:D2:35:31   
          Bit Rate=54 Mb/s   Sensitivity=4/6  
          Retry:on   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


Let us know what you find.

---

### Post by gammyhand on 2006-11-15
Thanks for the reply. This is what I get on iwconfig...looks like something is missing?

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11b/g  ESSID:"gandalf"  
          Mode:Managed  Channel=14  Access Point: Not-Associated   
          Bit Rate=11 Mb/s   Sensitivity=4/6  
          Retry:on   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

Not sure why it is 11mb/s either. Should be 54g.

Any ideas?

---

### Post by FrodoB on 2006-11-15
It is not connected yet.

Read and follow:

[https://help.ubuntu.com/community/WifiDocs/WirelessNetworking](https://help.ubuntu.com/community/WifiDocs/WirelessNetworking)

---

### Post by FrodoB on 2006-11-15
Also, if you can't figure out how to activate the network after entering all of the data, you can start it at the command line from a terminal window.

1) Verify that you network data is entered correctly. You can do this like this:

$ sudo gedit /etc/network/interfaces

this is going to open up the interfaces file in the gui text editor. You are looking for a record like this:

iface wlan0 inet dhcp
wireless-essid Gandalf
wireless-key 47256267273897034824456710
auto wlan0

Make sure that your wireless key is correct and that the access point essid is correct. Fix the key if it is incorrect and save the file, otherwise just close the editor.

2) Start the network from a terminal window:

$ sudo ifup wlan0

3) Bring the network down from a terminal window:

$ sudo ifdown wlan0

Good luck, you are nearly there.

---

### Post by gammyhand on 2006-11-15
I have just realised. I use WPA-PSK and on the wireless guide it says that mode is not supported? Guess I need to reconfigure my router? (and all my other wi-fi devices :()

---

### Post by gammyhand on 2006-11-16
> **gammyhand said:**
> I have just realised. I use WPA-PSK and on the wireless guide it says that mode is not supported? Guess I need to reconfigure my router? (and all my other wi-fi devices :()
So I guess the answer to that question is yes?

---

### Post by FrodoB on 2006-11-16
Yes, I thought you had answered your own question. WEP is the way forward.

---

### Post by gammyhand on 2006-11-16
But WEP is not very secure :( Any ideas when Ubuntu will support WPA-PSK?

---

### Post by gammyhand on 2006-11-16
Help! I have removed protection from my router so it is open and I still can't connect the wi-fi. It still says no wireless extensions on a iwconfig.

I did lfdown and lfup and it did start something :(

---

### Post by gammyhand on 2006-11-16
I am close to despair.

I have tried using a 64-bit and 128bit key in my router, it is set to automatic key type but i have tried setting it to shared and open system.

My SSID is correct. I have entered the password in network manager and tried it as hex and ascii and I still get:

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11b/g link..  ESSID:"GANDALF"  
          Mode:Managed  Channel=11  Access Point: Not-Associated   
          Bit Rate=54 Mb/s   Sensitivity=4/6  
          Retry:on   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

What am I doing wrong???

I tried lfdown and lfup and get this:

ralph@frodo:~$ sudo ifdown wlan0
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:0f:b5:c2:f2:64
Sending on   LPF/wlan0/00:0f:b5:c2:f2:64
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 192.168.0.1 port 67
ralph@frodo:~$ sudo ifup wlan0
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:0f:b5:c2:f2:64
Sending on   LPF/wlan0/00:0f:b5:c2:f2:64
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

### Post by FrodoB on 2006-11-16
You have not published the contents of your interfaces file, but the wlan0 part should look like this:

iface wlan0 inet dhcp
wireless-essid Gandalf
wireless-key xxxxxxxxxxxxxxxxxxxxxxxxxx
auto wlan0

replace the Xs with a valid key.

Get some good WEP keys made at:

[http://www.andrewscompanies.com/tools/wep.asp](http://www.andrewscompanies.com/tools/wep.asp)

Put them in the router and in the interfaces file.


Publish the contents of the interfaces file and the output from iwconfig.

---

### Post by gammyhand on 2006-11-18
This is my interfaces file. It looks right to me:

iface eth0 inet dhcp

iface wlan0 inet dhcp
wireless-essid GANDALF
wireless-key D7AA430F80537BB6AFC0370728

auto wlan0

auto eth0

---

### Post by FrodoB on 2006-11-19
> **gammyhand said:**
> This is my interfaces file. It looks right to me:

iface eth0 inet dhcp

iface wlan0 inet dhcp
wireless-essid GANDALF
wireless-key D7AA430F80537BB6AFC0370728

auto wlan0

auto eth0


Looks like from previous posts that it should say (GANDALF as gandalf):

iface wlan0 inet dhcp
wireless-essid gandalf
wireless-key D7AA430F80537BB6AFC0370728

auto wlan0

---

### Post by FrodoB on 2006-11-19
> **gammyhand said:**
> This is my interfaces file. It looks right to me:

iface eth0 inet dhcp

iface wlan0 inet dhcp
wireless-essid GANDALF
wireless-key D7AA430F80537BB6AFC0370728

auto wlan0

auto eth0


Looks like from previous posts that it should say (GANDALF as gandalf):

iface wlan0 inet dhcp
wireless-essid gandalf
wireless-key D7AA430F80537BB6AFC0370728

auto wlan0

Also what do you get from:

$ iwlist wlan0 scanning

This should show you what your router is set as.  The name has to be exact as to letter case.

Mine looks like this on the same type of device.

user@ubuntu:/etc$ iwlist wlan0 scanning
wlan0     Scan completed :
          Cell 01 - Address: 00:90:4A:D9:51:19
                    ESSID:"My_Essid"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:1
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54
                    Quality:83  Signal level:0  Noise level:4
                    Extra: Last beacon: 1312ms ago
          Cell 02 - Address: 00:90:4B:C9:71:29
                    ESSID:"<hidden>"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:1
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54
                    Quality:85  Signal level:0  Noise level:14
                    Extra: Last beacon: 14ms ago

---

### Post by ivago on 2006-11-19
> **FrodoB said:**
> Yes, I thought you had answered your own question. WEP is the way forward.
WEP is certainly NOT the way to go and should never be advised...

---

### Post by FrodoB on 2006-11-19
Ivago;

You are of course correct that it is not the best approach to security and we all know that already, but we are trying to get connected first and then work our way up. 

It certainly is a step above a device that is not working at all.  

As soon as he gets it going he is going to want to get to WPA as that is what he is accustomed to using. 

At any rate thanks for the reminder.

---

