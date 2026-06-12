---
title: "Feisty won't boot network, but manually, it works..."
date: 2007-04-20
forum: Networking &amp; Wireless
---

### Post by elmerfud on 2007-04-20
What is going on here ?

$ping [www.cbc.ca](www.cbc.ca)
ping: unknown host [www.cbc.ca](www.cbc.ca)

<No connection to Internet !>

$ sudo /etc/init.d/networking stop
 * Deconfiguring network interfaces...                                                 There is already a pid file /var/run/dhclient.wlan0.pid with pid 4075
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:90:4b:57:ea:5b
Sending on   LPF/wlan0/00:90:4b:57:ea:5b
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 192.168.1.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
                                                                                [ OK ]
$ sudo /etc/init.d/networking start
 * Configuring network interfaces...                                                   There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:90:4b:57:ea:5b
Sending on   LPF/wlan0/00:90:4b:57:ea:5b
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPOFFER from 192.168.1.1
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.101 -- renewal in 35409 seconds.

<networking now works>

Only problem with this is that I can't have my nfs mounts in fstab because it fails unless networking works at boot up. 

How do I fix this ?

---

### Post by elmerfud on 2007-04-20
$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:C0:9F:3E:CA:71
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:21 Base address:0x8800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:90:4B:57:EA:5B
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1877 (1.8 KiB)  TX bytes:1122 (1.0 KiB)
          Interrupt:22 Memory:d2004000-d2006000

$ ping [www.cbc.ca](www.cbc.ca)
ping: unknown host [www.cbc.ca](www.cbc.ca)

$ sudo /etc/init.d/networking stop
Password:
 * Deconfiguring network interfaces...                                                 There is already a pid file /var/run/dhclient.wlan0.pid with pid 4108
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:90:4b:57:ea:5b
Sending on   LPF/wlan0/00:90:4b:57:ea:5b
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 192.168.1.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
                                                                                [ OK ]
$ sudo /etc/init.d/networking start
 * Configuring network interfaces...                                                   There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:90:4b:57:ea:5b
Sending on   LPF/wlan0/00:90:4b:57:ea:5b
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPOFFER from 192.168.1.1
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.101 -- renewal in 40165 seconds.
                                                                                [ OK ]

ping [www.cbc.ca](www.cbc.ca)
PING a1849.gc.akamai.net (80.67.74.105) 56(84) bytes of data.
64 bytes from 80.67.74.105: icmp_seq=1 ttl=56 time=47.4 ms
64 bytes from 80.67.74.105: icmp_seq=2 ttl=56 time=46.5 ms
64 bytes from 80.67.74.105: icmp_seq=3 ttl=56 time=46.0 ms

--- a1849.gc.akamai.net ping statistics ---
4 packets transmitted, 3 received, 25% packet loss, time 15181ms
rtt min/avg/max/mdev = 46.019/46.676/47.417/0.573 ms

$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:C0:9F:3E:CA:71
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:21 Base address:0x8800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:90:4B:57:EA:5B
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::290:4bff:fe57:ea5b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:39 errors:0 dropped:0 overruns:0 frame:0
          TX packets:64 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:5604 (5.4 KiB)  TX bytes:9102 (8.8 KiB)
          Interrupt:22 Memory:d2004000-d2006000

$ ping [www.google.com](www.google.com)
PING [www.l.google.com](www.l.google.com) (66.102.7.104) 56(84) bytes of data.
64 bytes from mc-in-f104.google.com (66.102.7.104): icmp_seq=1 ttl=243 time=49.8 ms
64 bytes from mc-in-f104.google.com (66.102.7.104): icmp_seq=2 ttl=243 time=45.3 ms
64 bytes from mc-in-f104.google.com (66.102.7.104): icmp_seq=3 ttl=243 time=46.6 ms
64 bytes from mc-in-f104.google.com (66.102.7.104): icmp_seq=4 ttl=243 time=44.3 ms
64 bytes from mc-in-f104.google.com (66.102.7.104): icmp_seq=5 ttl=243 time=44.7 ms
64 bytes from mc-in-f104.google.com (66.102.7.104): icmp_seq=6 ttl=243 time=46.6 ms
64 bytes from mc-in-f104.google.com (66.102.7.104): icmp_seq=7 ttl=243 time=85.9 ms
64 bytes from mc-in-f104.google.com (66.102.7.104): icmp_seq=8 ttl=243 time=46.3 ms
64 bytes from mc-in-f104.google.com (66.102.7.104): icmp_seq=10 ttl=243 time=47.3 ms

