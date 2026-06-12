---
title: "Internet"
date: 2018-09-16
forum: Networking &amp; Wireless
---

### Post by baba8464 on 2018-09-16
Hi, I had upgraded Ubuntu-16 to Ubuntu-18. In Ubuntu-16 internet was working fine but now I can see,  I have internet connection (both wire and wireless). But internet is not working. Could you please help me to find problem? Internet is working in Windows.

I am still waiting if somebody will respond me and help me in this issue.

Thanks

/Babar

---

### Post by Doug S on 2018-09-16
> **baba8464 said:**
> I can see,  I have internet connection (both wire and wireless). But internet is not working. Could you please help me to find problem?Well, you haven't given us much information. Also, I am a little unclear what you mean by "I have an internet connection but internet is not working". To get started:

Can you ping your gateway? Example:

```
doug@s17:~$ [COLOR="#FF0000"]route -n[/COLOR]
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         [COLOR="#FF0000"]192.168.111.1[/COLOR]   0.0.0.0         UG    100    0        0 ens5
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 ens5
192.168.111.0   0.0.0.0         255.255.255.0   U     100    0        0 ens5
doug@s17:~$
doug@s17:~$ [COLOR="#FF0000"]ping 192.168.111.1[/COLOR]
PING 192.168.111.1 (192.168.111.1) 56(84) bytes of data.
64 bytes from 192.168.111.1: icmp_seq=1 ttl=64 time=0.351 ms
64 bytes from 192.168.111.1: icmp_seq=2 ttl=64 time=0.363 ms
64 bytes from 192.168.111.1: icmp_seq=3 ttl=64 time=0.318 ms
^C
--- 192.168.111.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2034ms
rtt min/avg/max/mdev = 0.318/0.344/0.363/0.019 ms

```Can you ping somewhere external via IP address? (A google name server is always good to try, because we know it will reply to "ping"):

```
doug@s17:~$ [COLOR="#FF0000"]ping 8.8.8.8[/COLOR]
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=123 time=29.3 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=123 time=29.2 ms
64 bytes from 8.8.8.8: icmp_seq=3 ttl=123 time=28.9 ms
64 bytes from 8.8.8.8: icmp_seq=4 ttl=123 time=28.7 ms
^C
--- 8.8.8.8 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3004ms
rtt min/avg/max/mdev = 28.712/29.056/29.313/0.259 ms

```Can you ping via name (i.e. is it actually DNS that is not working)?:
```
doug@s17:~$ [COLOR="#FF0000"]ping google-public-dns-a.google.com[/COLOR]
PING google-public-dns-a.google.com (8.8.8.8) 56(84) bytes of data.
64 bytes from google-public-dns-a.google.com (8.8.8.8): icmp_seq=1 ttl=123 time=28.1 ms
64 bytes from google-public-dns-a.google.com (8.8.8.8): icmp_seq=2 ttl=123 time=29.5 ms
64 bytes from google-public-dns-a.google.com (8.8.8.8): icmp_seq=3 ttl=123 time=29.2 ms
64 bytes from google-public-dns-a.google.com (8.8.8.8): icmp_seq=4 ttl=123 time=29.2 ms
^C
--- google-public-dns-a.google.com ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3004ms
rtt min/avg/max/mdev = 28.182/29.065/29.593/0.556 ms

```

---

### Post by baba8464 on 2018-09-16
I meant to say, it is connected to my router but it is showing symbol "?". When i open my browser then its shows "The site can't be reached".

