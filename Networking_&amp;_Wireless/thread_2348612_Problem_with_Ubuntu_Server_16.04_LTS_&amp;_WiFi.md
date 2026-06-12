---
title: "Problem with Ubuntu Server 16.04 LTS &amp; WiFi"
date: 2017-01-05
forum: Networking &amp; Wireless
---

### Post by jjhudak on 2017-01-05
I recently did a clean install of Ubuntu Server 16.04 LTS and configured the WiFi connection service correctly – it found the router, provided the correct WPA-2 key and it connected and said everything was fine.

Installation successfully terminated, I power cycled the machine and rebooted.  It came up fine. 
I did a package update and got error messages saying, effectively, that it can’t connect to the package servers.  I opened up the router connection table and saw that it had not issued an ip address to the server.  I rebooted the server again thinking there was a hiccup….same problem occurred.

Apparently the server will not automatically make a wireless connection to the router?  How can I force it to do this?  In the past, I’ve installed other Ubuntu LTS servers (8.04, 12.04) and they always connected via the wireless on boot.  How can this be solved?

Thanks
John

---

### Post by chili555 on 2017-01-05
> configured the WiFi connection service correctly Please show us the files:```
iwconfig
cat /etc/network/interfaces
```Of course, redact any passwords.

---

### Post by jjhudak on 2017-01-05
the results you requested:
~$ ifconfig
lo           Link encap:Local Loopback
                Inet addr:127.0.0.1 Mask: 255.0.0.0
                Inet6 addr: ::1/128 Scope:Host
                UP LOOPBACK RUNNING MTU:65536 Metric:1
                RX packets:500 errors:0 dropped:0 overruns:0 frame:0
                TX packets:500 errors:0 dropped:0 overruns:0 carrier
                collisions:0 txqueuelen:1
                RX bytes:38704  (38.7 KB) TX bytes: 38704  (38.7 KB)
~$ iwconfig
lo           no wireless extensions.
Enp3s0  no wireless extensions.
Wlp2s0 IEEE 802.11bgn ESSID:off/any
                Mode:Managed Access Point: Not-Associated Tx-Power=0 dBm
                Retry short limit:7  RTS thr:off Fragment thr:off
                Power Management:off
