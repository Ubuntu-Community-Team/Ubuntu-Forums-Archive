---
title: "ipv6 problem (internet via ADSL)"
date: 2006-07-30
forum: Networking &amp; Wireless
---

### Post by rupesh on 2006-07-30
hello all,

  one day before i installed Dapper 6.06. everything was fine with some installation problems. 
 then came this big ipv6 isuue. it is still not solved completely. i was partially able to solve this.
  problem is like this---
 i have D-link DSL-502T ADSL router/modem connected via ehternet. which do not support ipv6. hence i disabled mozilla ipv6 settings, as well as modified /etc/modprobe.d/aliases.
 as stated in following post-- (4th post by mips)
  
[http://www.ubuntuforums.org/showthread.php?t=78337](http://www.ubuntuforums.org/showthread.php?t=78337) 

after this my mozilla start working very finely but i was not able to connect via synaptic or any other application like Gaim messenger.

so i did further searching and found one more post. :-

[http://www.ubuntuforums.org/showthread.php?t=222817](http://www.ubuntuforums.org/showthread.php?t=222817)
(4th post by blitz)

so i created /etc/modprobe.d/blacklist-ipv6 file with said content. and now i dont get any ipv6 modules present.
by giving command :-

lsmod | grep ipv6

 after rebooting still i am not able to connect to internet via synaptic or any other application except mozilla..
 so can anyone plzz help..
 i am giving all my system information and other required info for further debugging..
 thanks in advance...

output of ifconfig eth0:-
eth0      Link encap:Ethernet  HWaddr 00:14:85:44:7B:C2
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3227 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2933 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:3318271 (3.1 MiB)  TX bytes:380304 (371.3 KiB)
          Interrupt:201 Base address:0xa000

output of lspci | grep Eth :-
0000:01:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

output of route -n:-
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0

output of cat /etc/resolv.conf:-
nameserver 192.168.1.1

cat /etc/network/interfaces:-
auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


iface dsl-provider inet ppp
provider dsl-provider

auto eth0

output of cat /etc/dhcp3/dhclient.conf:-
eth0      Link encap:Ethernet  HWaddr 00:14:85:44:7B:C2
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3227 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2933 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:3318271 (3.1 MiB)  TX bytes:380304 (371.3 KiB)
          Interrupt:201 Base address:0xa000

rupesh@rupesh-desktop:~$ lspci | grep Eth
0000:01:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
rupesh@rupesh-desktop:~$
rupesh@rupesh-desktop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
rupesh@rupesh-desktop:~$ cat /etc/resolv.conf
nameserver 192.168.1.1
rupesh@rupesh-desktop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


iface dsl-provider inet ppp
provider dsl-provider

auto eth0
rupesh@rupesh-desktop:~$
rupesh@rupesh-desktop:~$ cat /etc/dhcp3/dhclient.conf
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

this is my ISP providers web address:-
[http://mumbai.mtnl.net.in/triband/](http://mumbai.mtnl.net.in/triband/)[COLOR="Black"]****[/COLOR]

---

### Post by mips on 2006-07-30
Can you ping 192.168.1.1 ?
Can you ping 198.133.219.25 ?

---

### Post by rupesh on 2006-07-30
hey i can ping 192.168.1.1
 but i dont think i can ping to 192.133.219.25.
 this is my output:---------

rupesh@rupesh-desktop:~$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=255 time=0.723 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=255 time=0.590 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=255 time=0.584 ms
64 bytes from 192.168.1.1: icmp_seq=4 ttl=255 time=0.588 ms
64 bytes from 192.168.1.1: icmp_seq=5 ttl=255 time=0.608 ms
64 bytes from 192.168.1.1: icmp_seq=6 ttl=255 time=0.589 ms
64 bytes from 192.168.1.1: icmp_seq=7 ttl=255 time=0.587 ms
64 bytes from 192.168.1.1: icmp_seq=8 ttl=255 time=0.593 ms
64 bytes from 192.168.1.1: icmp_seq=9 ttl=255 time=0.587 ms
64 bytes from 192.168.1.1: icmp_seq=10 ttl=255 time=0.618 ms
64 bytes from 192.168.1.1: icmp_seq=11 ttl=255 time=0.602 ms
64 bytes from 192.168.1.1: icmp_seq=12 ttl=255 time=0.611 ms
64 bytes from 192.168.1.1: icmp_seq=13 ttl=255 time=0.599 ms
64 bytes from 192.168.1.1: icmp_seq=14 ttl=255 time=0.609 ms

[2]+  Stopped                 ping 192.168.1.1
rupesh@rupesh-desktop:~$ ping 192.133.219.25
PING 192.133.219.25 (192.133.219.25) 56(84) bytes of data.
From 220.227.119.54 icmp_seq=9 Destination Net Unreachable
From 220.227.119.54 icmp_seq=19 Destination Net Unreachable
From 220.227.119.54 icmp_seq=20 Destination Net Unreachable
From 220.227.119.54 icmp_seq=29 Destination Net Unreachable
From 220.227.119.54 icmp_seq=39 Destination Net Unreachable
From 220.227.119.54 icmp_seq=49 Destination Net Unreachable
From 220.227.119.54 icmp_seq=59 Destination Net Unreachable
From 220.227.119.54 icmp_seq=60 Destination Net Unreachable
From 220.227.119.54 icmp_seq=69 Destination Net Unreachable
From 220.227.119.54 icmp_seq=79 Destination Net Unreachable
From 220.227.119.54 icmp_seq=89 Destination Net Unreachable
From 220.227.119.54 icmp_seq=99 Destination Net Unreachable
From 220.227.119.54 icmp_seq=109 Destination Net Unreachable
From 220.227.119.54 icmp_seq=119 Destination Net Unreachable
From 220.227.119.54 icmp_seq=129 Destination Net Unreachable
From 220.227.119.54 icmp_seq=139 Destination Net Unreachable

[3]+  Stopped                 ping 192.133.219.25
rupesh@rupesh-desktop:~$

---

### Post by mips on 2006-07-30
> **rupesh said:**
> 
[2]+  Stopped                 ping 192.168.1.1
rupesh@rupesh-desktop:~$ ping 192.133.219.25
PING 192.133.219.25 (192.133.219.25) 56(84) bytes of data.
From [COLOR=Red]**220.227.119.54**[/COLOR] icmp_seq=9 Destination Net Unreachable


Ok, connectivity to your router is fine.
Who is 220.227.119.54 ??? This is a box on the internet somewhere saying to your PC it cannot reach 192.133.219.25
[http://www.schwarzl.com/ipcheck.html?action=query&ip1=220&ip2=227&ip3=119&ip4=54](http://www.schwarzl.com/ipcheck.html?action=query&ip1=220&ip2=227&ip3=119&ip4=54)

Which I find weird, browsing works but no other stuff. Maybe ask your ISP about this. Does everything work under windows ?

---

### Post by rupesh on 2006-07-30
yup i got who is 220.227.119.54
 this is one big telecom company in india. dont have any idea of how i got their ip. as i am not subscriber of this. so what to do now? 
 output of 220.227.119.54--------------

 	

Put in the tcp/ip number you are searching for:



Response from whois.apnic.net:
% [whois.apnic.net node-1]
% Whois data copyright terms [http://www.apnic.net/db/dbcopyright.html](http://www.apnic.net/db/dbcopyright.html)

inetnum: 220.224.0.0 - 220.227.255.255
netname: RelianceInfocomm
descr: Reliance Infocom Ltd
country: IN
admin-c: BN96-AP
tech-c: SC1210-AP
tech-c: CL1307-AP
status: ALLOCATED PORTABLE
notify: [email]Antiabuse.support@Relianceinfo.com[/email]
mnt-by: APNIC-HM
mnt-lower: MAINT-IN-SN
changed: [email]hm-changed@apnic.net[/email] 20040301
changed: [email]hm-changed@apnic.net[/email] 20060208
changed: [email]hm-changed@apnic.net[/email] 20060404
source: APNIC

route: 220.227.119.0/24
descr: Reliance Infocomm Ltd
origin: AS18101
mnt-by: MAINT-IN-SN
changed: [email]ip.nnoc@relianceinfo.com[/email] 20060405
source: APNIC
country: IN

person: B Nagaraj
nic-hdl: BN96-AP
remarks: Send spam & abuse Reports
remarks: include detailed information & time
remarks: to [email]antiabuse.support@relianceada.com[/email]
e-mail: [email]ricip.admin@relianceada.com[/email]
address: Reliance Communication Ventures Ltd,
address: 2CA 13 , D Block , 2nd Floor,
address: Dhirubai Ambani Knowledge City,
address: Thane Belapur Road, KoparKhairne,
address: Navi Mumbai - 400710 , INDIA.
phone: +91-22-30383796
fax-no: +91-22-30383899
country: IN
changed: [email]ricip.admin@relianceada.com[/email] 20060613
mnt-by: MAINT-IN-SN
source: APNIC

person: Shankha Chaudhuri
nic-hdl: SC1210-AP
remarks: Send spam & abuse Reports
remarks: include detailed information & time
remarks: to [email]antiabuse.support@relianceada.com[/email]
e-mail: [email]ricip.admin@relianceada.com[/email]
address: Reliance Communication Ventures Ltd,
address: 2W14 , DB 17 , D Block , 2nd Floor,
address: Dhirubai Ambani Knowledge City,
address: Thane Belapur Road, KoparKhairne,
address: Navi Mumbai - 400710 , INDIA.
phone: +91-22-30383936
fax-no: +91-22-30383899
country: IN
changed: [email]ricip.admin@relianceada.com[/email] 20060613
mnt-by: MAINT-IN-SN
source: APNIC

person: Cavin Lobo
nic-hdl: CL1307-AP
remarks: Send spam & abuse Reports
remarks: include detailed information & time
remarks: to [email]antiabuse.support@relianceada.com[/email]
e-mail: [email]ricip.admin@relianceada.com[/email]
address: Reliance Communication Ventures Ltd,
address: 3W24, Block-D,
address: DAKC, Kopar khairne,
address: Navi Mumbai 400 709
phone: +91-22-30383851
fax-no: +91-22-30383899
country: IN
changed: [email]ricip.admin@relianceada.com[/email] 20060613
mnt-by: MAINT-IN-SN
source: APNIC

---

### Post by rupesh on 2006-07-30
things do work pretty fine with windows XP. with no problem at all. can u suggest any solution?

---

### Post by mips on 2006-07-30
Please check that your router is properly configured.
[http://www.schwarzl.com/ipcheck.html?action=query&ip1=220&ip2=227&ip3=119&ip4=54](http://www.schwarzl.com/ipcheck.html?action=query&ip1=220&ip2=227&ip3=119&ip4=54)
[http://mumbai.mtnl.net.in/triband/htm/statip_d.pdf](http://mumbai.mtnl.net.in/triband/htm/statip_d.pdf)
Also ensure your D-Link has the latest firmware , [http://www.dlink.co.in/dlink/Drivers/view.asp?tab=DSL-502T](http://www.dlink.co.in/dlink/Drivers/view.asp?tab=DSL-502T)

---

### Post by rupesh on 2006-07-30
I dont know much abt router configuration and router is preconfigured by the ISP provider (as i had got it from ISP provider itself). so i hope it is properly configured. 
 only thing is i had not updated to recent firmware. from D-link.
 so what will u suggest? should i give a chance by upgrading firmware? and i am concerned whether after doing so it will again work properly (at least the way it is working now ?)
 thank u for ur quick response. and all help

---

### Post by rupesh on 2006-07-30
hello can i ask one thing?
 from where u got ip address 198.133.219.25?
 i dont see any reference anywhere in my posting? and why u asked me to pinge 198.133.219.25?

---

### Post by mips on 2006-07-30
> **rupesh said:**
> hello can i ask one thing?
 from where u got ip address 198.133.219.25?
 i dont see any reference anywhere in my posting? and why u asked me to pinge 198.133.219.25?

No there won't be any reference to it in your posting, it is the ip address for [www.cisco.com](www.cisco.com).

---

### Post by CVDpr on 2006-07-31
I have the same problem here.. and still waiting..

Only Firefox connect but not update, Gaim ect...

---

### Post by rupesh on 2006-07-31
ok mips i will give a try by upgrading firmware and reconfiguring router..
 and get back with results. 
 regards

---

### Post by mips on 2006-07-31
> **CVDpr said:**
> I have the same problem here.. and still waiting..

Only Firefox connect but not update, Gaim ect...

Stop waiting and start looking for a solution ;)

---

### Post by rupesh on 2006-07-31
hello mips,
 its latest firmware which is already installed on my router. i checked with tech support of d-link. so what next? any other suggestions?
 regards

---

### Post by rupesh on 2006-07-31
what does output of this command means?

$ip -6 route
192.168.1.0/24 dev eth0  proto kernel  scope link  src 192.168.1.3
default via 192.168.1.1 dev eth0

---

### Post by robek on 2006-07-31
I have the same problem with exactly the same router...
How do you disable IPv6?
I've changed /etc/modprobe.d/aliases to alias net-pf-10 off
and created bad_list file containing 
alias net-pf-10 off
is there anything else that should be done to disable it?

---

### Post by mips on 2006-07-31
> **robek said:**
> I have the same problem with exactly the same router...
How do you disable IPv6?
I've changed /etc/modprobe.d/aliases to alias net-pf-10 off
and created bad_list file containing 
alias net-pf-10 off
is there anything else that should be done to disable it?

Another way is to rename the module.

---

### Post by mips on 2006-07-31
> **rupesh said:**
> what does output of this command means?

$ip -6 route
192.168.1.0/24 dev eth0  proto kernel  scope link  src 192.168.1.3
default via 192.168.1.1 dev eth0

Something to the effect that you have network 192.168.1.0 with mask 255.255.255.0 on the eth0 device, source address has a default route via 192.168.1.1 device eth0

Maybe have a look at your ehternet card, there has been some issues with the 8139 in the past. Have you got a spare card to test with ?

---

### Post by rupesh on 2006-07-31
i again summarizes the problem, i have dapper installed and after readind all stuff to disable ipv6 i tried following steps:-
 1) disabled ipv6 in mozilla
 2) changed /etc/modprobe.d/aliases
 3) creating badlist file.
 4) creating blacklist-ipv6 file.
 
 now i dont get any modules loaded by 
 ip a | grep inet6
     or 
 lsmod | grep ipv6

after all this i am able to use mozilla. but still unable to connect using synaptic or gaim etc..
 can anyone plzz help me for fixing this problem? 

 
 thanks and regards

---

### Post by rupesh on 2006-07-31
:sad: the ethernet card is onboard (Gigabyte 845 intel chipset ).. and i dont have any spare card to test..? but how mozilla can connect and not other applications? 
 
 :---) i am geting frustrated now.....:sad:

---

### Post by robek on 2006-07-31
looks like D-Link is not compatible with Linux...
solution I found on some FreeBSD forum was to copile a IPv4-only kernel
not that I know how to do that or if it can be done with Ubuntu :)
so perhaps getting a new router is the easiest way

---

### Post by mips on 2006-07-31
Have you got any proxies setup on your PC ?

I dunno if traceroute is available on the install cd but if you edit your sources list maybe try and install traceroute. The do a traceroute to 198.133.219.25, it should give an indication of where things get stuck.

Just to confirm, you can browse any website via mozilla firefox, ie. [www.bt.co.uk](www.bt.co.uk) but no other applications have net access ?

---

### Post by mips on 2006-07-31
> **robek said:**
> looks like D-Link is not compatible with Linux...
solution I found on some FreeBSD forum was to copile a IPv4-only kernel
not that I know how to do that or if it can be done with Ubuntu :)
so perhaps getting a new router is the easiest way

