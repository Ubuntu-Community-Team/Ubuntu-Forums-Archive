---
title: "Problem with Wireless Connection, dell latitude d820, intel ipw3945 card"
date: 2006-12-22
forum: Networking &amp; Wireless
---

### Post by jck3j on 2006-12-22
I installed Ubuntu Edgy Eft about a week ago and have been having trouble configuring my wireless card. It works on windows fine, but i'm trying to make the switch to full-time linux. I have an Intel PRO/Wireless 3945ABG card and a dell latitude d820. I have tried many times to get this work to no success. I was wondering if anyone has this card with a similar computer and has gotten this to work.

---

### Post by n00b@linux on 2006-12-22
I do not have your PC but I do have your wireless nic.  It is working with WPA-PSK in my Alienware Area-51 m5550.

Have you tried```
lspci | grep 3945
```to check that the kernel has recognised it?

Have you tried```
lsmod | grep ipw3945
```to check that the 'ipw3945' kernel module has been loaded?

Have you tried```
iwconfig
```to see if 'eth1' or 'wlan0' is listed?

---

### Post by jck3j on 2006-12-22
This is what i get.

```

lspci | grep 3945
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

```

```

jck3j@jck3j-laptop:~$ lsmod | grep ipw3945
ipw3945               124576  1 
ieee80211              35272  1 ipw3945

```
and
```

jck3j@jck3j-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

eth1      unassociated  ESSID:"default"  
          Mode:Managed  Frequency=nan kHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:104   Missed beacon:0

```

I have WPA-PSK encryption. I have tried to use wpa_supplicant before, but I am not sure if i am doing it correctly. The name of the network in my house is 'default.'

---

### Post by jml on 2006-12-22
First, try to simplify your set up.  Disable all encryption temporarily and see if you can connect in the clear.  Be sure to disable any other network card.  Wireless will not work with any other card enabled.  If you can connect that way, then you know that its not a driver issue.

Next download two applications with Synaptic:  network-manager and network-manager-gnome.  You should also have wpa_supplicant installed, but don't try to configure it manually.  Network-manager does a good job of that.  If these suggestions are too sketchy, search this sub-forum and the wiki for network-manager and you should be able to find more detailed instructions.  Hope this helps.

Joe

---

### Post by n00b@linux on 2006-12-22
Excellent.  Your lspci result shows that the kernel has correctly recognised the device.  Your lsmod result shows that the device driver has been loaded.  You simply need to configure the 'eth1' interface.  Follow the thread in my sig and you should be good to go.  It worked for me and, given your results from the above commands, I see no reason why it shouldn't work for you.  Post back if it worked, or if you're still having problems :)

---

### Post by jck3j on 2006-12-22
I am having a problem with the /etc/network/interfaces file. I edited it as follows

"iface eth1 inet static
wireless-essid default
address 192.168.168.40
netmask 255.255.255.0
network 192.168.168.0
broadcast 192.168.168.255
gateway 192.168.168.230
dns-nameservers 192.168.168.230
wpa-driver wext
wpa-conf managed
wpa-ssid default
wpa-ap-scan 2
wpa-proto RSN
wpa-pairwise CCMP
wpa-group CCMP
wpa-key-mgmt WPA-PSK
wpa-psk -------------------------------------------------------"

i used wpa_supplicant to get the wpa-psk.

but i get an error when i try restarting the network.
```

jck3j@jck3j-laptop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth0.pid with pid 12253
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:15:c5:07:ae:ec
Sending on   LPF/eth0/00:15:c5:07:ae:ec
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.0.1 port 67
There is already a pid file /var/run/dhclient.eth2.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
eth2: ERROR while getting interface flags: No such device
eth2: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth2.
There is already a pid file /var/run/dhclient.ath0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
ath0: ERROR while getting interface flags: No such device
ath0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up ath0.
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.
There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:15:c5:07:ae:ec
Sending on   LPF/eth0/00:15:c5:07:ae:ec
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
                                                                         [ ok ]
jck3j@jck3j-laptop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth0.pid with pid 12513
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:15:c5:07:ae:ec
Sending on   LPF/eth0/00:15:c5:07:ae:ec
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.0.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
There is already a pid file /var/run/dhclient.eth2.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
eth2: ERROR while getting interface flags: No such device
eth2: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth2.
There is already a pid file /var/run/dhclient.ath0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
ath0: ERROR while getting interface flags: No such device
ath0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up ath0.
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.
There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:15:c5:07:ae:ec
Sending on   LPF/eth0/00:15:c5:07:ae:ec
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
                                                                         [ ok ]

```
Do you see any errors?

Do I need to change anything in lines 2-7 of the /etc/network/interfaces file?

---

### Post by jck3j on 2006-12-23
Thank you both for your help. I ended up using the NetworkManager Applet 0.6.3 and it seems to work really well for my system.

---

### Post by Azakus on 2006-12-23
> **jck3j said:**
> Thank you both for your help. I ended up using the NetworkManager Applet 0.6.3 and it seems to work really well for my system.

I love that applet.

---

### Post by CapnJ1105 on 2007-08-14
Hey,
I just got a dell latitude D820, and I am having wireless problems as well.  I am not sure why.  Mine also works fine with windows, but not with linux mint?  I am kind of new to linux so any help you could provide would be great.  Do I need to do some extra configuration or something?

Thanks so much,

---