[COLOR=#000000]Can you ping somewhere external via IP address? (A google name server is always good to try, because we know it will reply to "ping"):

Should you meant by "ping google"  then it d´doest not work for me.

route -n and
ping 192.168.10.1      // working

ping 8.8.8.8              // working 


My internet is not working 



[/COLOR]

[COLOR=#000000]Can you ping somewhere external via IP address? (A google name server is always good to try, because we know it will reply to "ping"):

Should you meant by "ping google"  then it d´doest not work for me.

route -n and
ping 192.168.10.1      // working

ping 8.8.8.8              // working 


My internet is not working 



[/COLOR]

I was trying to post pics i got from camera but it is not way to post here. Otherwise i can show you in place of internet connection symbol, I have "?".

[COLOR=#FF0000]ping google-public-dns-a.google.com  


[/COLOR]I tried above command also but this is not working for me.

---

### Post by Doug S on 2018-09-16
O.K. so internet is working fine, and it is actually DNS that is not working (which seems to be a common problem with 18.04). At least now we know where to concentrate.

I am not an expert on DNS issues with 18.04 (I am not a fan of netplan and so have not moved from 16.04 to 18.04). Maybe someone else is. Meantime, I'll try to figure out the next step.

---

### Post by baba8464 on 2018-09-16
This is my bad luck to take decision to upgrade Ubuntu 18 at this occasion. I have to work on my Labs. So what to recommend to reinstall Ubuntu 16.04 ? Or can I degrade back to Ubuntu 16.04?

---

### Post by Doug S on 2018-09-16
> **baba8464 said:**
> This is my bad luck to take decision to upgrade Ubuntu 18 at this occasion. I have to work on my Labs. So what to recommend to reinstall Ubuntu 16.04 ? Or can I degrade back to Ubuntu 16.04?well, don't go back to 16.04 yet. Is your IP address via DHCP or is it static? What files do you have in /etc/netplan? Example:

```
doug@s17:~$ [COLOR="#FF0000"]ls -l /etc/netplan[/COLOR]
total 4
-rw-r--r-- 1 root root 104 Apr 20 00:48 01-network-manager-all.yaml
doug@s17:~$ [COLOR="#FF0000"]cat /etc/netplan/01-network-manager-all.yaml[/COLOR]
# Let NetworkManager manage all devices on this system
network:
  version: 2
  renderer: [COLOR="#FF0000"]NetworkManager[/COLOR]

```O.K. so my test 18.04 computer is using NetworkManager, and I can observe the DNS has been set therein. What do you observe under settings - network - under the settings for whatever interface?

---

### Post by baba8464 on 2018-09-16
I would also like to share with you when i upgraded and then restarted my labtop, Ubuntu was unable to boot. Screen was getting on and off quickly but I managed to see lines with started with [Ok] but two lines was [failure].

1) Fail to start Cgroup management daemon¨.
2) Fail to start process error reports when automatic reporting is enabled.

In advance options: i used option: make space. So after that it booted.

IPV4 is DHCP and IPV6 is Disable.

[COLOR=#FF0000]ls -l /etc/netplan

total 0

[/COLOR]
[COLOR=#FF0000]cat /etc/netplan/01-network-manager-all.yaml
[/COLOR]No such file or directory

I am using this to restart network-manager.

sudo /etc/init.d/network-manager restart.   

It restart network but still internet is not working,

---

### Post by Doug S on 2018-09-16
It seems that if one upgrades from 16.04 to 18.04, then netplan is not used and ifupdown is still used. For DHCP, you should be getting the DNS information with your IP address lease. Example (Specific for my network interface, br0. You would have to look at the correct file for your interface name):

```
doug@s15:~/idle$ [COLOR="#FF0000"]cat /var/lib/dhcp/dhclient.br0.leases[/COLOR]

...[snip]...

lease {
  interface "br0";
  fixed-address 192.168.111.112;
  option subnet-mask 255.255.255.0;
  option routers 192.168.111.1;
  option dhcp-lease-time 86400;
  option dhcp-message-type 5;
  [COLOR="#FF0000"]option domain-name-servers 192.168.111.1[/COLOR];
  option dhcp-server-identifier 192.168.111.1;
  option broadcast-address 192.168.111.255;
  option domain-name "smythies.com";
  renew 1 2018/09/17 03:58:31;
  rebind 1 2018/09/17 14:54:23;
  expire 1 2018/09/17 17:54:23;
}
doug@s15:~/idle$

```You will have to decide how to proceed. If you want to switch to netplan, perhaps start [here]("https://askubuntu.com/questions/1034711/how-to-enable-netplan-on-ubuntu-server-upgraded-from-16-04-to-18-04"). If you want to stay with ifupdown, then we still need to figure out what is wrong. please post the contents of your /etc/network/interfaces file.

---

### Post by baba8464 on 2018-09-16
Let we try with ifupdown, there is no specific reason for this. i wrote in terminal cat [COLOR=#000000]/etc/network/interfaces:

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback[/COLOR]

---

### Post by baba8464 on 2018-09-16
It is too late here in Sweden, I will get back again tomorrow for this issue. I hope tomorrow you have good solution for this. I appreciate your effort.

---

### Post by baba8464 on 2018-09-17
Hi, I am here if you have something to share with me to fix error?

---

### Post by baba8464 on 2018-09-17
Hello, Do you have something to share ?

---

### Post by Doug S on 2018-09-17
The problem is that I mostly use servers and don't, with certainty, know if desktop computers are configured in the same way (Because servers don't use network manager). If you are still using "ifupdown" then I don't understand why your /etc/network/interfaces file is basically empty. Save a copy of the existing file and then try editing it to specify the interface and that it is dhcp. Something like (using my interface name. yours will likely be different):

```
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

# The primary interface (d-link PCI card)
auto enp4s0
iface enp4s0 inet dhcp
```note: you will need to edit the file as root, i.e.:
```
doug@DOUG-64:~$ sudo nano /etc/network/interfaces

```

---

### Post by baba8464 on 2018-09-18
I modified interfaces file. I added these lines: 

# The primary interface (d-link PCI card)
auto enp4s0
iface enp4s0 inet dhcp

But still internet is not working.

---