Not all DLinks have the problem and usually disabling IPv6 or loading v2 firmware sorts the issue out on those that do have an issue.

---

### Post by mips on 2006-07-31
> **rupesh said:**
> but how mozilla can connect and not other applications? 
 
 :---) i am geting frustrated now.....:sad:

A valid point but you see some strange things sometimes.

You are not the only one getting frustrated ](*,)

Another thing you can try is changing your mtu setting to 1492 or smaller.

---

### Post by rupesh on 2006-07-31
all right mips this is what u want o/p of traceroute:--

rupesh@rupesh-desktop:~$ traceroute 198.133.219.25
traceroute to 198.133.219.25 (198.133.219.25), 30 hops max, 40 byte packets
 1  * * *
 2  triband-mum-59.184.63.254.mtnl.net.in (59.184.63.254)  14.369 ms  15.499 ms  14.918 ms
 3  triband-mum-59.185.0.97.mtnl.net.in (59.185.0.97)  17.090 ms  14.188 ms  14. 682 ms
 4  59.160.0.138.static.vsnl.net.in (59.160.0.138)  228.783 ms  224.434 ms  227. 020 ms
 5  vsb-lvsb-gig.Bbone.vsnl.net.in (202.54.2.22)  227.002 ms  226.109 ms  226.56 9 ms
 6  nny-mum-3rd-stm1.Bbone.vsnl.net.in (202.54.2.14)  243.763 ms  242.656 ms  24 3.654 ms
 7  GigabitEthernet1-1.IG5.NYC4.ALTER.NET (208.192.178.117)  228.384 ms  227.656  ms  226.855 ms
  8  0.so-7-1-3.XL4.NYC4.ALTER.NET (152.63.35.38)  226.720 ms  227.412 ms  227.0 25 ms
 9  0.so-1-1-0.XL2.SJC2.ALTER.NET (152.63.50.58)  293.295 ms  292.357 ms  292.833 ms
