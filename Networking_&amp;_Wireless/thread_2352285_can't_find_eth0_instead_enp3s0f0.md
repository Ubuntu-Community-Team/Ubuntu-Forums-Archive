---
title: "can't find eth0 instead enp3s0f0"
date: 2017-02-11
forum: Networking &amp; Wireless
---

### Post by samuelbles on 2017-02-11
Hi,

I am new to ubuntu and I have a problem with my ethernet. I can't find eth0 instead enp3s0f0

```
enp3s0f0  Link encap:Ethernet  HWaddr 20:6a:8a:44:55:05            
inet6 addr: fe80::3fdd:b167:5850:1f41/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:302 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:51972 (51.9 KB)
          Interrupt:19 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1626 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1626 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:344498 (344.4 KB)  TX bytes:344498 (344.4 KB)


wlp2s0    Link encap:Ethernet  HWaddr 20:7c:8f:69:e2:d5  
          inet addr:10.6.11.50  Bcast:10.6.11.255  Mask:255.255.255.0
          inet6 addr: fe80::37ea:ff8a:d671:3412/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13629 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8705 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8682863 (8.6 MB)  TX bytes:1829780 (1.8 MB)
```

i try a couple tutorial like change the ```
/etc/network/interfaces
``` but still not solve my problem.
what i'm trying to do is communicate to my raspberry pi via ssh but before i want to know the ip address of my raspberry using nmap in this tutorial [https://www.raspberrypi.org/documentation/remote-access/ip-address.md](https://www.raspberrypi.org/documentation/remote-access/ip-address.md) 
I follow the ```
hostname -i
``` but the output is the loopback ip
Before i want to communicate to arduino ethernet shield. i ran ```
telnet IP port
``` but the result is network unreachable
so i know the problem is from my computer 
i appreciate your help thanks!

---

### Post by pqwoerituytrueiwoq on 2017-02-11
Ubuntu no longer uses names like eth0, eth1 instead it uses weird looking numbers based on the chip and port number the device is on

you can see stuff like this now (these are from a system with 2 NICs each with 2 ports (4 Ethernet jacks total))
eno1
eno2
enp5s0f0
enp5s0f1

i usually look at my router's DHCP client list to find the IP for a new raspberry pi install that does not yet have a static IP address
this command would show you a list of the devices on your network
```
nmap -sn 10.6.11.0/24  | grep "^Nmap"
```
* your system looks to have a wired jack and a wifi connection, you appear to only have a wifi connection active


please be aware that by default a RPI with a new install will NOT have SSH enabled by default
you will need to put a file named "ssh" in the boot partition of the raspberry pi's sd card
[https://www.raspberrypi.org/blog/a-security-update-for-raspbian-pixel/](https://www.raspberrypi.org/blog/a-security-update-for-raspbian-pixel/) (also applies minimal installs)
I can confirm there are bots out there that to try the default ssh login for a raspberry pi (seen them show a server's /var/log/auth.log file)

if you open the sd cards boot partition on you ubuntu box via the guu you can run this command to add the file (or just make a new empty file via right click -> new file)
```
touch /media/$USER/boot/ssh
```

as for your telnet command, you are supposed to change IP and port to a ip address and port number


you should not edit the /etc/network/interfaces file on a desktop ubuntu install (you have a network manager installed that handles this itself)

---

### Post by samuelbles on 2017-02-11
Oh thanks for your reply
I forgot enabled about it about the ssh raspberry 

at the telnet, i alredy use this command ```
telnet 192.168.1.3 10002 
``` and the output is [B]trying 192.168.1.3.. 

[/B]but i still can't connect it to my arduino ethernet shield

this is my [B]xinetd status
[/B]
```
xinetd.service - LSB: Starts or stops the xinetd daemon.   Loaded: loaded (/etc/init.d/xinetd; bad; vendor preset: enabled)
   Active: active (running) since Sab 2017-02-11 23:27:55 WIB; 52min ago
     Docs: man:systemd-sysv-generator(8)
  Process: 4998 ExecStop=/etc/init.d/xinetd stop (code=exited, status=0/SUCCESS)
  Process: 5010 ExecStart=/etc/init.d/xinetd start (code=exited, status=0/SUCCESS)
   CGroup: /system.slice/xinetd.service
           &#9492;&#9472;5025 /usr/sbin/xinetd -pidfile /run/xinetd.pid -stayalive -inetd...


Peb 11 23:27:55 bles xinetd[5025]: removing daytime
Peb 11 23:27:55 bles xinetd[5025]: removing daytime
Peb 11 23:27:55 bles xinetd[5025]: removing discard
Peb 11 23:27:55 bles xinetd[5025]: removing discard
Peb 11 23:27:55 bles xinetd[5025]: removing echo
Peb 11 23:27:55 bles xinetd[5025]: removing echo
Peb 11 23:27:55 bles xinetd[5025]: removing time
Peb 11 23:27:55 bles xinetd[5025]: removing time
Peb 11 23:27:55 bles xinetd[5025]: xinetd Version 2.3.15 started with libwr...n.
Peb 11 23:27:55 bles xinetd[5025]: Started working: 0 available services
Hint: Some lines were ellipsized, use -l to show in full
```

is that seems okay to you?
thanks, i appreciate your help

---

### Post by pqwoerituytrueiwoq on 2017-02-11
I have never used a arduino, i know telnet is on port 23 by default did you change it to port 10002?

---

### Post by wildmanne39 on 2017-02-11
enp3s0f0 is your ethernet connection it has been renamed with the new system put into place in 16.04.

---

### Post by samuelbles on 2017-02-11
i'm sorry i mean port 23 not 10003 *typo there
no i'm not changing anything

---

### Post by The Cog on 2017-02-11
Is this network at home? 
The reason I ask: Your Ubuntu is on network 10.6.11.* and your telnet command is trying to connect to something on network 192.168.1.*. If this is a large company network then this might be entirely possible. But I am thinking that this might be a small home network in which case they should both be on the same network number.

---

### Post by samuelbles on 2017-02-11
no sir,
what i want to do is just a simple telnet connection using ethernet cable from my laptop as a server and arduino as a client. The client IP is 192.168.1.3

---

### Post by The Cog on 2017-02-11
So this is an ethernet patch lead, direct between the PC and the Arduino?
If that's right:
Your Ububtu ethernet port is called enp3s0f0 not eth0, because of a recent change in the way interfaces are named, but that should not cause any problems.
You say the arduino is 192.168.1.3 - I'll take your word for that. I know nothing about arduinos.

From post #1 I can see that your Ubuntu box does not have an IP address on enp3s0f0 at the moment. However, the cable is connected and it is transmitting packets which is good.

Ubuntu will need a different IP address in the same network range. e.g. 192.168.1.2. Ubuntu normally gets given an IP address by a DHCP server on the network. I don't suppose the arduino will do that, so you need to manually configure a "static" IP address on enp3s0f0. I would suggest 192.168.1.2 with a subnet mask of 255.255.255.0. Don't give it a default gateway on this interface. See this link [https://help.ubuntu.com/lts/serverguide/network-configuration.html](https://help.ubuntu.com/lts/serverguide/network-configuration.html) for both temporary and permanent IP address assignment.

Also, Ubuntu doesn't normally listen for incoming telnet connections. You could install a telnet server on Ubuntu with the command:
```
sudo apt install telnetd
```
but be aware that there are lots of telnet password guessing bots scanning the internet. Look at whether telnet connections could reach you from the internet.
Uninstall the telnet server again when you have finished with it.

---

