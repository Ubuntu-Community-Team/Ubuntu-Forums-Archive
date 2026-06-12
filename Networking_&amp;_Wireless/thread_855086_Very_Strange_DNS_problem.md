---
title: "Very Strange DNS problem"
date: 2008-07-10
forum: Networking &amp; Wireless
---

### Post by andymic on 2008-07-10
Hi,

I recently loaded ubunto 8.04 onto a laptop so I could play with it whilst working away from home.

The laptop is a Samsung X50 which uses an Intel2915 wireless adaptor.

During setup I could not get the wireless adapter running so chose the fixed ethernet port as my primary.

Post install and following updates the adapter worked and I have excellent signal strength.

However, I appear to have a strange DNS problem.

If I connect via cat5 to my ADSL router I can resolve url's without any problem.

If I connect via the WAP (which is also connected to the same ADSL router) firefox just hangs and eventually asks me to try again.  If i type 64.233.183.104 into the browser it takes me straight to google.

Both connections use DHCP.

I'm confused........

---

### Post by superprash2003 on 2008-07-10
when you are connected only  via wireless.. go to the terminal and type cat /etc/resolv.conf and post output here

---

### Post by mattze on 2008-07-10
find out what interface your wireless is on via iwconfig.
then try sudo dhclient [wireless interface].
the dns server can be tested via dig [hostname].

---

### Post by andymic on 2008-07-10
Right o,

I've done all as suggested results are as follows.

andy@ubuntu:~$ cat /etc/resolv.conf
### BEGIN INFO
#
# Modified_by:  NetworkManager
# Process:      /usr/bin/NetworkManager
# Process_id:   4943
#
### END INFO

search qt-spt1.local


nameserver 192.168.93.1

where qt-spt1.local is a windows dhcp server



andy@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"QTBR"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1D:7E:A0:AA:D0   
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=91/100  Signal level=-38 dBm  Noise level=-91 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

andy@ubuntu:~$ sudo dhclient eth1
[sudo] password for andy: 
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:0e:35:a8:c5:82
Sending on   LPF/eth1/00:0e:35:a8:c5:82
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPOFFER of 192.168.93.27 from 192.168.93.1
DHCPREQUEST of 192.168.93.27 on eth1 to 255.255.255.255 port 67
DHCPACK of 192.168.93.27 from 192.168.93.1
bound to 192.168.93.27 -- renewal in 307886 seconds.


All of these commands issued whilst wireless was on and cat5 disconnected

---

### Post by andymic on 2008-07-10
Just to clarify.

I also had the exact same problem last night at my flat through a netgear router (providing DHCP).

I know that IP's are being issued properly and DNS setup correctly when using my Vista (spit) laptop.

---

### Post by superprash2003 on 2008-07-10
hmm.. i would say it would be better you try using opendns servers.. [http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html)

---

### Post by toolzen on 2008-07-10
Try this:

Go into the file /etc/nsswitch.

Go to the line that starts with "hosts" and make sure the word "dns" is listed. 

If it is not, add it. 

Restart and try to connect. 

I had a similar problem in open solaris (could go to any website by typing ip address, but not domain name), and that was the standard fix.

On a side note - Solaris may be the "worlds most powerful operating system," but it isn't for the weak of stomach.

Anyway, try the above and if it doesn't work we'll go from there.

---

