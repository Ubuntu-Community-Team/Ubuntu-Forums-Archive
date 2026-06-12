---
title: "Making a VPN connection, what needed?"
date: 2007-06-29
forum: Networking &amp; Wireless
---

### Post by Riel on 2007-06-29
Hello,


I have a working Wifi Network, and I want to connect to the server on my office via VPN.

Problem is, in the whole Ubuntu, i really can't find anything about VPN, there are no options in the network-manager. 

Are there any short howto's to setup a VPN connection, what programs to install etc? I use PPTP or something like that ;) I'm not really into it.

In internet-explorer I had to surf to //xxxxnfp1   to get to my maps etc. How would this work on Ubuntu, I can't just surf there I guess?


Thanx in Advance, the rest of Ubuntu is working like a charm!!! I am really impressed...

---

### Post by dkd903 on 2007-06-29
this will help you a lot as it did 2 my friend:::
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_Configure_and_start_PPTP_tunnels_.28VPN.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_Configure_and_start_PPTP_tunnels_.28VPN.29)

---

### Post by Riel on 2007-06-29
So, a whole lot of information. I'll go trough it, thank you very much already, I'll let you know if I managed it.

---

### Post by Riel on 2007-06-29
This has been my problem:

To setup a VPN Click the NetworkManager Icon in the tray VPN Connections->Configure VPN Use the defaults and be sure to check the box: Refuse EAP under the Authentication tab. To get my connection to work I also had to check Require MPPE Encryption under Compression & Encryption


I did the step before, installed the pptp component, but can't see VPN Connections in the tray.

I did a restart after install.

I see VPN connection manager (PPP Generic) under Programs, Internet. What icon does it have? It has some 'windows .exe file'-like icon. Is that right? Cause, when I click it, nothing happens.

Can it be, because Connection Manager is running during install? I can't close it I guess, for I need the Wifi connection to install the program?

---

### Post by Riel on 2007-06-29
Instructions here and problems:

[I]
right-click the network icon on your system tray and choose Remove,[/I]