~$ cat /etc/network/interfaces
#This file describes the network interfaces available on your system
# and how to activate them.  For more information, see interfaces(5)
source /etc/network/interfaces.d/*
#the loopback network interface
auto lo
iface lo inet loopback

---

### Post by chili555 on 2017-01-06
>  configured the WiFi connection service correctly Where? How?

Evidently, this server is running a desktop environment and Network Manager. Ordinarily, using NM, one merely needs to click the icon and see ones network, click on the network and supply the WPA2 password. Did you do something else? What? 

In Network Manager, did you select "Automatically connect to this network when it is available"?

---

### Post by jjhudak on 2017-01-06
> **chili555 said:**
> Where? How?

Evidently, this server is running a desktop environment and Network Manager. Ordinarily, using NM, one merely needs to click the icon and see ones network, click on the network and supply the WPA2 password. Did you do something else? What? 

In Network Manager, did you select "Automatically connect to this network when it is available"?

No - I downloaded Server, so how could it be running a desktop environment?
No Icons - this is a headless server and everything is done through the CL.

I was inaccurate in my previous post.  Last evening I reinstalled from the CD.  The network connection that was established via wifi was a temporary thing, just to dnld additional packages needed for the configuration I selected (e.g. apache, mysql, OpenSSH, etc.) I interperted this as a network connection that would remain when rebooted to run the system. From the above info, the system does not know about the wireless link.

So my question now is: How can I establish a wireless link to the router?  I want to use WPA2 with a preshared passkey.
Thanks
J

---

### Post by nraygun on 2017-01-06
I'm in the same boat you are. Why would the install ask for the primary network interface, configure it, allow the use of it, but then not have it ready at boot? Very frustrating and not intuitive.

OK, rant off.

I'm in the same boat but I've gotten a little further by editing the interfaces file in /etc/network. I have:
[FONT=courier new]auto wlp2s0
iface wlp2s0 inet dhcp
wireless-essid Blah
wireless-key blahblah123[/FONT]

And it gets hung up on DHCP with numerous "DHCPDISCOVER on wlp2s0 to 255.255.255.255 port 67 interval 3 (xid=0xc2f3c329)" messages and ultimately failing.

---

### Post by chili555 on 2017-01-06
> **nraygun said:**
> I'm in the same boat you are. Why would the install ask for the primary network interface, configure it, allow the use of it, but then not have it ready at boot? Very frustrating and not intuitive.

OK, rant off.

I'm in the same boat but I've gotten a little further by editing the interfaces file in /etc/network. I have:
[FONT=courier new]auto wlp2s0
iface wlp2s0 inet dhcp
wireless-essid Blah
wireless-key blahblah123[/FONT]

And it gets hung up on DHCP with numerous "DHCPDISCOVER on wlp2s0 to 255.255.255.255 port 67 interval 3 (xid=0xc2f3c329)" messages and ultimately failing.Please start your own new question.

---

### Post by chili555 on 2017-01-06
> How can I establish a wireless link to the router? Please try this: [http://askubuntu.com/questions/464507/ubuntu-14-04-server-wifi-wpa2-personal/464552#464552](http://askubuntu.com/questions/464507/ubuntu-14-04-server-wifi-wpa2-personal/464552#464552)

I recommend a static IP address so that you can ftp and ssh to it. Of course, also substitute your interface, wlp2s0.

---

### Post by jjhudak on 2017-01-06
Thank you - I'll give it a shot.  The procedure makes sense. 
The discussion in the thread also outlines a dynamic IP address via DHCP  - I'll try this first and then create a reservation in my router and  then reconfigure the server to have a static IP address.

BTW, you don't need a static IP address for either ssh or ftp...just  makes it easier in that one does not have to look up the assigned IP  address when configured by DHCP.
Thanks again.

Just curious, why does this issue even exist? The installation procedure is very misleading.
OMG, I just found out that Ubuntu changed to systemd in 16.04.....sigh.
J

---

### Post by chili555 on 2017-01-06
> BTW, you don't need a static IP address for either ssh or ftp...just makes it easier in that one does not have to look up the assigned IP address when configured by DHCP.I am well aware of that. I just prefer and recommend the easy way. Not everyone has a router that allows DHCP reservations.>  why does this issue even exist?I think the developers that put together the server edition assume a certain level of skill in these matters. Obviously, based on the number of questions I answer just like this, the skill level varies.

---

### Post by jjhudak on 2017-01-09
> **nraygun said:**
> I'm in the same boat you are. Why would the install ask for the primary network interface, configure it, allow the use of it, but then not have it ready at boot? Very frustrating and not intuitive.

OK, rant off.

I'm in the same boat but I've gotten a little further by editing the interfaces file in /etc/network. I have:
[FONT=courier new]auto wlp2s0
iface wlp2s0 inet dhcp
wireless-essid Blah
wireless-key blahblah123[/FONT]

And it gets hung up on DHCP with numerous "DHCPDISCOVER on wlp2s0 to 255.255.255.255 port 67 interval 3 (xid=0xc2f3c329)" messages and ultimately failing.

I basically did the same thing you did, and am getting the same result.  I consulted the  thread that chili555 referenced, and used the approach suggested later in the responses where the comment was using DHCP,  and get the same results.
I am stuck at this point.....suggestions anyone???
Thank you
j

---

### Post by chili555 on 2017-01-09
> **jjhudak said:**
> I basically did the same thing you did, and am getting the same result.  I consulted the  thread that chili555 referenced, and used the approach suggested later in the responses where the comment was using DHCP,  and get the same results.
I am stuck at this point.....suggestions anyone???
Thank you
jMay we please see your interfaces file with the password redacted? Also:```
iwconfig
```

---

### Post by jjhudak on 2017-01-09
I'll get this when I can access the machine later today.
In the mean time, been reading some additional docs and they referr to using wpa_supplicant  since the router uses WPA2.  Should I be using wpa_supplicant?

---

### Post by chili555 on 2017-01-09
> **jjhudak said:**
> I'll get this when I can access the machine later today.
In the mean time, been reading some additional docs and they referr to using wpa_supplicant  since the router uses WPA2.  Should I be using wpa_supplicant?That's a more complicated method to connect but it is unnecessary to write the conf file and customize it. A proper /etc/network/interfaces file will do perfectly well.

---

### Post by jjhudak on 2017-01-09
jjh@pluto-server:~$ iwconfig
lo        no wireless extensions.

enp3s0    no wireless extensions.

wlp2s0    IEEE 802.11bgn  ESSID:"M*****"
          Mode:Managed  Frequency:2.432 GHz  Access Point: 00:7F:28:C8:11:AE
          Bit Rate=19.5 Mb/s   Tx-Power=17 dBm
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=24/70  Signal level=-86 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:3  Invalid misc:594   Missed beacon:0

My interfaces file:
jjh@pluto-server:/etc/network$ cat interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).
source /etc/network/interfaces.d/*
#The loopback network interface
#auto lo
#iface lo inet loopback
#
#auto  wlp2s0
#iface wlp2s0 inet static
#address 192.168.1.190
#netmask 255.255.255.0
#gateway 192.168.1.1
#wpa-ssid M******
#wpa-psk L******
#dns-nameservers 8.8.8.8 192.168.1.1
#
auto wlp2s0
iface wlp2s0 inet dhcp
wpa-ssid M*****
wpa-psk L***************

After editing the file,
command I executed:
sudo ifup &#8211;v wlp2s0

And it connected - It did not work previously because I had a typo in my router password

Here is my network interfaces:

jjh@pluto-server:~$ ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:196 errors:0 dropped:0 overruns:0 frame:0
          TX packets:196 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1
          RX bytes:14000 (14.0 KB)  TX bytes:14000 (14.0 KB)

wlp2s0    Link encap:Ethernet  HWaddr 48:5d:60:7e:80:85
          inet addr:192.168.1.10  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::4a5d:60ff:fe7e:8085/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:112741 errors:0 dropped:0 overruns:0 frame:0
          TX packets:54135 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:162739529 (162.7 MB)  TX bytes:5336149 (5.3 MB)

As you can see, I am connected at 192.168.1.10   (Yea!)
Thank you very much for your help!!!- i learned a few things.
If you see anything incorrect or can suggest something better for the above information, please let me know.
j

---

### Post by chili555 on 2017-01-09
It looks like you are all set! Glad it's working.

---

