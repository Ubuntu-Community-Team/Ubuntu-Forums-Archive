---
title: "SSH, Samba problems after reboot"
date: 2006-11-20
forum: Networking &amp; Wireless
---

### Post by jdwinfodesign on 2006-11-20
I have a desktop running Ubuntu Dapper and a laptop set up to dual-boot Windows XP and Dapper.

Both machines were configured and able to communicate over my wireless network.

Recently, I rebooted the desktop machine, which is the server, and I could not connect via Samba from either OS on the laptop.

So, I uninstalled Samba and LinNeighborhood on the laptop, and the Samba server on the desktop.

After reinstallation, everything worked.

After rebooting again, the same problem has returned, with the additional issue that I cannot ssh between the laptop (running Ubuntu) and the desktop.

So...there must be something wrong somewhere, eh? 

During my reinstallation of Samba, I installed the Samba server and commons on the desktop, then edited /etc/hosts on both machiens with the IP address for each. I could ping back and forth. And, the Samba setup seemed to work.

The IP addresses have remained the same, so what else could it be?

And why can I not ssh between machines now? I can ssh to my Web hosting account, if that information is useful.

If someone can point me to a simple install (not the one on the ubuntu.org website) that would be great.

---

### Post by earobinson on 2006-11-20
can you check that the sshd is actually running for example? Sounds to me like the deamons that run the apps arnt being booted

---

### Post by dbott67 on 2006-11-20
Can you post the output of the following commands (from the server):
```
dbott@edgy:~$ **ps aux | grep sshd**
root      4173  0.0  0.1   4940  1072 ?        Ss   Nov19   0:00 /usr/sbin/sshd
root     21505  0.0  0.2   7716  2336 ?        Ss   10:08   0:00 sshd: dbott [priv]
dbott    21515  0.0  0.1   7716  1600 ?        S    10:08   0:00 sshd: dbott@pts/1
dbott    21662  0.0  0.0   2800   752 pts/1    R+   10:13   0:00 grep sshd
```
```
dbott@edgy:~$ **sudo iptables -L**
Password:
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```

-Dave

---

### Post by jdwinfodesign on 2006-11-20
jdw@jdw-desktop:~$ ps aux | grep sshd
root      4549  0.0  0.2   4764  1028 ?        Ss   08:18   0:00 /usr/sbin/sshd
jdw       5222  0.0  0.1   2896   824 pts/0    S+   10:40   0:00 grep sshd
jdw@jdw-desktop:~$ sudo iptables -L
Password:
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

---

### Post by dbott67 on 2006-11-20
Okay.. this tells me that the ssh daemon is running (a good thing) and that you don't have any firewall that is blocking (also good).

Are both computers on the same subnet?

Can you post the the output of the following commands from both the server and from the laptop:
```
dbott@edgy:~$ **ifconfig -a**
eth0      Link encap:Ethernet  HWaddr 00:50:BA:C0:A7:XX
          inet addr:192.168.1.106  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::250:baff:fec0:a755/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:17147 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10202 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:10077494 (9.6 MiB)  TX bytes:1773036 (1.6 MiB)
          Interrupt:185 Base address:0xc000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
```

```
dbott@edgy:~$ **route -n**
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
```

---

### Post by jdwinfodesign on 2006-11-20
jdw@jdw-desktop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:0B:CD:64:C7:FC
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20b:cdff:fe64:c7fc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7584 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7658 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:6292716 (6.0 MiB)  TX bytes:1175611 (1.1 MiB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:110 errors:0 dropped:0 overruns:0 frame:0
          TX packets:110 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:80727 (78.8 KiB)  TX bytes:80727 (78.8 KiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

jdw@jdw-desktop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0

---

### Post by dbott67 on 2006-11-20
> **jdwinfodesign said:**
> jdw@jdw-desktop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:0B:CD:64:C7:FC
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20b:cdff:fe64:c7fc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7584 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7658 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:6292716 (6.0 MiB)  TX bytes:1175611 (1.1 MiB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:110 errors:0 dropped:0 overruns:0 frame:0
          TX packets:110 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:80727 (78.8 KiB)  TX bytes:80727 (78.8 KiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

jdw@jdw-desktop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0

Everything looks good with the settings above for the server.

Can you also print the output of the laptop?

BTW, are trying to SSH using Windows or Ubuntu or do they both not work?

-Dave

---

### Post by jdwinfodesign on 2006-11-21
jdw@jdw-laptop:~$ ps aux | grep sshd
root      4805  0.0  0.1   4760  1024 ?        Ss   07:46   0:00 /usr/sbin/sshd
jdw       5380  1.0  0.1   2888   808 pts/0    R+   07:51   0:00 grep sshd
jdw@jdw-laptop:~$ sudo iptables -L
Password:
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
jdw@jdw-laptop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:0D:60:79:E5:52
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Base address:0x8000 Memory:c0220000-c0240000

eth1      Link encap:Ethernet  HWaddr 00:0E:35:7D:A3:AF
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:35ff:fe7d:a3af/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:274 errors:0 dropped:0 overruns:0 frame:0
          TX packets:141 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:177209 (173.0 KiB)  TX bytes:13879 (13.5 KiB)
          Interrupt:11 Base address:0xa000 Memory:c0210000-c0210fff

irda0     Link encap:IrLAP  HWaddr 00:00:00:00
          NOARP  MTU:2048  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:8
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:13 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:832 (832.0 b)  TX bytes:832 (832.0 b)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

jdw@jdw-laptop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth1

---

### Post by jdwinfodesign on 2006-11-21
The previous post contains the output from the laptop.

In answer to your question: I have not tried ssh'ing to the server from the laptop using Windows, only Ubuntu. However, neither OS can mount a Samba share from the server. For this reason, I figured it was something amiss with either the Samba setup or a network config issue on the desktop machine.

---

### Post by dbott67 on 2006-11-21
Everything looks okay here also.

My next recommendation would be to use Synaptic to remove the following packages:

- ssh
- samba
- smbclient
- smbfs

Use the option to "**Mark for Complete Removal**" as well (this should get rid of all config files).  I don't know what the "apt-get remove" equivalent is, or else you could use that.

Then, re-install the above packages.

-Dave

---

### Post by jdwinfodesign on 2006-11-21
I will give that a try. However, this is a lot like what I did before...the only difference being that I did not uninstall and reinstall ssh.

I will get that done today or tomorrow and then try to recreate the issue by rebooting the desktop machine. Then, I will post a reply with the results.

---

### Post by neocon2005 on 2006-11-22
Hello folks
I can confirm that I have a very similar problem. Ubuntu (edgy) on laptop and desktop. Can't ssh from laptop to desktop when I am home. When I took the laptop to work, had no problems connecting via ssh. I have a Linksys router WRT56G (NAT port 22 to desktop). I tried connecting laptop via ethernet also. No luck. I was hoping to use ssh to share folders between the Ubuntu machines.. alas.. Please help. Thanks in advance.

---

