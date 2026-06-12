---
title: "Newbie Networking Questions"
date: 2006-07-28
forum: Networking &amp; Wireless
---

### Post by jvn on 2006-07-28
I recently set up a dual-boot machine at school with Windows XP Pro.  It has been a lot of fun playing with Ubuntu and getting things set up.  Everything went beautifully, until I had to move my desk to a new location.  Since I moved the computer I haven't been able to config my network settings.  When I boot into Windows I am able to connect just fine.  

I have searched the forums but I haven't been able to solve the problem.  I did see one requesting the following information for background:

Output of **ifconfig eth0**
Output of **lspci | grep Eth**
Output of **route -n**
Output of **cat /etc/resolv.conf**
Output of **cat /etc/network/interfaces**
Output of **cat /etc/dhcp3/dhclient.conf**
Output from Windows of **ipconfig /all**

Here is that output:

```
me@computer:~$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:12:3F:A4:F5:26
          inet6 addr: fe80::212:3fff:fea4:f526/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2387 errors:9650 dropped:0 overruns:0 frame:9650
          TX packets:48 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:165189 (161.3 KiB)  TX bytes:14832 (14.4 KiB)


me@computer:~$ lspci | grep Eth
0000:03:08.0 Ethernet controller: Intel Corporation 82801G (ICH7 Family) LAN Controller (rev 01)


me@computer:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface


me@computer:~$ cat /etc/resolv.conf
search eller.arizona.edu
nameserver 128.196.190.92
nameserver 128.196.190.93
domain eller.arizona.edu


me@computer:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp


me@computer:~$ cat /etc/dhcp3/dhclient.conf
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

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


C:\Documents and Settings\finphd>ipconfig /all

Windows IP Configuration

        Host Name . . . . . . . . . . . . : finphd-1
        Primary Dns Suffix  . . . . . . . : eller.college
        Node Type . . . . . . . . . . . . : Hybrid
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No
        DNS Suffix Search List. . . . . . : eller.college
                                            eller.arizona.edu

Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . : eller.arizona.edu
        Description . . . . . . . . . . . : Intel(R) PRO/100 VE Network Connection
        Physical Address. . . . . . . . . : 00-12-3F-A4-F5-26
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        IP Address. . . . . . . . . . . . : 128.196.239.236
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 128.196.239.1
        DHCP Server . . . . . . . . . . . : 128.196.190.92
        DNS Servers . . . . . . . . . . . : 128.196.190.92
                                            128.196.190.93
        Primary WINS Server . . . . . . . : 128.196.190.93
        Lease Obtained. . . . . . . . . . : Friday, July 28, 2006 10:08:52 AM
        Lease Expires . . . . . . . . . . : Friday, July 28, 2006 11:08:52 AM

```


I would very much appreciate your help with this.  

Thank you!

---

### Post by steve.horsley on 2006-07-28
It looks to me as though you are not being given an IP address by the DHCP server. 

Can you try **sudo dhclient eth0** and see how it goes? Post the results?

---

