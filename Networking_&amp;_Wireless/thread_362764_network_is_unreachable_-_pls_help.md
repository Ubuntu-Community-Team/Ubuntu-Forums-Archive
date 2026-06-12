---
title: "network is unreachable - pls help"
date: 2007-02-16
forum: Networking &amp; Wireless
---

### Post by vbdanl on 2007-02-16
Hi.  I am getting old trying to get this d-link usb wireless connection to work with linux.
I followed the instructions [here]("http://www.ubuntuforums.org/showthread.php?t=11623&highlight=dwl-122") and get the error "Network is unreachable" when I try to ping a known good address.
I would like to think I am getting close.. but who knows?  Here is the output I hope will make sense to someone:
```
dan@Dan-linux-Antec:/etc/hotplug/usb$ sudo sh ./prism2_usb
message=lnxreq_ifstate
  ifstate=enable
  resultcode=success
message=lnxreq_hostwep
  resultcode=no_value
  decrypt=true
  encrypt=true
message=dot11req_mibset
  mibattribute=dot11PrivacyInvoked=true
  resultcode=success
message=dot11req_mibset
  mibattribute=dot11WEPDefaultKeyID=0
  resultcode=success
message=dot11req_mibset
  mibattribute=dot11WEPDefaultKey0="my_key_ends_with:d1"
  resultcode=success
message=lnxreq_autojoin
  ssid='my_essid_key'
  authtype=sharedkey
  resultcode=success
wlan0     Link encap:Ethernet  HWaddr 00:0D:88:E0:6F:B7  
          inet6 addr: fe80::20d:88ff:fee0:6fb7/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:103 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:31104 (30.3 KiB)

There is already a pid file /var/run/dhclient.pid with pid 6359
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:0d:88:e0:6f:b7
Sending on   LPF/wlan0/00:0d:88:e0:6f:b7
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

dan@Dan-linux-Antec:/etc/hotplug/usb$ ping 172.16.0.1
connect: Network is unreachable
```