10  POS1-0.XR2.SJC2.ALTER.NET (152.63.56.142)  288.355 ms  287.332 ms  287.936 ms
11  192.ATM6-0.GW5.SJC2.ALTER.NET (152.63.48.81)  293.297 ms  293.772 ms  294.841 ms
12  ciscosys-gw1.customer.alter.net (65.208.80.242)  288.400 ms  288.838 ms  288.142 ms
13  sjce-dmzbb-gw1.cisco.com (128.107.239.89)  293.288 ms  292.486 ms  292.869 ms
14  sjck-dmzdc-gw2.cisco.com (128.107.224.73)  286.912 ms  285.648 ms  286.582 ms
15  * * *
16  * * *
17  * * *
18  * * *
19  * * *
20  * * *
21  * * *
22  * * *
23  * * *
24  * * *
25  * * *
26  * * *
27  * * *
28  * * *
29  * * *
30  * * *
rupesh@rupesh-desktop:~$

---

### Post by rupesh on 2006-07-31
hey mips.. whats this mtu setting and how to change it?
 let me try out that thing too if  u can't find out any solution out of traceroute... plz.... keep this post alive.. untill we find some solution..
 regards

---

### Post by mips on 2006-07-31
Ok, thats good news. You are getting past your ISP all the way to Cisco's  firewall/DMZ and you wont see anything beyond that. You have internet connectivity in other words.

