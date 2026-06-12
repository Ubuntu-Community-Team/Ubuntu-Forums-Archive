---
title: "HELP!!! Problem in networking"
date: 2006-11-18
forum: Networking &amp; Wireless
---

### Post by ubuntpku on 2006-11-18
Recently i have installed dapper on my friend's laptop. At first it works fine. But after a re-install ( We made a stupid mistake which forced us to do so), the networking get into problem. 

All the configurations (we use DHCP) are exactly same as those in WinXP, but we cannot access any site on the internet. However, we can ping every PC in the same LAN successfully. 

I've spent weeks in persuading him to switch to ubuntu from M$ WinXP, so i really feel embarrassed.

PLEASE HELP!](*,) Any suggestion is appreciated!

---

### Post by bernied on 2006-11-18
I think you want to use the route command, to direct all IP traffic that isn't going to your local network through your router.

So first you need to know the IP of the router. If it were 192.168.0.1 then:

route add default gw 192.168.0.1

Maybe use 'via' instead of gw (gw=gateway). Sorry can't test this just now.

Also investigate ifconfig command.

---

### Post by mips on 2006-11-18
1. Please post output of **ifconfig eth0**  (Depends on your interface number)
2. Please post output of **lspci | grep Eth**
3. Please post output of **route -n**
4. Please post output of **cat /etc/resolv.conf**
5. Please post output of **cat /etc/network/interfaces**
6. Please post output of **cat /etc/dhcp3/dhclient.conf**
7. Please copy **entire** output of windows **ipconfig /all** command here

you might have to disbale IPv6 and also look at DNS but one step at a time.

---

### Post by k1001001 on 2006-11-18
I am having a very similar problem, though I think mine is even more complex. My laptop running Dapper runs fine on the LAN at school, but while I've been home this weekend, it has hardly worked at all. Normally, when I plug in my laptop to any ethernet port using CAT5 cable, it will work automatically, however this has not been the case at home.

Like the first user, I can ping any computer on the LAN, or even any site on the Internet, but I cannot access the actual site most of the time. If I play with the Network Manager enough, sometimes I can get working internet for about 30 seconds, and then it goes out again. I also cannot connect wirelessly to my home router because it uses WPA encryption, and I can't download any programs from the repository to activate WPA on my laptop.

My laptop specs:
Averatec 5400
CPU: AMD Athlon XP-M 1.6 Ghz
RAM: 1.0 GB
Originally had Windows XP, but it crashed (surprise) and now I am running Dapper. The laptop is a piece of junk, but I am trying to make do.

Here is the information you asked for:
```

ifconfig eth0
Link Encap:Ethernet HWaddr 00:40:CA:CE:DF:29
inet addr: 192.168.0.3 Bcast: 192.168.0.255 Mask: 255.255.255.0
inet6 addr: fe80::240:caff:fece:df29/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:1619 errors:0 dropped:0 overruns:0 frame:1
TX packets 2038 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:1039333 (1014.9 KiB) TX bytes:221700 (216.5 KiB)
Interrupt:177 Base address:0x1400

lspci | grep Eth
0000:00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)

route -n
Destination   Gateway  Genmask       Flags  Metric  Ref Use Iface
192.168.0.0   0.0.0.0  255.255.255.0  U      0       0  0   eth0
0.0.0.0    192.168.0.1 0.0.0.0        UG     0       0  0   eth0

cat /etc/resolv.conf
search domain.actdsltmp
nameserver 192.168.0.1
nameserver 192.168.0.1

cat /etc/network/interfaces
auto lo
iface lo inet loopback
auto eth0
iface eth0 inet dhcp
auto eth1
iface eth1 inet dhcp
auto eth2
iface eth2 inet dhcp
auto ath0
iface ath0 inet dhcp
auto wlan0
iface wlan0 inet dhcp
iface ra0 inet dhcp
wireless-essid ukyedu **(my college's wireless lan)**
auto ra0

cat etc/dhcp3/dhclient/conf
send host-name "andare.fugue.com";
send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
send dhcp-lease-time 3600;
supersede domain name "fugue.com home.vix.com";
prepend domain-name-servers 127.0.0.1;
request subnet-mask, broadcast-address, time-offset, routers,
 domain-name, domain-name-servers, host-name,
 netbios-name-servers, netbios-scope;
require subnet-maks, domain-name-servers;
timeout 60;
retry 60;
reboot 10;
select-timeout 5;
initial-interval 2;
script "etc/dhcp3/dhclient-script";
media "-link0 -link1 -link2", "link0 link1";
reject 192.33.137.203;
alias {
 interface "eth0";
 fixed address 192.5.5.213;
 option subnet-mask 255.255.255.255;
}
lease {
 interface "eth0";
 fixed-address 192.33.137.200;
 medium "link0 link1";
 option host-name "andare.swiftmedia.com";
 option subnet-mask 255.255.255.0
 option broadcast-address 192.33.137.255;
 option routers 192.33.137.250
 option domain-name-servers 127.0.0.1;
 renew 2 2000/1/12 00:00:01;
 rebind 2 2000/1/12 00:00:01;
 expire 2 2000/1/12 00:00:01;
}

And on Windows (the computer I'm typing from on the same LAN) running Win2000 Pro
Windows 2000 IP Configuration

        Host Name . . . . . . . . . . . . : fred-woqylr69m9
        Primary DNS Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Broadcast
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No
        DNS Suffix Search List. . . . . . : domain.actdsltmp
 Connection-specific DNS Suffix  . : domain.actdsltmp
 Description . . . . . . . . . . . : Intel(R) PRO/100 VE Network Connection
 Physical Address. . . . . . . . . : 00-03-47-A1-54-60
 DHCP Enabled. . . . . . . . . . . : Yes
 Autoconfiguration Enabled . . . . : Yes
 IP Address. . . . . . . . . . . . : 192.168.0.4
 Subnet Mask . . . . . . . . . . . : 255.255.255.0
 Default Gateway . . . . . . . . . : 192.168.0.1
 DHCP Server . . . . . . . . . . . : 192.168.0.1
 DNS Servers . . . . . . . . . . . : 192.168.0.1
                                     192.168.0.1
```

