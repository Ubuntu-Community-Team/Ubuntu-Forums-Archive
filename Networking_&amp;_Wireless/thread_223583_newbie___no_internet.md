---
title: "newbie _ no internet"
date: 2006-07-26
forum: Networking &amp; Wireless
---

### Post by meirbenezra on 2006-07-26
ok I checked out many different posts but first of all couldnt understand many of the things written. I'm using ubuntu and xp dual boot and writing all these from xp. The problem is my ubuntu doesnt recognize my internet nor network. When I used the live cd everything worked fine. But when I installed it suddenly network stopped working. I cannot even connect to my modems ip address. it cannot find any other pcs in windows network even though two are connected. I read this one about ip6 I tried it didnt work. I need a solution. I think ubuntu is the right distro for me the only (big) problem is network...

---

### Post by Ziox on 2006-07-26
did you activate the card? from Ubuntu i mean, go to System => Admin. => Network, and see if the card is activated.

---

### Post by meirbenezra on 2006-07-26
yeah the system recognized the ip of my modem eth0 is activated but when I look at the status it always gives packet recieving errors
thereis one thing called networking tools or sth like that there I think was these info given and the eroors just keep increasing. whereas the live cd worked just fine but slow of course and I want ubuntu to be installed on my pc...

---

### Post by mips on 2006-07-27
My standard response follows:

What hardware are you using, modem/router model etc ???
How is the above hardware configured ???