Are you sure there are no proxies configured under system menu some where ?

Does a traceroute to the hostname [www.cisco.com](www.cisco.com) work ?

---

### Post by mips on 2006-07-31
> **rupesh said:**
> hey mips.. whats this mtu setting and how to change it?
 let me try out that thing too if  u can't find out any solution out of traceroute... plz.... keep this post alive.. untill we find some solution..
 regards

To change mtu to 1492 (or lower) see:

[http://ubuntuforums.org/showthread.php?t=82093](http://ubuntuforums.org/showthread.php?t=82093)
[http://www.ubuntuforums.org/showthread.php?t=104371](http://www.ubuntuforums.org/showthread.php?t=104371)

---

### Post by mips on 2006-07-31
You can also edit your
/etc/resolv.conf file to
```
 nameserver 203.94.227.70
nameserver 203.94.227.70
#nameserver 192.168.1.1
```

and see if it helps at all.

---

### Post by rupesh on 2006-07-31
this is my stand alone desktop system and i had installed dapper freshly. (so no proxy setting) still i checked out system-> Preferences->Network proxy
  it is marked as Direct internet connection 
so no firewall thats for sure
 here is o/p of tracerout [www.cisco.com:--](www.cisco.com:--)

rupesh@rupesh-desktop:~$  traceroute [www.cisco.com](www.cisco.com)
traceroute to [www.cisco.com](www.cisco.com) (198.133.219.25), 30 hops max, 40 byte packets
 1  * * *
 2  triband-mum-59.184.63.254.mtnl.net.in (59.184.63.254)  15.515 ms  15.528 ms  14.942 ms
 3  triband-mum-59.185.0.97.mtnl.net.in (59.185.0.97)  14.720 ms  14.184 ms  14.993 ms
 4  59.160.0.138.static.vsnl.net.in (59.160.0.138)  226.753 ms  226.110 ms  226.651 ms
 5  vsb-lvsb-gig.Bbone.vsnl.net.in (202.54.2.22)  228.909 ms  227.853 ms  226.825 ms
 6  nny-mum-3rd-stm1.Bbone.vsnl.net.in (202.54.2.14)  243.575 ms  242.657 ms  245.292 ms
 7  GigabitEthernet1-1.IG5.NYC4.ALTER.NET (208.192.178.117)  228.432 ms  226.142 ms  226.813 ms
 8  0.so-7-1-3.XL4.NYC4.ALTER.NET (152.63.35.38)  226.973 ms  225.867 ms  228.874 ms
 9  0.so-1-1-0.XL2.SJC2.ALTER.NET (152.63.50.58)  292.938 ms  292.114 ms  293.182 ms
10  POS1-0.XR2.SJC2.ALTER.NET (152.63.56.142)  288.234 ms  287.192 ms  286.220 ms
11  192.ATM6-0.GW5.SJC2.ALTER.NET (152.63.48.81)  293.630 ms  292.372 ms  293.106 ms
12  ciscosys-gw1.customer.alter.net (65.208.80.242)  288.430 ms  285.758 ms  286.441 ms
13  sjce-dmzbb-gw1.cisco.com (128.107.239.89)  293.264 ms  290.557 ms  292.856 ms
14  sjck-dmzdc-gw2.cisco.com (128.107.224.73)  286.619 ms  285.759 ms  288.140 ms
15  * * *
16  * * *
17  * * *
18  * * *
19  * * *
20  * * *
21  * * *
22  * * *
23  * * *
24  * * *
25  * * *
26  * * *
27  * * *
28  * * *
29  * * *
30  * * *
rupesh@rupesh-desktop:~$

---

### Post by mips on 2006-07-31
To see if you have any proxies configured go to System->Preferences->Proxy settings  (That was the place in Breezy anyway)

---

### Post by rupesh on 2006-07-31
> **mips said:**
> You can also edit your
/etc/resolv.conf file to
```
 nameserver 203.94.227.70
nameserver 203.94.227.70
#nameserver 192.168.1.1
```

and see if it helps at all.

:D :D :D :D HEYYYYYYYYYYYYY  IT WORKED WITH ABOVE POST.....:D :D :D 
               THANKS MIPS U R REALLY GENIUS
       THANKS FOR ALL HELP AND SUPPORT KEEP THIS GOOD WORK DOING

---

### Post by mips on 2006-07-31
You are using DHCP and it will probably overwrite that config with the next reboot.

Reboot and check if that file has changed back to it's original state ?

I still can't understand how the web browsing worked but not the other stuff.

---

### Post by rupesh on 2006-07-31
thanks a lot ,mips...  at least making my synaptic work...
   yes u r right...
 it is rewriting the file...
 so what's solution on this?????????????:eek:

---

### Post by rupesh on 2006-07-31
:d

---

### Post by mips on 2006-07-31
You can disbale DHCP and use a Static IP configuration in your interfaces file or you can look at these two threads:

Post#17-  [http://www.ubuntuforums.org/showpost.php?p=720539](http://www.ubuntuforums.org/showpost.php?p=720539)
Post#01- [http://www.ubuntuforums.org/showthread.php?t=221404](http://www.ubuntuforums.org/showthread.php?t=221404)

Another option would be to manually specify those two dns server addresses in your router and see if it passes it on to your pc in which case you dont have to change anything on the pc.

---

### Post by rupesh on 2006-07-31
all right mips..
 i will definately give a try for it.. and get back with results..
 i will definately post my results after this.. but now its time to go..
 thanks for all help once again...
 may god bless u..:D

---

### Post by robek on 2006-07-31
Call me thick...
but where do you get 203.94.227.70 from?
I guess I should use something different... ;)

---

### Post by mips on 2006-07-31
> **robek said:**
> Call me thick...
but where do you get 203.94.227.70 from?
I guess I should use something different... ;)