---

### Post by mips on 2006-11-19
> **k1001001 said:**
> I am having a very similar problem, though I think mine is even more complex. 

Everything looks ok. Could I suggest you disbale IPv6 globally & not just in firefox.

Secondly, get you ISPs primary & secondary DNS server IP addresses (from their website or call tech support) and insert them above the existing nameser entries in the resolv.conf file, nameserver *IP address*.

See if this makes a difference at all.

---

### Post by ubuntpku on 2006-11-19
Thank you all!:-D

But my friend has run out of his patience. We've reinstalled dapper early this morning (GMT+8) and everything goes well .

Really appreciate your help, dear mips and bernied.

Several people here also had this problem but they wouldn't like to solve it by reinstallation. So I'm still looking for the right solution.

I'll ask them to post what mips suggested.

---

### Post by trubblemaker on 2006-11-19
mips is on the money, unfortunately ipv6 doesn't play nice on some routers and edgy really get upset if it isn't correct.

to disable ipv6:

add "blacklist ipv6"
to /etc/modprobe.d/blacklist

---

### Post by ubuntpku on 2006-11-19
This is another case. He use a static IP address. The problem is same: he cannot visit any site on the Internet under ubuntu but can do in WinXP.


Hi, trubblemaker, i'll tell your idea to them. IPv6 may be a point. Thank you very much.:-D

