---
title: "Problems with wireless connection with Ralink 2500 pci"
date: 2007-04-13
forum: Networking &amp; Wireless
---

### Post by nuttiplutt on 2007-04-13
Hi there!

I'm new to Ubuntu and have first tried to install 6.10, but couldn't get wireless connection. I've tried your howto and other tips on how to fill in the "interfaces" file. Well, nothing worked and then I installed 7.04 beta and at least the network was identified, but I couldn't connect with either my own network or some open networks. I even tried to turn off all encryptions and firewall on my router, but still I couldn't connect, not even with WEP through the GUI interface.
I'm doing dual boot with windows xp and can connect to my network in windows.

Is this then a problem with settings or drivers? I don't really have the technical skills to be able to install new drivers for rt2500 and I also get errors that it can't create the rt2500.ko-file with the "make" command.
I've now tried after the new install of 7.04 beta to use the info in this post: [http://ubuntuforums.org/showthread.php?t=241565]("http://ubuntuforums.org/showthread.php?t=241565")
I'll try to post here the output from some commands to give you more info.

```
kristian@ubuntu:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).
# The loopback network interface
auto lo
iface lo inet loopback
# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
script grep
map eth0

auto ra0

iface ra0 inet dhcp
pre-up ifconfig ra0 up
pre-up ifconfig ra0 down
pre-up ifconfig ra0 up
pre-up ifconfig ra0 down
pre-up iwconfig ra0 essid "WLANKRISTIAN"
pre-up iwconfig ra0 mode Managed
pre-up iwpriv ra0 set AuthMode=WPAPSK
pre-up iwpriv ra0 set EncrypType=AES
pre-up iwpriv ra0 set WPAPSK="290********" (my key is 11 numbers)
pre-up ifconfig ra0 up

```

```
kristian@ubuntu:~$ iwconfig ra0
ra0       RT2500 Wireless  ESSID:""  
          Mode:Managed  Frequency=2.412 GHz  Bit Rate:54 Mb/s   Tx-Power:0 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-91 dBm  Noise level:-214 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

```
kristian@ubuntu:~$ lsmod | grep rt
parport_pc             36388  1 
parport                36936  3 ppdev,lp,parport_pc
rt2500                178276  1 
iTCO_vendor_support     4868  1 iTCO_wdt
agpgart                33480  1 intel_agp
```


This is the 'iwlist ra0 scan' that shows my router called WLANKRISTIAN :

```
          Cell 05 - Address: 00:16:38:6F:75:59
                    Mode:Managed
                    ESSID:"WLANKRISTIAN"
                    Encryption key:on
                    Channel:11
                    Quality:0/100  Signal level:-58 dBm  Noise level:-201 dBm

```

Hope someone can help me make it work since Ubuntu doesn't help me if I can't get on the net...

Thanks!

---

### Post by Austin_KW on 2007-04-13
AES does not work, at least for my version of the rt2500 driver. I suggest that you change your network encryption to TKIP.

I dont use 7.04, (still on edgy) so you might might want to remove network-manager which I think is included in feisty. 
"sudo apt-get remove network-manager-gnome" (you can always add it back with "sudo apt-get install network-manager-gnome")

---

### Post by nuttiplutt on 2007-04-14
Thank you for your answer!

I've now made some progress by uninstalling network manager, changing to TKIP and added a netmask and gateway in /etc/network/interfaces:

```
kristian@ubuntu:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).
# The loopback network interface
auto lo
iface lo inet loopback
# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
script grep
map eth0

auto ra0

iface ra0 inet dhcp
netmask 255.255.255.0 [COLOR="Red"](The subnetmask in my router)[/COLOR]
gateway 192.168.2.1 [COLOR="Red"](The gateway in my router)[/COLOR]
pre-up ifconfig ra0 up
pre-up ifconfig ra0 down
pre-up ifconfig ra0 up
pre-up ifconfig ra0 down
pre-up iwconfig ra0 essid "WLANKRISTIAN"
pre-up iwconfig ra0 mode Managed
pre-up iwpriv ra0 set AuthMode=WPAPSK
pre-up iwpriv ra0 set EncrypType=TKIP
pre-up iwpriv ra0 set WPAPSK="2909*******" [COLOR="Red"](I use 11 numbers as key)[/COLOR]
pre-up ifconfig ra0 up