Visit your ISP's website or call them and find out what the IP Addresses are for their primary & secondary DNS servers. Can usually be found in the documentation/support sections.

---

### Post by robek on 2006-07-31
It works!!!
mips you're great!!!
thanks a lot!

---

### Post by markmark on 2006-07-31
I just saw this thread, I had this exact problem with a d-link router, it didn't pass on the nameservers. If I manually specified them in /etc/resolv.conf they just got overwritten. You can disable a bunch of stuff to stop this happening, but what worked best for me was to edit /etc/dhcp3/dhclient.conf

Find the line that says:
```
#prepend domain-name-servers 127.0.0.1;
```Uncomment it and replace 127.0.0.1 with your actual nameservers, like this:
```
prepend domain-name-servers 212.23.21.20, 212.23.21.20;
```(using your nameservers obviously) This means that whenever your dhcp client does it's thing it will automatically re-add those namesevers to your resolv.conf. If you want you can also stop it from grabbing your router (the 192.168.1.1 entry you see in resolv.conf) I needed to do this to make it work. Find the line that looks like:
```
request subnet-mask, broadcast-address, time-offset, routers,
        domain-name, domain-name-servers, host-name,
        netbios-name-servers, netbios-scope;
```And remove "domain-name-servers," so it looks like:
```
request subnet-mask, broadcast-address, time-offset, routers,
        domain-name, host-name,
        netbios-name-servers, netbios-scope;
```Obviously this stops the dhcp client requesting nameservers, and you end up with only the ones you prepended above.

