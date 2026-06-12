---
title: "Help Setting up a Home Network - Ubuntu Desktop to Ubuntu Wireless Laptop"
date: 2006-09-06
forum: Networking &amp; Wireless
---

### Post by mtn on 2006-09-06
**[SIZE="4"]Success Yeeehaaw – See the 6th post![/SIZE]**

I want to set up a home network so I can share files between a desktop and laptop both running Ubuntu Dapper. Although I have been getting on really well with Ubuntu I don't know where to start when it comes to networking.

I have a Belkin 802.11g wireless router that my PC is wired to and a laptop that connects wireless to the router so both have access to the internet. Can anyone point me towards a “how to” or give me some an idea how I might go about sharing files between these to computers?

Cheers

---

### Post by arosboro on 2006-09-06
I'm doing the same thing.  You'd want to find some guides on setting up samba for Dapper.  Samba is the open source version of windows file sharing.

Also if you want wpa for the wireless security (wep is broken), you need to find out how to install wpa_supplicant (that's the step I'm at).

Ssh is also very useful to learn about, it helps you remotely run commands and transfer files to between your computers with encryption.

---

### Post by mtn on 2006-09-06
Thanks, I'm slowly making head way. This samba guide looks ok [https://help.ubuntu.com/community/SettingUpSamba#head-ef9b96864b8c44ebe5891fe9ac7f5da1ed46d1bc](https://help.ubuntu.com/community/SettingUpSamba#head-ef9b96864b8c44ebe5891fe9ac7f5da1ed46d1bc)

Also went through this NFS guide [http://nfs.sourceforge.net/nfs-howto/index.html](http://nfs.sourceforge.net/nfs-howto/index.html) Set up my desktop as server and laptop as client. I got stuck when I needed to know my "server name", no idea what that is! Anyway, when I tried the mount command from my laptop I'm told I need to indicate what file system I'm trying to mount, I think it is reiser but I don't know what the command/switch is!

Good luck...

---

### Post by mtn on 2006-09-07
This is totally doing my nut in now. I have tried a number of “how to's” and threads. Tried settign up NFS and samba and nothing seems to work.

These two samba guides look like they should do but they don't work for me...
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)
[http://doc.gwos.org/index.php/Share_files_using_Samba](http://doc.gwos.org/index.php/Share_files_using_Samba)

I think I'm missing something as nothing explains what the server name is.

The out put for my desktop when using “/sbin/ifconfig” that I am setting up as the server is...

```
mike@Ubuntu-Home:~$ /sbin/ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0F:EA:3F:A3:C0
          inet addr:169.254.112.113  Bcast:169.254.255.255  Mask:255.255.0.0
          inet6 addr: fe80::20f:eaff:fe3f:a3c0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:23415 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23240 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:8880463 (8.4 MiB)  TX bytes:2074702 (1.9 MiB)
          Interrupt:217

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:112 errors:0 dropped:0 overruns:0 frame:0
          TX packets:112 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:9762 (9.5 KiB)  TX bytes:9762 (9.5 KiB)
```

The out put from my laptop that I am setting up as the client is...

```
mike@mike-laptop:~$ /sbin/ifconfig lo        Link encap:Local Loopback
         inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:39 errors:0 dropped:0 overruns:0 frame:0
          TX packets:39 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2266 (2.2 KiB)  TX bytes:2266 (2.2 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:E0:98:C3:01:73
          inet addr:192.168.2.4  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:98ff:fec3:173/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1428 errors:0 dropped:115 overruns:0 frame:0
          TX packets:1350 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1000130 (976.6 KiB)  TX bytes:189509 (185.0 KiB)
          Interrupt:11 Memory:d023e000-d023e100
```

When I login to my router it shows these settings...

```
LAN Settings

LAN/WLAN MAC: 00:11:50:08:FC:08, 00:11:50:09:89:0F 
IP address: 192.168.2.1
Subnet mask: 255.255.255.0
DHCP Server: Enabled

Internet Settings 

WAN MAC address: 00:11:50:08:FC:09
Connection Type: Dynamic
Subnet mask: 255.255.254.0
Wan IP: 80.192.27.221
Default gateway: 80.192.26.1
DNS Address: 62.31.64.39
```

In the LAN > DHCP Client List section this is what I have...

```
LAN > DHCP 

IP Address	Host Name 	MAC Address
192.168.2.2	(null)		00:0f:ea:3f:a3:c0
192.168.2.4	(null)		00:e0:98:c3:01:73
```

So it looks like I don't have host names for my computers, could this be the problem?

Any help with this would be amazing!

---

### Post by tbonius on 2006-09-07
The servername is the given computername for each system you installed.  During installation.. each system is given a name.  For all the other systems on a network, they need to be able to resolv the name to an IP address via different methods in order to connect to that system over the network.  

Most network employ DNS (Domain Name Services).  This service is exactly how you are able to find web pages and various other services on the internet.

In a home network of only two or so computers.. DNS isnt really necessary (though it can be helpful in maintaining the name and address space of a network).  To have your computers on a small network be able to resolv each other.. you would simply edit their /etc/hosts file and put in entries for each computer.

Something similar to:

```

192.168.0.2     ubuntu1
192.168.0.3     ubuntu2

```

etc..

Be sure you put the correct IP addresses of each host you want to resolve.  Now you should be able to ping the computer with the name you put in /etc/hosts

```
ping ubuntu1
64 bytes from ubuntu1 (192.168.0.2): icmp_seq=1 ttl=64 time=0.050 ms

```

The advantage to DNS is that you dont have to edit /etc/hosts files on EVERY single computer on the network.  There is a centralized name server that all computers on the network use to resolve the server names to IP addresses.

Hope this helps

T

---

### Post by mtn on 2006-09-08
Thanks tbonius, I couldn't figure out that you needed to give each computer the IP address and hostname of the other computer on the network.

**Setting Up FTP File Sharing**
I went into System>Administration>Networking, the general tab gives you the hostname (or aliases as they are called in the “hosts” tab!). I then used the hostname on the other computer as the aliases name in the “host” tab, for example on the desktop “hosts” tab I added the laptop,  “IP address”: 192.168.2.4 and “aliases”: ubuntu-laptop. I did the same on the laptop changing the IP for the desktop's IP address 192.168.2.2 and aliases: ubuntu-home. I then followed this guide “HOWTO Ridiculously easy home file sharing with FTP and Zeroconf”: [http://www.ubuntuforums.org/showthread.php?t=218630&highlight=samba](http://www.ubuntuforums.org/showthread.php?t=218630&highlight=samba) only where it says “hostname.local” I changed that for my computers hostnam/aliases i.e. ubuntu-home and ubuntu-laptop and this did the job.

On reflection it was probably my ignorance regarding the hostnames that was stopping me setup Samba and NFS...oh well FTP will do just fine.

**Firewall Issue**
I had on probem as I forgot I had Firestarter (my firewall) running and this was blocking the FTP connections form the computers. I opened up Firestarter on each computer and clicked on the "events" tab, found the IP address of the other computer indicating that there had been an attempted FTP connection. I right clicked on this and click the "allow connections from source" option and that was sorted.

Thanks again for your help.

---