```

Now at least I get a link quality to my router in iwconfig which I didn't get before:

```
kristian@ubuntu:~$ iwconfig ra0
ra0       RT2500 Wireless  ESSID:"WLANKRISTIAN"  
          Mode:Managed  Frequency=2.412 GHz  Bit Rate:24 Mb/s   Tx-Power:1 dBm   
          RTS thr:off   Fragment thr:off
          [COLOR="Red"]Link Quality=66/100[/COLOR]  Signal level=-60 dBm  Noise level:-212 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

But I don't get connection and when I do the "ifdown ra0" and "ifup ra0", it still tries to get connection on 255.255.255.255, but I thought I set the netmask to be 255.255.255.0 as it is set in my router. I can't change to .255 in the router as it says it only allows numbers between 0-255.

I've done restarts of the computer between changing the settings.
I also finally managed to install the build-essentials as I finally realized that I had to put in the installation cd for it to find the files! :)  

Hope you have suggestions of a next step since I feel I'm getting closer to making it work!

Thanks!

---

### Post by Austin_KW on 2007-04-14
You are making progress. 255.255.255.255 is the broadcast ip (all networks/all stations) and it is correct that the dhcp client should try to connect to it (anyone) to get an ip address.

You should not have to set the netmask or gateway because you are using dhcp. When the dhcp server responds it will set these parameters.

I cannot tell if the dhcp request succeeded;
What is the output from "ifconfig ra0" or "sudo dhclient ra0"


PS. If you want to build a newer version of the driver you will need the kernel headers in addition to build-essientials
 sudo apt-get install linux-headers-`(uname -r)`

---

### Post by nuttiplutt on 2007-04-15
Hi again!

I got a bit of panic since I've done several edits and suddenly lost the link quality completely, but soon realized that I've done some typing errors, but that's all corrected now.

The kernel headers were already installed and with latest version.
I haven't tried to update drivers to rt2500 yet since I'm afraid it will ruin the small progress I've got so far with getting link quality to the router. I've read that the 7.04 beta version have quite updated drivers for rt2500 already installed.

Btw, could the problems be linked to firewalls? I haven't changed anything in firewall settings in 7.04, but on my router I have firewall enabled. I did earlier try to turn off both firewall and all encryptions on my router, but still didn't get connected. That was under 6.10 version, though.


Ok, here's the latest outputs from the commands:

```
kristian@ubuntu:~$ sudo dhclient ra0
There is already a pid file /var/run/dhclient.pid with pid 6101
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/
Listening on LPF/ra0/00:0e:2e:52:2a:f8
Sending on   LPF/ra0/00:0e:2e:52:2a:f8
Sending on   Socket/fallback
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


kristian@ubuntu:~$ ifconfig ra0
ra0       Link encap:Ethernet  HWaddr 00:0E:2E:52:2A:F8  
          inet6 addr: fe80::20e:2eff:fe52:2af8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16209 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5231 (5.1 KiB)  TX bytes:648663 (633.4 KiB)
          Interrupt:20 Base address:0xc000


kristian@ubuntu:~$ iwconfig
lo        no wireless extensions.
ra0       RT2500 Wireless  ESSID:"WLANKRISTIAN"  
          Mode:Managed  Frequency=2.462 GHz  Access Point: 00:16:38:6F:75:59   
          Bit Rate:24 Mb/s   Tx-Power:2 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=85/100  Signal level=-57 dBm  Noise level:-202 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

---

### Post by Austin_KW on 2007-04-15
Still not getting an IP address. 

If you can not get connected even with encryption off, do you have mac access control in your router.

I think now i would download the serialmonkey.com cvs driver and try build it. You can always save a copy of the current driver. It is easy to reinstall it, if necessary
"locate rt2500.ko" will find it, it is somewhere in /lib/module/your kernel version.

But I dont know why you can not connect in 6.10. It works for me at least with the pcimcia card (same driver). So double check you router config (esp. dhcp enabled, mac address filtering disabled, encryption key and type).

---

### Post by nuttiplutt on 2007-04-15
Yes, it seems to be the point where I better install newest drivers, check all settings in router and even try out a static ip-address. If none of that helps and I even turn off all security on the router for a while, then and first THEN will I give up! :D ;) 

I'll post a new report to you when it's done.

Thanks again!

---

### Post by nuttiplutt on 2007-04-16
Latest news and yes, it's good news!

I think that the updating of drivers solved the problem although I'm still not exactly sure of what the problem was.

After updating the drivers and rebooting, I still didn't get connected, but after running these three commands, I got connected!

```
kristian@ubuntu:~$ sudo ifup ra0
ifup: interface ra0 already configured
kristian@ubuntu:~$ iwconfig
lo        no wireless extensions.

