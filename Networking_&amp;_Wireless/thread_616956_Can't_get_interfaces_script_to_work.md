---
title: "Can't get interfaces script to work"
date: 2007-11-18
forum: Networking &amp; Wireless
---

### Post by david_215 on 2007-11-18
I have messed with my interfaces script so many times that I've lost track of what's what.

Here's what I've got:

david@kitchen:~$ cat /etc/network/interfaces 
auto lo
iface lo inet loopback

#auto eth0
iface eth0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wpa-passphrase "**************"
wpa-ssid "delta-juliet-bravo-golf"
iwconfig wlan0 up


Here's my iwconfig:

david@kitchen:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"delta-juliet-bravo-golf"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:18:F8:FE:F8:F8   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Signal level=-53 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


My wireless card was recognized as ra0 under Feisty, but it is now wlan0 after my Gutsy upgrade.

I must type the following after every reboot in order to get my connection to work:

sudo ifdown wlan0
sudo ifup wlan0

This works every time (so far).

I think the fix for this is probably easy...can someone give me the proper lines for my interfaces script so I don't have to keep resetting the connection manually?

Many thanks.

---

### Post by kevdog on 2007-11-18
Try this:

auto wlan0
iface wlan0 inet dhcp
pre-up ifconfig wlan0 down
pre-up ifconfig wlan0 up
pre-up ifconfig wlan0 down
pre-up ifconfig wlan0 up
wpa-passphrase "**************"
wpa-ssid "delta-juliet-bravo-golf"
iwconfig wlan0 up

Lastly it might be right but with your:
wpa-passphrase "**************"

I thought the form was either
wpa-passphrase XXXXXXX <---Hex Key without quotes or
wpa-passphrase s:ASCII_KEY_WITHOUT_QUOTES

Let me know if this doesnt work, I have some other ideas.

---

### Post by david_215 on 2007-11-18
I tried your suggestion, but it didn't work.  Just curious--why repeat the pre-up down/up series?

Maybe it would help to see the output when I "sudo ifdown wlan0":

There is already a pid file /var/run/dhclient.wlan0.pid with pid 4780
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:1c:10:6a:44:6e
Sending on   LPF/wlan0/00:1c:10:6a:44:6e
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 192.168.2.1 port 67


And when I "sudo ifup wlan0":

ioctl[SIOCSIWAUTH]: Operation not supported
WEXT auth param 4 value 0x0 - ioctl[SIOCSIWAUTH]: Operation not supported
WEXT auth param 5 value 0x1 - There is already a pid file /var/run/dhclient.wlan0.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:1c:10:6a:44:6e
Sending on   LPF/wlan0/00:1c:10:6a:44:6e
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPOFFER from 192.168.2.1
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPACK from 192.168.2.1
bound to 192.168.2.103 -- renewal in 32851 seconds.

---

### Post by kevdog on 2007-11-18
Ok try the following (Ive read about this trick before but Im applying it in a new fashion):

auto wlan0
iface wlan0 inet dhcp
ifconfig wlan0 down
ifconfig wlan0 up
ifconfig wlan0 down
wpa-passphrase "**************"
wpa-ssid "delta-juliet-bravo-golf"
ifconfig wlan0 up

---

### Post by david_215 on 2007-11-18
Sadly, it didn't work.  In fact, here's what I received when I tried my "sudo ifdown wlan0" trick:

david@kitchen:~$ sudo ifdown wlan0
[sudo] password for david:
/etc/network/interfaces:10: duplicate option
ifdown: couldn't read interfaces file "/etc/network/interfaces"

I restored the interfaces script and am now back up.

Is there another script that is run during boot-up where I could add the "ifdown/ifup"?  Something that is run after interfaces?

---

### Post by kevdog on 2007-11-18
The answer to your question is yes, but it depends upon the run-level and where you want to put it.  You need to ensure that all the wireless kernel packages are up and running before you cycle the interface.  I tried doing what you described a long time ago, but it didnt work for me.  

Sorry I couldn't help you.  I know its possible, however what is happening, is that initially your wireless is trying to connect before a dependency is properly loaded, causing it to fail.  When you type your commands the dependency is loaded so there isnt a problem.  Sorry I can't be of any further help.

---

### Post by david_215 on 2007-11-19
Adding a start-up script seemed to do the trick.  
I followed the instructions from this link:  [http://ubuntu.wordpress.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/](http://ubuntu.wordpress.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/)

My script is just a two-liner:
ifdown wlan0
ifup wlan0

Thanks for the help, Kevdog.

---