[http://doc.gwos.org/index.php/DisableIPV6](http://doc.gwos.org/index.php/DisableIPV6)
[http://www.ubuntuforums.org/showthread.php?t=78337](http://www.ubuntuforums.org/showthread.php?t=78337) 

1. Please post output of **ifconfig eth0**  (Depends on your interface number)
2. Please post output of **lspci | grep Eth**
3. Please post output of **route -n**
4. Please post output of **cat /etc/resolv.conf**
5. Please post output of **cat /etc/network/interfaces**
6. Please post output of **cat /etc/dhcp3/dhclient.conf**
7. Please copy **entire** output of windows **ipconfig /all** command here
8. Who is your ISP and provide a web link.

---

### Post by The_Observer on 2006-07-28
Hi there,

I'm also facing the same problem. I couldn't connect to the network... And also internet. My computer is connected to the internet through a home network. I'm using Nvidia onboard ethernet adapter and heard that Nvidia ethernet have a lot of problems. 

Forgot to mention, I'm totally new to linux base OS. I did try to edit /etc/network/interfaces but fail since I'm not root user. I'm totally confused on how to login as root. Without logging as root, I can't modify anything. Really hope to get some help. Currently still using windows (dual boot). I really hope to use fully linux once I'm a so called expert :p 

By the way, any ideas on how to copy the output from Ubuntu to be pasted here? Thanks...

---

### Post by jayant on 2006-07-28
> **The_Observer said:**
> 
Forgot to mention, I'm totally new to linux base OS. I did try to edit /etc/network/interfaces but fail since I'm not root user. I'm totally confused on how to login as root. Without logging as root, I can't modify anything. Really hope to get some help. Currently still using windows (dual boot). I really hope to use fully linux once I'm a so called expert :p

use sudo
for example to run ifconfig type:
sudo ifconfig <then it'll prompt for your password>
to edit interfaces type:
sudo vi /etc/network/interfaces

hope it helps

---

### Post by The_Observer on 2006-07-28
> use sudo
for example to run ifconfig type:
sudo ifconfig <then it'll prompt for your password>
to edit interfaces type:
sudo vi /etc/network/interfaces

Thanks.... Will try ASAP... Very fast response :KS  Btw, any ideas on how to configure my network?

---

### Post by eXisor on 2006-07-28
It could also be that your system is using both 'dfme' and 'tulip'.
Do a 'lsmod', and if both are listed, you have the problem. (It happens on davicom chipset based network cards).

If so, edit the /etc/modprobe.d/blacklist file and add tulip at the bottom. Restart and you should just be using the dfme driver.

---

### Post by The_Observer on 2006-07-28
> 1. Please post output of ifconfig eth0 (Depends on your interface number)
2. Please post output of lspci | grep Eth
3. Please post output of route -n
4. Please post output of cat /etc/resolv.conf
5. Please post output of cat /etc/network/interfaces
6. Please post output of cat /etc/dhcp3/dhclient.conf
7. Please copy entire output of windows ipconfig /all command here
8. Who is your ISP and provide a web link.

Here's the info when I use DHCP...

```
theobserver@theobserver:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:E0:4C:FA:EC:D6
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:51 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:225 Base address:0x4000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:31 errors:0 dropped:0 overruns:0 frame:0
          TX packets:31 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2592 (2.5 KiB)  TX bytes:2592 (2.5 KiB)

theobserver@theobserver:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
theobserver@theobserver:~$ lspci | grep Eth
0000:00:08.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
theobserver@theobserver:~$ cat /etc/resolv.conf
nameserver 192.168.1.1
domain MSHOME
theobserver@theobserver:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.7
netmask 255.255.255.0
gateway 192.168.1.1

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

theobserver@theobserver:~$ cat /etc/dhcp3/dhclient.conf
# Configuration file for /sbin/dhclient, which is included in Debian's
#       dhcp3-client package.
#
# This is a sample configuration file for dhclient. See dhclient.conf's
#       man page for more information about the syntax of this file
#       and a more comprehensive list of the parameters understood by
#       dhclient.
#
# Normally, if the DHCP server provides reasonable information and does
#       not leave anything out (like the domain name, for example), then
#       few changes must be made to this file, if any.
#

#send host-name "andare.fugue.com";
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
#prepend domain-name-servers 127.0.0.1;
request subnet-mask, broadcast-address, time-offset, routers,
        domain-name, domain-name-servers, host-name,
        netbios-name-servers, netbios-scope;
#require subnet-mask, domain-name-servers;
#timeout 60;
#retry 60;
#reboot 10;
#select-timeout 5;
#initial-interval 2;
#script "/etc/dhcp3/dhclient-script";
#media "-link0 -link1 -link2", "link0 link1";
#reject 192.33.137.209;

#alias {
#  interface "eth0";
#  fixed-address 192.5.5.213;
#  option subnet-mask 255.255.255.255;
#}

#lease {
#  interface "eth0";
#  fixed-address 192.33.137.200;
#  medium "link0 link1";
#  option host-name "andare.swiftmedia.com";
#  option subnet-mask 255.255.255.0;
#  option broadcast-address 192.33.137.255;
#  option routers 192.33.137.250;
#  option domain-name-servers 127.0.0.1;
#  renew 2 2000/1/12 00:00:01;
#  rebind 2 2000/1/12 00:00:01;
#  expire 2 2000/1/12 00:00:01;
#}
```

and here's for static ip...

```
theobserver@theobserver:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:E0:4C:FA:EC:D6
          inet addr:192.168.1.7  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:57 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:698 (698.0 b)  TX bytes:0 (0.0 b)
          Interrupt:225 Base address:0x4000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:32 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2680 (2.6 KiB)  TX bytes:2680 (2.6 KiB)

theobserver@theobserver:~$ lspci | grep Eth
0000:00:08.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
theobserver@theobserver:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
theobserver@theobserver:~$ cat /etc/resolv.conf
nameserver 192.168.1.1
domain MSHOME
theobserver@theobserver:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.7
netmask 255.255.255.0
gateway 192.168.1.1

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

theobserver@theobserver:~$ cat /etc/dhcp3/dhclient.conf
# Configuration file for /sbin/dhclient, which is included in Debian's
#       dhcp3-client package.
#
# This is a sample configuration file for dhclient. See dhclient.conf's
#       man page for more information about the syntax of this file
#       and a more comprehensive list of the parameters understood by
#       dhclient.
#
# Normally, if the DHCP server provides reasonable information and does
#       not leave anything out (like the domain name, for example), then
#       few changes must be made to this file, if any.
#

#send host-name "andare.fugue.com";
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
#prepend domain-name-servers 127.0.0.1;
request subnet-mask, broadcast-address, time-offset, routers,
        domain-name, domain-name-servers, host-name,
        netbios-name-servers, netbios-scope;
#require subnet-mask, domain-name-servers;
#timeout 60;
#retry 60;
#reboot 10;
#select-timeout 5;
#initial-interval 2;
#script "/etc/dhcp3/dhclient-script";
#media "-link0 -link1 -link2", "link0 link1";
#reject 192.33.137.209;

#alias {
#  interface "eth0";
#  fixed-address 192.5.5.213;
#  option subnet-mask 255.255.255.255;
#}

#lease {
#  interface "eth0";
#  fixed-address 192.33.137.200;
#  medium "link0 link1";
#  option host-name "andare.swiftmedia.com";
#  option subnet-mask 255.255.255.0;
#  option broadcast-address 192.33.137.255;
#  option routers 192.33.137.250;
#  option domain-name-servers 127.0.0.1;
#  renew 2 2000/1/12 00:00:01;
#  rebind 2 2000/1/12 00:00:01;
#  expire 2 2000/1/12 00:00:01;
#}
```

While this is from windows...

```
Windows IP Configuration

        Host Name . . . . . . . . . . . . : MusafirKelana
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Unknown
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No

Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : NVIDIA nForce Networking Controller
        Physical Address. . . . . . . . . : 00-E0-4C-FA-EC-D6
        Dhcp Enabled. . . . . . . . . . . : No
        IP Address. . . . . . . . . . . . : 192.168.1.7
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.1.1
        DNS Servers . . . . . . . . . . . : 192.168.1.1
```

By the way, I connect through a 8 port switch which is connected to a D-link DSL-500T.

Also, sorry bcoz I don't really understand this,

>  	It could also be that your system is using both 'dfme' and 'tulip'.
Do a 'lsmod', and if both are listed, you have the problem. (It happens on davicom chipset based network cards).

If so, edit the /etc/modprob.d/blacklist file and add tulip at the bottom. Restart and you should just be using the dfme driver.

I open the blacklist file, it was empty...

Hope to get help from you guys. Thanks ;)

---

### Post by HorseloverFat on 2006-07-28
> **The_Observer said:**
> Also, sorry bcoz I don't really understand this,



I open the blacklist file, it was empty...

What he's telling you to do is, open up a terminal and type *lsmod*. Go through the list and check if both dfme and tulip are in it. If they both are, add *tulip* to the aforementioned blacklist file.

I'm having similar network problems with my nforce network adaptor. I installed Ubuntu tonight, and although it is "activated" (and presumably therefore should be working), it isn't. 

The confusing thing is, it was working fine in Fedora, until suddenly it stopped and refused to activate. This was a couple of days ago.

---

### Post by meirbenezra on 2006-07-28
I'm writing this post from my ubuntu :) I'm so happy noww that my internet works and my whole network... The solution was to blacklist tulip. If you guys use davicom chipset ethernet cards really try this it worked for mee thx for everyone helping out..

---

### Post by eXisor on 2006-07-29
Glad to be of assistance.

---

### Post by mips on 2006-07-30
[The_Observer]("http://www.ubuntuforums.org/member.php?u=141665"),

Can you ping your router from the PC when using a static config ?

---

### Post by The_Observer on 2006-07-30
Hi there,

Well, guess what? I'm now writing from my Ubuntu. Just got the internet working after buying a new D-link ethernet card. Well, Nvidia ethernet is a real pain... Thanks for the help anyway :D

---