Here is what is in /etc/network/interfaces (it actually has a lot more blank lines, but don't think they make any difference):
```
dan@Dan-linux-Antec:/etc/network$ cat interfaces
auto lo
iface lo inet loopback

iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

iface wlan0 inet dhcp
wireless-essid 2WIRE529
wireless-key 00:0D:72:1D:4B:D0

auto wlan0

auto eth0

```

And output from iwconfig:
```
dan@Dan-linux-Antec:/etc/network$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

wlan0     IEEE 802.11-b  ESSID:"2WIRE529"  Nickname:"2WIREXXX"
          Mode:Auto  Frequency:2.427 GHz  Access Point: "MY-ACCESS-PT"   
          Bit Rate:11 Mb/s   Tx-Power:18 dBm   
          Retry min limit:8   RTS thr:off   Fragment thr:off
          Link Quality=50/92  Signal level=-42 dBm  Noise level=-92 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



```
I started reading the post about WPA1, WPA2, etc, but wasn't sure if that was the approach I should be using or not..
I appreciate any help you can offer.. thanks.  dan:confused:

---

### Post by gradedcheese on 2007-02-16
Hi.  First, remove (or just put a '#' in front of) these lines from your /etc/network/interfaces file:

> 
auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp


To edit it, you need to use sudo like this "sudo gedit /etc/network/interfaces".  And then restart networking:

```

sudo /etc/init.d/networking restart

```

Now, so far you are associated but you don't get a DHCP offer.  I suspect that you don't have any WEP-related problems, but there might be some other issues.  Ask dhclient to only use the wifi interface:

```

sudo killall dhclient
sudo dhclient wlan0

```

...does that help?

---

### Post by vbdanl on 2007-02-16
stick with me.. am at work now, and will be around 10pm CST before I get back to the computer.  will try your suggestion.  one other thing i forgot to mention, the network icon in the upper right corner of screen shows "Network not active" or something like that. I have a ethernet cable I unplug from PC next to the one with wireless, in order to establish internet service so i can cut and paste the info i am getting.  i go into admin-network to turn off the ethernet cable when i am trying to get the wireless to work.  not sure if doing that helps or has anything to do with my problem, but just in case..

---

### Post by vbdanl on 2007-02-16
I tried what you suggested.. no luck.. here is the output:
```
dan@Dan-linux-Antec:/etc/network$ sudo vi interfaces
dan@Dan-linux-Antec:/etc/network$ cat interfaces
auto lo
iface lo inet loopback

iface eth0 inet dhcp

# auto eth1
# iface eth1 inet dhcp

# auto eth2
# iface eth2 inet dhcp

# auto ath0
# iface ath0 inet dhcp

iface wlan0 inet dhcp
wireless-essid 2WIRE529
wireless-key 00:0D:72:1D:4B:D0

auto wlan0


auto eth0

```

Not sure if I need a different driver loaded or if there is a default linux driver?
dan@Dan-linux-Antec:/etc/network$ ndiswrapper -l
No drivers installed


dan@Dan-linux-Antec:/etc/network$ sudo vi interfaces
```
dan@Dan-linux-Antec:/etc/network$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.wlan0.pid with pid 4878
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:0d:88:e0:6f:b7
Sending on   LPF/wlan0/00:0d:88:e0:6f:b7
Sending on   Socket/fallback
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device wlan0 ; Operation not supported.
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan0 ; Operation not supported.
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device wlan0 ; Operation not supported.
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan0 ; Operation not supported.
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:0d:88:e0:6f:b7
Sending on   LPF/wlan0/00:0d:88:e0:6f:b7
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

Then the 2nd part:
```
dan@Dan-linux-Antec:/etc/network$ sudo killall dhclient
dan@Dan-linux-Antec:/etc/network$ sudo dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 5322
removed stale PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:0d:88:e0:6f:b7
Sending on   LPF/wlan0/00:0d:88:e0:6f:b7
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
dan@Dan-linux-Antec:/etc/network$ ping 172.16.0.1
PING 172.16.0.1 (172.16.0.1) 56(84) bytes of data.
64 bytes from 172.16.0.1: icmp_seq=1 ttl=255 time=1.56 ms
64 bytes from 172.16.0.1: icmp_seq=2 ttl=255 time=0.490 ms
64 bytes from 172.16.0.1: icmp_seq=3 ttl=255 time=1.40 ms

--- 172.16.0.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2001ms
rtt min/avg/max/mdev = 0.490/1.153/1.566/0.475 ms

```

Thanks for your help.  What should I try now?

---

### Post by chili555 on 2007-02-16
I would change ```
wireless-key 00:0D:72:1D:4B:D0

```

To: ```
wireless-key 000D721D4BD0

```

Then do sudo ifup wlan0 and let us know.

---

### Post by vbdanl on 2007-02-17
> **chili555 said:**
> I would change ```
wireless-key 00:0D:72:1D:4B:D0

```

To: ```
wireless-key 000D721D4BD0

```

Then do sudo ifup wlan0 and let us know.

Here are the results:
```
dan@Dan-linux-Antec:~$ sudo vi /etc/network/interfaces
dan@Dan-linux-Antec:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

iface eth0 inet dhcp

# auto eth1
# iface eth1 inet dhcp

# auto eth2
# iface eth2 inet dhcp

# auto ath0
# iface ath0 inet dhcp

iface wlan0 inet dhcp
wireless-essid 2WIRE529
wireless-key 000D721D4BD0
# wireless-key 00:0D:72:1D:4B:D0

auto wlan0


auto eth0
```

dan@Dan-linux-Antec:~$ sudo ifup wlan0
ifup: interface wlan0 already configured

Here are some notes that help me remember commands I have used (some I remember what they did, some not..).  Maybe I did something that you would think relevant to my wireless problems.. maybe something will pop up..
```
dan@Dan-linux-Antec:~$ cat notes1
# wireless Networking notes
# To install wireless stuff:
sudo apt-get install linux-wlan-ng

# To view usb port scripts:
cd /etc/hotplug/usb

# the wireless commands that get executed during bootup
cat /etc/hotplug/usb/prism2_usb
sudo modprobe prism2_usb prism2_doreset
sudo wlanctl-ng wlan0 lnxreq_ifstate ifstate=enable
sudo wlanctl-ng wlan0 lnxreq_hostwep decrypt=true encrypt=true
sudo wlanctl-ng wlan0 dot11req_mibset mibattribute=dot11PrivacyInvoked=true
sudo wlanctl-ng wlan0 dot11req_mibset mibattribute=dot11WEPDefaultKeyID=0
sudo wlanctl-ng wlan0 dot11req_mibset mibattribute=dot11WEPDefaultKey0="00:0d:72:1d:4b:d1"
sudo wlanctl-ng wlan0 lnxreq_autojoin ssid="2WIRE529" authtype="sharedkey"
sudo ifconfig wlan0
sudo sleep 2
sudo dhclient wlan0

# To restart networking?:
sudo sh /etc/hotplug/usb/prism2_usb

# /etc/network/if-pre-up.d/linux-wlan-ng-pre-up
# This script takes care of bringing up wlan-ng device.
# It is run by ifup, and gets information from the 
# /etc/network/interfaces file. It is derived from the
# init.d/wlan script in the wlan-ng distribution 
# added this line to linux-wlan-ng-pre-up so it would get executed twice during bootup:
result=`$WLANCTL $IFACE lnxreq_ifstate ifstate=enable`

# To check..
lsmod | grep prism
lsmod | grep p802

# To view log output after changing something:
dmesg
cd /proc/net/p80211
cat wlan0

sudo wlan  #not sure what this does

# iwpriv - configure optional parameters of a wireless network interface
# iwpriv is the companion tool to iwconfig(8).  iwpriv deals with parameters and
# settings specific to each driver (as opposed to iwconfig which deals with generic ones)
sudo iwpriv wlan0 set NetworkType=Infra

# Someone suggested renaming prism2_usb to p80211
# I tried it, but didn't seem to make any difference, so changed it back

# To view what wireless drivers are installed:
ndiswrapper -l   (this is a lower case L)
No drivers installed

# To view hardwired network interfaces:
ifconfig

# To display network connections, routing tables, interface statistics,
#     masquerade connections, and multicast memberships
netstat -rn

# To view wireless network interfaces:
iwconfig

# To ping the 2wire default gateway:
ping 172.16.0.1

# To restart networking:
sudo /etc/init.d/networking restart

# To ask dhclient to only use the wifi interface:
sudo kill dhclient
sudo dhclient wlan0
```

Thanks for helping.  What now?

---

### Post by chili555 on 2007-02-19
This: > ifup: interface wlan0 already configured sounds suspiciously like wlan0 got an IP address and is waiting for your next command, like ping -c3 [www.google.com](www.google.com).

Maybe not.

I would also change this: ```
iface wlan0 inet dhcp
wireless-essid 2WIRE529
wireless-key 000D721D4BD0
# wireless-key 00:0D:72:1D:4B:D0

auto wlan0
```

to this; ```
auto wlan0
iface wlan0 inet dhcp
wireless-essid 2WIRE529
wireless-key 000D721D4BD0
# wireless-key 00:0D:72:1D:4B:D0
```

Then do sudo /etc/init.d/networking restart and lets see if we connect.

---

### Post by vbdanl on 2007-02-19
Still no luck. same errors as always.
enter ping 172.16.0.1 (which I can do successfully from this computer with ethernet), and I get "connect: Network is unreachable".
entered: sudo ifup wlan0 and get "ifup: interface wlan0 already configured"
entered: ping -c3 [www.google.com](www.google.com) and get "ping: unknown host www.google.com"
I changed the /etc/network/interfaces file to be exactly as you suggested. then ran
/etc/init.d/networking restart
It comes back with:
Reconfiguring network interfaces..
There is already a pid file..
killed old client process, removed pid file
listening on LPF/wlan0/00:0d:88:e0:6f:b7
Sending on same..
sending on socket/fallback
error for wireless request "Set Encode" (8B2A):
  Set failed on device wlan0 ; Operation not supported.
same for ESSID, same 2 error messages repeated..
there is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
then several DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3 , 6, 6, 12, 14, 18, and 2 error messages.
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

Same errors I always get.
I was wondering if I need to setup a route?
If I enter: route  all I get back is headings, no detail.
Also, I have not tried to install the wpasupplicant package yet.  Should I ?
thanks again for all your help.

---

### Post by chili555 on 2007-02-20
This: > ping 172.16.0.1 (which I can do successfully from this computer with ethernet) is troubling. This IP address is IANA Special Use according to whois. I cannot ping it.

Next, I am suspicious about your wireless-key. Are you using WEP or WPA? The way the wireless-key is set up in /etc/network/interfaces is appropriate for WEP, but not WPA. I realize you have obscured your actual key, but it doesn't seem to be long enough. Please double-check your key in your router and make sure it is exactly that in /etc/network/interfaces.

I would also like to see the output of sudo ifconfig -a as well as sudo iwconfig. 

Hang in, we'll get there.

---

### Post by vbdanl on 2007-02-20
> **chili555 said:**
> This:  is troubling. This IP address is IANA Special Use according to whois. I cannot ping it.

Next, I am suspicious about your wireless-key. Are you using WEP or WPA? The way the wireless-key is set up in /etc/network/interfaces is appropriate for WEP, but not WPA. I realize you have obscured your actual key, but it doesn't seem to be long enough. Please double-check your key in your router and make sure it is exactly that in /etc/network/interfaces.

I would also like to see the output of sudo ifconfig -a as well as sudo iwconfig. 

Hang in, we'll get there.

Chili555 and Gradedcheese - Thanks to both of you for your persistance and devotion. I don't think I ever would have got this to working without your help.  Chili, you were right on in this last post as to what the actual problem was.  Last night around midnight I was reading the 2wire documentation for the nth time, and for some reason listened to what i was reading.. imagine that!. anyway, it said to enter the key from the bottom of the 2wire modem.  I had mistakenly entered the access point as the wireless key.  the access point is also listed in the 2wire documentation, and from all the posts I have been following and commands i have been entering, I thought it was the correct key.  can't say how many times i read where you need to enter your key as xx:xx:xx:xx:xx, which is exactly the same format as the AP.  anyway, I gave it a try last night, and low and behold, it worked.
I don't really know the difference between WPA and WEP to answer your question. I remember some post said to run a command that would take your wireless key and turn it into a long (maybe 40 or so characters) key, and you were supposed to use that instead of the actual 10 digit key - does this make sense ?  I will have to search for that post to see if I can understand the reasoning behind doing that..
When I get home and back on the pc, I will have to ask a few more questions regarding the setup.  thanks again for all your help.
Dan

---