You might need to restart networking or dhcp3 or something for the changes to take effect. Something like:```
sudo /etc/init.d/dhcp3 restart
```I'm guessing, but I don't have a machine to check it on.

---

### Post by robek on 2006-08-01
I've simply commented out call to make_resolv_conf() near the end of dhclient-script and than edited resolv.conf

---

### Post by rupesh on 2006-08-02
firstly Thanks for all ppl for their valuable suggestions and all help.
 and special thanks to genius MIPS. to fix last bug i tried following things with the results:-

 1) assigning IP statically----- It worked finely for some time.. but it took long time to load pages.. also with frequent errors of server could not reach. 

2) assigning dns server in router--- it was already specified there..

3)commenting out make_resolv_conf(). didnt worked out for me.. as network itself was not able to establish.

4)as suggested by markmark making changes in /etc/dhcp3/dhclient.conf worked very fine. i didnt need to remove already existing entry i.e. 192.168.1.1 

  hope this will help for all those who r facing same problem.

---

### Post by Troglodite on 2006-09-14
Hi I have the same problem.

Already did everything in here, but i cant seem to put it working. My router doesnt tracerout the cisco.com. And i tried doing directly from the router, and it doesnt trace either. So i guess the problem is the router. Any ideas?

---

### Post by mips on 2006-09-15
Will have a look a bit later but I have to go out now.