I can only see 'Start Network'  (or something like that -> it's Dutch ('Netwerk Aanzetten')
And in grey ' Connection info'  and and Info line.

At left click I can only see ' Manual Configuration' .



Installing manually does this:

    * Install manually 

wget -c [http://linux.edu.lv/uploads/content/pptp.tar.gz](http://linux.edu.lv/uploads/content/pptp.tar.gz)
tar zxvf pptp.tar.gz
cd ./pptp/
sudo sh ./pptp/install
cd ..

```
riel@noname:~$ wget -c http://linux.edu.lv/uploads/content/pptp.tar.gz
--19:25:19--  http://linux.edu.lv/uploads/content/pptp.tar.gz
           => `pptp.tar.gz'
Herleiden van linux.edu.lv... 195.13.158.141
Verbinding maken met linux.edu.lv|195.13.158.141|:80... verbonden.
HTTP-verzoek is verzonden; wachten op antwoord... 200 OK
Lengte: 2,377,599 (2.3M) [application/octet-stream]

100%[====================================>] 2,377,599    130.60K/s    ETA 00:00

19:25:37 (131.98 KB/s) - 'pptp.tar.gz' opgeslagen [2377599/2377599]

riel@noname:~$ tar zxvf pptp.tar.gz
pptp/install-seciiba
pptp/php-pcntl_4.3.8-2_i386.deb
pptp/libglade0_1%3a0.17-3_i386.deb
pptp/libglib1.2_1.2.10-9_i386.deb
pptp/libgtk1.2-common_1.2.10-17_all.deb
pptp/libgtk1.2_1.2.10-17_i386.deb
pptp/libxml1_1%3a1.8.17-10_i386.deb
pptp/php-gtk-pcntl_1.0.0-2_i386.deb
pptp/pptp-linux_1.5.0-4_i386.deb
pptp/install
pptp/pptpconfig_20040809_all.deb
riel@noname:~$ cd ./pptp/
riel@noname:~/pptp$ sudo sh ./pptp/install
sh: Can't open ./pptp/install

```

---

### Post by Riel on 2007-06-29
It is installed with Network Manager turned off, but nothing happens either. When I go to Applications -> internet I still see VPN Connection Manager, but clicking it does simply nothing??

Now I'm stuck!

---

### Post by Riel on 2007-06-29
Next thing I tried is starting nm-nm-vpn-properties with GKSUDO

It works, properties OPEN, I get to set up my network, but in the Terminal it got some problems (the GUI just works):

```
riel@noname:~$ gksudo

** (nm-vpn-properties:6392): WARNING **: Cannot open module '/usr/lib/network-manager-vpnc/libnm-vpnc-properties'

** (nm-vpn-properties:6392): CRITICAL **: vpnui_opt_connect_signals: assertion `opt->widget!=NULL' failed

** (nm-vpn-properties:6392): CRITICAL **: vpnui_opt_connect_signals: assertion `opt->widget!=NULL' failed

** (nm-vpn-properties:6392): CRITICAL **: vpnui_opt_connect_signals: assertion `opt->widget!=NULL' failed
esd: Esound sound daemon already running or stale UNIX socket
/tmp/.esd-0/socket
This socket already exists indicating esd is already running.
Exiting...

(nm-vpn-properties:6392): Gtk-CRITICAL **: gtk_widget_set_sensitive: assertion `GTK_IS_WIDGET (widget)' failed

(nm-vpn-properties:6392): Gtk-CRITICAL **: gtk_widget_set_sensitive: assertion `GTK_IS_WIDGET (widget)' failed

(nm-vpn-properties:6392): Gtk-CRITICAL **: gtk_widget_set_sensitive: assertion `GTK_IS_WIDGET (widget)' failed
edit_cb

(nm-vpn-properties:6392): Gtk-CRITICAL **: gtk_widget_set_sensitive: assertion `GTK_IS_WIDGET (widget)' failed

(nm-vpn-properties:6392): Gtk-CRITICAL **: gtk_widget_set_sensitive: assertion `GTK_IS_WIDGET (widget)' failed

(nm-vpn-properties:6392): Gtk-CRITICAL **: gtk_widget_set_sensitive: assertion `GTK_IS_WIDGET (widget)' failed

(nm-vpn-properties:6392): Gtk-CRITICAL **: gtk_widget_set_sensitive: assertion `GTK_IS_WIDGET (widget)' failed

(nm-vpn-properties:6392): Gtk-CRITICAL **: gtk_widget_set_sensitive: assertion `GTK_IS_WIDGET (widget)' failed

(nm-vpn-properties:6392): Gtk-CRITICAL **: gtk_widget_set_sensitive: assertion `GTK_IS_WIDGET (widget)' failed

** (nm-vpn-properties:6392): WARNING **: Widget show event

```





Now, I got a connection set up, but how do I go to connect to it??

---

### Post by cursebg on 2007-06-30
man i have exactly the same problem... since months and it's still unsolved :(

---

### Post by Riel on 2007-07-01
I read the topic everyday, but seems  a hard problem.

Maybe change the title to something more attracitve? :p

---

### Post by Riel on 2007-07-02
Damn,

don't make this be the reason to go back to winXP .. :(:(

I really need my VPN :(

---

### Post by ntetreau on 2007-07-02
This is more of a "Bump" than anything else, but I use the NetworkManager VPN addon for Cisco without problems.  I just installed it with Synaptic, then when I left Click on NM > VPN Connections > Configure VPN I get a nice GUI to configure it.  

What if you try this in a terminal:

```
sudo killall NetworkManager
sudo NetworkManager --no-daemon
```

you should get a few lines relating to starting VPN services, perhaps they are some clues?

Also, you can take a look at the syslog, and see if you get clues there also?

In the mean time, try to install the NM vpnc addon, just to see if you get the extra option in NM, including the configure VPN gui.  Perhaps it is a bug in the pptp vpn?

Nic

---

### Post by Riel on 2007-07-02
Try that later this evening.
Thanx for the new option!
I see a lot of forums trough the internet with the same prob! No real solutions there!

I am even thinking about letting some Linux-guy/girl come to my house to get it all working and just pay him/her :) Opensource is cool , but the time spending on how things work are too expensive for me atm.

For now, just the VPN and for my business i'm 100% rolling. Just some home-stuff that needs to be fixed.

---

### Post by rimoth on 2007-07-02
I use vpnc it works a treat. Just install and then convert your cisco.pcf using pcf2vpnc. I use it through the command line as I couldn't find a gui. Nonetheless dead easy to use.

---

### Post by Riel on 2007-07-02
ok, that's nice, but what did you exactly do? :p I' m quite new, but  eager to learn :)

I need to connect to a PPTP server (or something like that :p)

---

### Post by Riel on 2007-07-02
> **ntetreau said:**
> This is more of a "Bump" than anything else, but I use the NetworkManager VPN addon for Cisco without problems.  I just installed it with Synaptic, then when I left Click on NM > VPN Connections > Configure VPN I get a nice GUI to configure it.  

What if you try this in a terminal:

```
sudo killall NetworkManager
sudo NetworkManager --no-daemon
```

you should get a few lines relating to starting VPN services, perhaps they are some clues?

Also, you can take a look at the syslog, and see if you get clues there also?

In the mean time, try to install the NM vpnc addon, just to see if you get the extra option in NM, including the configure VPN gui.  Perhaps it is a bug in the pptp vpn?

Nic

```
riel@noname:~$ sudo NetworkManager --no-daemon
NetworkManager: <information>   starting...
NetworkManager: <information>   Adding VPN service 'org.freedesktop.NetworkManager.vpnc' with name 'vpnc' and program '/usr/lib/network-manager-vpnc/nm-vpnc-service'
NetworkManager: <information>   Adding VPN service 'org.freedesktop.NetworkManager.ppp_starter' with name 'ppp' and program '/usr/bin/nm-ppp-starter'
NetworkManager: <information>   Updating allowed wireless network lists.
NetworkManager: <WARNING>        nm_dbus_get_networks_cb (): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored..
NetworkManager: <WARNING>        nm_signal_handler (): Caught signal 2, shutting down normally.
NetworkManager: <information>   Caught terminiation signal
NetworkManager: <debug info>    [1183399493.722250] nm_print_open_socks (): Open Sockets List:
NetworkManager: <debug info>    [1183399493.722339] nm_print_open_socks (): Open Sockets List Done.
riel@noname:~$ 

```

Heeej, no wireless networks found?

I am typing this with a Wireless Connection, fully functioning with NM, like a charm.
Strange.

---

### Post by Riel on 2007-07-02
I found it here too:

[https://lists.ubuntu.com/archives/ubuntu-bugs/2007-January/387953.html](https://lists.ubuntu.com/archives/ubuntu-bugs/2007-January/387953.html)

---

### Post by rimoth on 2007-07-02
OK through System>Administration>synaptic package manger. Click search type in vpnc - install this package.

To run it run from a terminal window run (apps>accesories>terminal) sudo vpnc-connect. This uses a default.conf not sure where it is located - just google all the key workds. Stick with it when it works then you're 100% there and no looking back....good luck


I'm not sure this works with pptp.

To edit the default.conf file use sudo gedit dir/filename.conf

---

### Post by ntetreau on 2007-07-03
Riel, don't worry about the wireless warnings, its irrelevant as far as your concerned.  The VPN services seems to start fine.  Do you get a "VPN Connections" when you left click on the NM icon?

Nic

PS:  I have added a screenshot showing in synaptic the pptp vpn module installed for NM, the options in NM to configure VPN as well as PPTP tunnel showing up when I try to add a new VPN tunnel.  Let me know what you get.

---

### Post by Riel on 2007-07-03
I only see ' Manual configuration' (in dutch).

Maybe the languageversion is a problem?

IN ' 2'  you see the VPN PPP link. Strange icon? Clicking it does nothing.

---

### Post by Riel on 2007-07-03
3 is right click menu

(turn on network, and in grey networkinfo)

---

### Post by ntetreau on 2007-07-03
I have that strange icon as well and nothing happens when i click on it.  It seems your problem is not really one of VPN but more one related to NM.  You see, you should have more than just manual configuration when you click on it.  If you go into System > Administration > Network  what do you have listed (give as much details as possible.)  Also, try to comment out (adding # at the beginning of each line of text) everything in the file /etc/network/interfaces except for the 2 lines relating to the "lo" interface.

```
sudo gedit /etc/network/interfaces
```

Restart the computer and see what you get.

Nic

---

### Post by ntetreau on 2007-07-03
Try this as well to reconfigure NM:

```
 sudo dpkg-reconfigure network-manager
```

Nic

---

### Post by Riel on 2007-07-03
What must I comment out?

(reconfigure didn't help)


```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface

iface eth0 inet dhcp




iface ath0 inet dhcp
wireless-essid Frtizboxriel
wireless-key s:1234567890abc

auto ath0
```

withouth the last 3 i would have no connection left I guess (not tried it). Can you tell me what to # out?




Screenshots are the info you asked.

---

### Post by Riel on 2007-07-03
Just let the 2 lines with LO there.

Reboot.

Hmm .. no network, but I was sure about that.

Left click ...

and:
[B]
YESSSSSSSSSSSS[/B]


Just had to reconfigure the Wireless connection again, but that worked flawlessly.


Now all seems ok. Thank you very much.
This could be helpful for everyone, and i saw, it was in the wiki!!!!! 
The wiki is hard to find/or find related stuff. Maybe an item to work on. I totally missed it, and I looked a lot trough there :)


But, what was the problem after all? Why didn't it work at first? Now I want to know :)

---

### Post by ntetreau on 2007-07-03
Good to see everything is working, enjoy ubuntu!

Nic

---

### Post by Riel on 2007-07-03
Almost everything, but not completedly.

[http://ubuntuforums.org/showthread.php?t=491372](http://ubuntuforums.org/showthread.php?t=491372)

Made the new topic, because the problem is a bit different.

I can set 2 options:

Peer DNS trough tunnel
and only use vpn connection for these ...

but I know my ip, but not what's behind the /

---

### Post by Imposeren on 2007-07-09
connot connect to vpn.
Network manager says that there are no active networks:
```

NetworkManager: <WARNING>^I nm_vpn_manager_activate_vpn_connection (): nm_vpn_manager_activate_vpn_connection(): no currently active network device, won't activate VPN.
```


but ifconfig says:
```

eth0      Link encap:Ethernet  HWaddr 00:18:F3:75:92:43
          inet addr:10.*.*.*  Bcast:10.*.*.*  Mask:255.255.255.0
          inet6 addr: *** 4 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:21154 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4070 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:4342080 (4.1 MiB)  TX bytes:633701 (618.8 KiB)
          Interrupt:19
```


NetworkManager's vpn config:
```
[main]
Description=maket
Connection-Type=pptp
PPTP-Server=10.*.*.*
Use-Peer-DNS=no
Encrypt-MPPE=no
Encrypt-MPPE-128=yes
Compress-MPPC=no
Compress-Deflate=no
Compress-BSD=no
PPP-Lock=yes
Auth-Peer=no
Refuse-EAP=no
Refuse-CHAP=no
Refuse-MSCHAP=no
MTU=1416
MRU=1416
LCP-Echo-Failure=8
LCP-Echo-Interval=10
PPP-Custom-Options=
Peer-DNS-Over-Tunnel=no
X-NM-Routes=
Use-Routes=no

```


VPN server pptp config:
```
ipcp-accept-local
ipcp-accept-remote
lcp-echo-failure 10
lcp-echo-interval 30
require-mppe-128
require-mschap-v2
nobsdcomp
nodeflate
```


**Update:**
i solved my problem. I tried Network manager because I could'nt start vpn through default "pppd call  name" comand. I solved this problebm. It did'nt work because of wront MTU. changing it to prociders defaults helped

P.S. excuse me for my bad English

---

### Post by dupa on 2008-01-24
I cannot see "VPN Connections" in the menu.
If I delete eth0 from /etc/network/interfaces file, then I see VPN Connections and I can configure it.. but of course it doesn't work because i have not any connection to internet alive...

What shoud I do?

---