--- [www.l.google.com](www.l.google.com) ping statistics ---
10 packets transmitted, 9 received, 10% packet loss, time 13074ms
rtt min/avg/max/mdev = 44.350/50.804/85.954/12.521 ms

---

### Post by elmerfud on 2007-04-20
$ dmesg | grep ndis
[   25.820277] ndiswrapper version 1.38 loaded (preempt=no,smp=yes)
[   25.979388] ndiswrapper: driver bcmwl5 (Broadcom,06/26/2004, 3.70.17.0) loaded
[   25.985231] ndiswrapper: using IRQ 22
[   26.616315] usbcore: registered new interface driver ndiswrapper

$ dmesg | grep wlan0
[   26.616094] wlan0: ethernet device 00:90:4b:57:ea:5b using NDIS driver: bcmwl5, version: 0x3461100, NDIS version: 0x501, vendor: '', 14E4:4320:103C:12F4.5.conf
[   26.616151] wlan0: encryption modes supported: WEP; TKIP with WPA; AES/CCMP with WPA
[  168.422812] wlan0: no IPv6 routers present

---

### Post by mike2357 on 2007-04-20
Exact same problem for me.

Contents of /etc/dhcp3/dhclient.conf and /etc/network/interfaces attached in tar file.

---

### Post by ggw10 on 2007-04-21
Exactly the same for me. I have an intel macbook (Atheros wireless chipset). I have it
set up for manual configuration. After I boot, it has successfully associated with my wireless 
network, it has configured the interface, but it does not have a local IP address or routing. If
I do 
sudo /etc/init.d/neworking restart,
then the networking is fine. Very strange. What happens, or doesn't happen, on boot
that stops the network from working?

Graham

---

### Post by mike2357 on 2007-04-21
It's still a problem for me, although I did learn of one way to speed things up.  After I installed Fiesty and logged on, a network status icon began on appear in the notification area of my panel.  After I boot, it reports there is no network connection.

I can left-click on the icon and select Wired Network, and a network connection is established.

Like the other authors who posted here, I have no idea what's preventing connectivity when I boot.  The above solution may save a few keystrokes, but it's not really viable since by the time I log on, it's too late for other services that start when booting but depend on connectivity.

---

### Post by elmerfud on 2007-04-23
I removed Network Manager from my system using Adept and now the network works when I boot up.

---

### Post by thorby on 2007-04-23
Exactly the same problem after installing Feisty in a Parallels virtual machine in Mac OS X. This VM had been running Edgy just dandy, networking "just worked," but after the Feisty install, no network connection.

Like the people above, I futzed around and found that if I just did **sudo dhclient** it would grab a DHCP lease and all would be sweet until reboot.

Thank you, Mike2357, for pointing out that network icon in the status bar -- I'm sure that will do the same thing as the dhclient command did.

elmerfud -- could you expand on the statement "removed Network Manager ... using Adept" ? What's Adept and is Network Manager something new or newly enabled in Feisty?

---

### Post by thorby on 2007-04-23
OK, removing Network Manager was a **BAD IDEA**. I noted that the network icon in the status bar was in fact the Gnu Network Manager, which ironically is supposed to make networking completely easy.

It does not. I quickly found that it would not remember that I wanted a Wired Network from one reboot to the next, so I followed elmerfud's advice and removed Network Manager -- using Synaptic. 

Now my Feisty machine won't let me login. It boots up, I sign in, and it hangs before the desktop appears.

I am going to have to do a complete reinstall, it looks like. This is not nice.


n.b. the previous reply was entered from firefox inside the Feisty virtual machine. This one is from mac os x in the host machine -- I don't have a working Feisty any more :confused:

---

### Post by MaX on 2007-04-23
Just install it again from the command line then?

Ctrl+Alt+F1

---

### Post by thorby on 2007-04-23
I got a failsafe xterm session going and did the install, found the correct command on the ubuntuguide.org wiki, and that got me a working gnome session again anyway.

At startup there is a message, **the Network Manager applet could not find some required resources, it cannot continue**. And there is no little network icon in the status bar -- and no network. 

Manual execution of **sudo dhclient** restores networking as before.

I would greatly appreciate some info on how to configure this wunnerful Network Manager so it would automatically start up the wired network -- like Edgy did without any help, grump.

---

### Post by elmerfud on 2007-04-23
Do you have your network devices enabled ? (System Settings -> Network Settings)

Network manager is an application that sits on top of the regular network services.  I cannot think of any reason why removing it should crash your system.  

There is no need to re install !  There NEVER is with Linux.  Do a command line boot and do an apt-get install.