```

1.ifconfig eth0
eth0 Link encap:Ethernet HWaddr 00:03:47:E9:40:0F
inet addr:172.31.16.109 Bcast:172.31.16.255 Mask:255.255.255.0
inet6 addr: fe80::203:47ff:fee9:400f/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:5629 errors:0 dropped:0 overruns:0 frame:0
TX packets:157 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:2112795 (2.0 MiB) TX bytes:20570 (20.0 KiB)

2.lspci | grep Eth
02:08.0 Ethernet controller: Intel Corporation 82801BA/BAM/CA/CAM Ethernet Controller (rev 03)

3.route -n
Kernel IP routing table
Destination Gateway Genmask Flags Metric Ref Use Iface
172.31.16.0 0.0.0.0 255.255.255.0 U 0 0 0 eth0
0.0.0.0 172.31.16.1 0.0.0.0 UG 0 0 0 eth0

4.cat /etc/resolv.conf
nameserver 172.16.1.139
nameserver 172.16.1.141

5.cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 172.31.16.109
netmask 255.255.255.0
gateway 172.31.16.1

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

6.cat /etc/dhcp3/dhclient.conf
# Configuration file for /sbin/dhclient, which is included in Debian's
# dhcp3-client package.
#
# This is a sample configuration file for dhclient. See dhclient.conf's
# man page for more information about the syntax of this file
# and a more comprehensive list of the parameters understood by
# dhclient.
#
# Normally, if the DHCP server provides reasonable information and does
# not leave anything out (like the domain name, for example), then
# few changes must be made to this file, if any.
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
# interface "eth0";
# fixed-address 192.5.5.213;
# option subnet-mask 255.255.255.255;
#}

#lease {
# interface "eth0";
# fixed-address 192.33.137.200;
# medium "link0 link1";
# option host-name "andare.swiftmedia.com";
# option subnet-mask 255.255.255.0;
# option broadcast-address 192.33.137.255;
# option routers 192.33.137.250;
# option domain-name-servers 127.0.0.1;
# renew 2 2000/1/12 00:00:01;
# rebind 2 2000/1/12 00:00:01;
# expire 2 2000/1/12 00:00:01;
#}

7.Under Windows :ipconfig /all
Windows IP Configuration

Host Name . . . . . . . . . . . . : rj-zhaoyiping1
Primary Dns Suffix . . . . . . . :
Node Type . . . . . . . . . . . . : Unknown
IP Routing Enabled. . . . . . . . : No
WINS Proxy Enabled. . . . . . . . : No

Ethernet adapter local:

Connection-specific DNS Suffix . :
Description . . . . . . . . . . . : Intel(R) PRO/100 VE Network Connection
Physical Address. . . . . . . . . : 00-03-47-E9-40-0F
Dhcp Enabled. . . . . . . . . . . : No
IP Address. . . . . . . . . . . . : 172.31.16.109
Subnet Mask . . . . . . . . . . . : 255.255.255.0
Default Gateway . . . . . . . . . : 172.31.16.1
DNS Servers . . . . . . . . . . . : 172.16.1.139
172.16.1.141
```

---

### Post by wieman01 on 2006-11-19
Deleted... Apologies.

---

### Post by k1001001 on 2006-11-20
If I disable IPv6, will that make Dapper work on all networks? And if so, then why was it there in the first place?

---

### Post by trubblemaker on 2006-11-20
It's complicated. IPv6 is going to be necessary in a couple of years. We'll eventually run out of ipv4.  It's not implemented properly on all networks, it's the network admins/(bad routers fault) and more often than not it's browsers like firefox, that don't handle badly done ipv6.  but as the default browser is firefox...  (you can just turn it off in firefox. But as you say if it doesn't work why is it installed?)
[For the official posting by ubuntu dev on ipv6 look here]("http://ubuntuforums.org/showpost.php?p=478267&postcount=8")


.

---

### Post by wieman01 on 2006-11-20
> **k1001001 said:**
> If I disable IPv6, will that make Dapper work on all networks? And if so, then why was it there in the first place?
Yes, it will by all means work on all networks. Why it is there is a very valid question, really. So far I have not found an answer. IPV6 has been implemented, however, has a few years to go before it  has any practical use or significance. IPV6 is the extension of IPV4 which basically covers the entire Internet (with a few exceptions). You are safe to disable it. It should be turned off by default as it is rarely used.

---

### Post by k1001001 on 2006-11-21
So I disabled IPv6 in this manner:
Terminal
sudo gedit /etc/modprobe.d/blacklist
And I added this line at the end of the blacklist file:
blacklist ipv6

This got Firefox to work perfectly, but Gaim is still not working. It works fine on this computer I'm using to type, which is connected to the same router. This is only a problem here at home, as I mentioned. Any suggestions?

EDIT: Also tried option 1 on post 4 of [this]("http://www.ubuntuforums.org/showthread.php?t=78337") thread, but no luck with Gaim either.

---

### Post by trubblemaker on 2006-11-22
Looks like time for a new thread. Sorry I dont have any helpful hints for you.  I might suggest using a more descriptive title than this forum. "HELP!" doesn't actually help people that are trying to help you.  But "Network problems ip but no webpages", would get people here real quick.  Not trying to rag on anyone just trying to educate.

---

### Post by ubuntpku on 2006-11-28
> **trubblemaker said:**
> Looks like time for a new thread. Sorry I dont have any helpful hints for you.  I might suggest using a more descriptive title than this forum. "HELP!" doesn't actually help people that are trying to help you.  But "Network problems ip but no webpages", would get people here real quick.  Not trying to rag on anyone just trying to educate.

I have been out these days. Sorry.

Thank you for your suggestions. I'll do it better next time.

Actually, a reinstallation of ubuntu solved this problem on my friend's laptop.(which cause the same problem described by me, but this time in winxp  instead)

Again, thank you all who helped me.:)

---