---

### Post by mips on 2006-09-17
> **Troglodite said:**
> Hi I have the same problem.

Already did everything in here, but i cant seem to put it working. My router doesnt tracerout the cisco.com. And i tried doing directly from the router, and it doesnt trace either. So i guess the problem is the router. Any ideas?

Still got a problem ?

---

### Post by tomhollis on 2006-09-30
I had the same problem with a linksys router, adding the DNS of my ISP and removing the router solved the problem as above.

Thanks

Tom

---

### Post by thelinuxguy on 2006-12-09
> **rupesh said:**
> yup i got who is 220.227.119.54
 this is one big telecom company in india. dont have any idea of how i got their ip. as i am not subscriber of this. so what to do now? 
 output of 220.227.119.54--------------
 	


U were talking about Reliance Infocomm and that you haven't subscribed to them. This may be your problem. 

Your output shows that you have a WLAN card. Reliance Infocomm operates wireless internet in many areas in India (I am unaware of any such operations elsewhere). So you are getting connected to Reliance Infocomm's gateway. But you don't have a username/password to be authenticated to use the connection. Its just that you are getting a DHCP assigned IP.

And maybe that interface is somehow getting set as the default gateway. So you can ping 192.168.1.1 (which can be reached locally) but you cannot ping 198.133.219.25 because it is an external IP and requires you to go through the gateway; which, at the moment you aren't allowed to.

To solve the problem, either deactivate the WLAN interface (if you are not using it) or set 192.168.1.1 as the default gateway. I would recommend the first since you are connecting to the internet using the DLink router/modem. Hey mips, good idea about pinging the two addresses ;)

I have no idea how the browser is able to get you content. Maybe it also tries 192.168.1.1 after trying the default gateway. Try this out and let us know if this solves your problem.

Regards.

---