---

### Post by thorby on 2007-04-23
> Do you have your network devices enabled ? (System Settings -> Network Settings)I presume you mean System > Administration > Network? (I don't see anything with "Settings" in its name).

That's the first place I went when, after first booting Feisty, it was clear there was no access. The Network admin app is not very informative, but there is a plus sign by "Wired connection" which is set for Address:dhcp. Under Properties it says "Configuration: Automatic configuration (DHCP)". And there is no connectivity going on.

Unlike the Mac OS X network panels, there is nothing I can do with the Network settings, for example I can't tell it to "renew dhcp lease" like I can with OS X. Or use it to see any other settings, like the OS X TCP settings, etc. It's really uninformative.

Anyway, when I get a terminal and "sudo dhclient" I get connectivity immediately, i.e. I can use Network Tools to ping and lookup, firefox to browse etc. Also true if I just selected "Wired network" from the Network Manager applet -- before I ruined it!

> Network manager is an application that sits on top of the regular network services. I cannot think of any reason why removing it should crash your system.It does not crash the system, it hangs login. After I used Synaptic to remove it, on the next boot, I could not log in. I entered my id and password and the "butterscotch screen" came up -- but not the musical sounds and not the Ubuntu CPU or whatever that graphic is -- and it just hung. After a few seconds the upper left corner of the screen turned white. That was it.

The only way to get a login to work was to use the login options to force a "safe terminal" session and use apt-get to install Network Manager. Now, as I said, I can log in and when I do, I get a message that the applet is missing something, and there is no Network Manager applet in the status bar.

I would love to know how to fully restore the network manager and even more, would love to know how to make it do what it is supposed to do (make networking seamless).

---

### Post by not-a-bot on 2007-04-24
I have a similar problem, but even worse. It's driving me nuts. On Edgy everything worked fine.

Now there is no wired network connection after booting although everything looks fine. I have to manually select my wired network in the new network manager (which already was selected, received the correct IP from my router, etc). After the pretty reconnecting animation everything works fine ... but just for a while. Once there is no network traffic for a few minutes my connection is dead again. All information looks perfectly alright, but no traffic will go in or out. I have to manually reconnect all the time. :(

---

### Post by ilantz on 2007-04-24
Hi !

You guys made sure the /etc/network/interfaces file got all lines commented except the loopback interface?
most of the network manager probs being posted are sourced in that config file...

eg:

auto lo
iface lo inet loopback

#iface eth0 inet static
#address 192.168.x.x
#netmask 255.255.255.0
#gateway 192.168.x.x
#auto eth0

---

### Post by MaX on 2007-04-24
A friend of mine installed 6.10 just a day or two before Feisty was released, everything worked fine.

Now he has done the upgrade (via update-manager) to Feisty and his network needs restarting to work after a reboot.

What has happened inbetween? He doesn't have a clue about config files and wouldn't have touched one manually.

Ubuntu F-ed something up with this update.

---

### Post by sefs on 2007-04-27
This happens in both upgrade or fresh install for me.

On boot the network applet icon is there pretty as you please with lights flashing but no one is home.  I have to restart the net work to get connectivity.  Wonder if it has to do with via chipsets and motherboards.

---

### Post by burito on 2007-09-03
hmm, this is the closest problem I can find to my issue, but yeah, basically networking did work, and some updates ago (completely unsure of how long ago) it stopped.

I've got an ASUS F3JP, and the wireless works perfectly every time with the proprietry drivers, that worked out of the box (no need to install a single package), and so did the realtek 8169 network card. Now for the life of me I cannot get the rtl8169 to work anymore.

burito@burito:~$ lsmod | grep r8169
r8169                  32392  0 
burito@burito:~$ 

That strikes me as odd.
Odder still is when I...
burito@burito:~$ sudo ifconfig eth0 192.168.1.5
It appears to work, however when I ping my router at 192.168.1.1 I get "no route to host".
I was thinking this was avahi/wireless related, until I noticed that the r8169 module had no references. I've tried booting a clean system (no non-free modules) and the same results. No matter what I kill it doesnt want to play. I fear this is IPtables/something beardy related, which is quite beyond me ;_;

but, in actual direct contribution to the thread, what network adapters does everyone use, and if you know, is the relevant module getting any references?

edit: silly me, found something better describing my problem - [http://ubuntuforums.org/showthread.php?t=538448&highlight=r8169](http://ubuntuforums.org/showthread.php?t=538448&highlight=r8169) - , sooner or later I'll learn,

---