ra0       RT2500 Wireless  ESSID:"WLANKRISTIAN"  
          Mode:Managed  Frequency=2.462 GHz  Access Point: 00:16:38:6F:75:59   
          Bit Rate:54 Mb/s   Tx-Power:0 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=67/100  Signal level=-58 dBm  Noise level:-195 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


kristian@ubuntu:~$ sudo ifdown ra0
There is already a pid file /var/run/dhclient.ra0.pid with pid 4974
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/
Listening on LPF/ra0/00:0e:2e:52:2a:f8
Sending on   LPF/ra0/00:0e:2e:52:2a:f8
Sending on   Socket/fallback
[COLOR="Red"]DHCPRELEASE on ra0 to 192.168.2.1 port 67       (This entry was new after installing latest drivers)[/COLOR]


kristian@ubuntu:~$ sudo ifup ra0
There is already a pid file /var/run/dhclient.ra0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/
Listening on LPF/ra0/00:0e:2e:52:2a:f8
Sending on   LPF/ra0/00:0e:2e:52:2a:f8
Sending on   Socket/fallback
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 12
DHCPOFFER from 192.168.2.1
DHCPREQUEST on ra0 to 255.255.255.255 port 67
DHCPACK from 192.168.2.1
bound to 192.168.2.2 -- renewal in 505858 seconds
```

And then after a big cheer, I did the 315 updates and rebooted.
To my big surprise, I wasn't connected to the net after the reboot, so I ran the three commands in the exact same order, and I got a connection again. After that, I've automatically got connected every time I've started Ubuntu.

I can now conquer the world!! :D 

Thank you so much for helping me with this!

---

### Post by Austin_KW on 2007-04-16
Good news, Just remember to keep the sources for the driver. If you update the kernel you may need to do the make again or at least "make install"

---

### Post by smo0th on 2007-04-18
This is how it worked for me:

[http://ubuntuforums.org/showthread.php?p=2472174#post2472174](http://ubuntuforums.org/showthread.php?p=2472174#post2472174)

\\:D/

---

### Post by Bartezz on 2007-04-18
Let me begin by apoloigising if this is a stupid question.

All of the above has happened on my new install of 6.10 Edgy.

I can ping my router and administer the router from ubuntu but I cannot connect to the internet.

I have to follow the ifup, ifdown, iwconfig routine above to be able to see the router but after that it is all well.

What are the "315 updates" stated above?

And is there anything else I can do to get connected to the internet as I my eagerness in Linux is fading?

Please help the newest of the new here? :KS

---

### Post by Austin_KW on 2007-04-18
If you can ping and administer your router you are almost there and you are on your local network. So internet problems will then usually be routing or DNS lookup.

what is the output from the following commands  
ping -c 3 google.com
ping -c 3 64.233.167.99
ifconfig ra0
cat /etc/network/interfaces
cat /etc/resolv.conf
route

---

### Post by Bartezz on 2007-04-18
I have managed to solve the issue now.

It appears that the internet was not being allowed due to the IPV6 standard being used as default. Once I disabled IPV6 by following this:
 IPV6

    *

      The internet standard is currently considered ipv4. The new standard, ipv6, is slowly being implemented to replace ipv4. Because it's not widely used at the moment, ipv6 can cause problems. It is enabled by default in Ubuntu. This can cause no internet if above seems ok.
          o

            Firefox specific
                +

                  In the address bar type about:config. Find this line network.dns.disableIPv6 and double click on it to change the value to true.
          o

            System wide
                +

                  Open the file /etc/modprobe.d/aliases
                  Add the first three lines to the file. The line with # starting is already in the file. Find it and add the # in front of it.

      alias net-pf-10 ipv6 off
      alias net-pf-10 off
      alias ipv6 off
      #alias net-pf-10 ipv6

      After making these changes a reboot is required.

Everything is now peachy. What a wonderful learning curve this is, I feel like my dad with a mobile phone.:D

---

### Post by nuttiplutt on 2007-04-18
> **Bartezz said:**
> 

What are the "315 updates" stated above?



Glad to hear that it works as I know how frustrating it is not getting connection. My reference to the 315 updates was merely that after I finnaly got connected, the first thing I did was to run Update Manager to download and install all updates to Ubuntu 7.04 Beta. Being a Windows user, I was a bit overwhelmed that I had 315 new updates to Ubuntu. But it went like a charm...in the end! :D

---

### Post by Bartezz on 2007-04-19
Ah thanks for the explanation.

Although happy to have connection it is still not being connected yet, but there is loads of time now as there is no frustration in running a few commands to get wireless network.

this minor niggle still beats Windows for me. 

:)

---

### Post by RavanH on 2007-04-19
Hey! Without getting technical: have you given Wicd Manager a try? It did what Network Manager couldn't on my machine with a Ralink RT2500 pcie card... And easy too! No difficult config or file-editing needed :)

See [http://adam.blackhole.cx/wicd/wb/](http://adam.blackhole.cx/wicd/wb/)

---

### Post by Austin_KW on 2007-04-19
For graphical configuration the is also RutilT (originaly developed for rt2500 cards), it should support wpa etc [http://cbbk.free.fr/bonrom/](http://cbbk.free.fr/bonrom/) 

(I think you need "sudo apt-get install build-essential libgtk2.0-dev")

---

### Post by wilderness wanderer on 2007-04-20
My 2 cents:

rt2500 pci card worked fine under Edgy. Upgraded via alt CD and no network. Numerous attempts at getting network manager to sort it out failed. I uninstalled network manager and it still will not connect via the Gnome network GUI. Note that this is with WEP encryption.

I _am_ able to connect via the command line:

sudo ifconfig ra0 down
sudo iwconfig ra0 essid blahblahblah key hexblahblah
sudo dhclient ra0

I found this at [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/37120](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/37120)

Syntax to manually configure in /etc/network/interfaces

iface ra0 inet dhcp
        pre-up ifconfig ra0 up
        pre-up ifconfig ra0 down
        pre-up ifconfig ra0 up
        pre-up ifconfig ra0 down
        pre-up iwconfig ra0 essid "MyRouterName"
        pre-up iwconfig ra0 mode Managed
        pre-up iwpriv ra0 set AuthMode=WPAPSK
        pre-up iwpriv ra0 set EncrypType=TKIP
        pre-up iwpriv ra0 set WPAPSK="MySecretPassword
        pre-up ifconfig ra0 up
auto ra0

Since I am only using WEP, modified to:

iface ra0 inet dhcp
        pre-up ifconfig ra0 up
        pre-up ifconfig ra0 down
        pre-up ifconfig ra0 up
        pre-up ifconfig ra0 down
        pre-up iwconfig ra0 essid "MyRouterName"
        pre-up iwconfig ra0 key "MyKeyInHex"
        pre-up iwconfig ra0 mode Managed
        pre-up ifconfig ra0 up
auto ra0

Now I have wireless connectivity which survives a reboot.

---

