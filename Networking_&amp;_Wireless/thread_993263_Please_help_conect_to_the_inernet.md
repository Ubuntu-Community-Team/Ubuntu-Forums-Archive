---
title: "Please help conect to the inernet"
date: 2008-11-25
forum: Networking &amp; Wireless
---

### Post by medusgovs on 2008-11-25
Hi there,
I have dual boot system Ubuntu and ms XP. Can't get Ubuntu online while having no problems in XP.
I did everything as said in the [manual]("https://help.ubuntu.com/8.10/internet/C/modems-adsl-pppoe.html") and much more, but it wont work.
if i use "sudo pppoeconf" i get this message:
sorry, i scanned 2 interfaces, but the Access Concentrator of your provider did not respond. please check your network and modem cables. ANother reason may be another running pppoe process wich controls modem.

if i choose my ethernet card by "sudo pppeoconf eth0" it starts with message:
Interface eth0 has MTU of 576 -- should be 1500.  You may have serious connection problems."
but then installs the connection that doesn't work.

ifconfig output:

```
eth0      Link encap:Ethernet  HWaddr 00:1b:fc:2a:8f:86  
          inet addr:172.20.32.218  Bcast:172.20.39.255  Mask:255.255.248.0
          UP BROADCAST RUNNING MULTICAST  MTU:576  Metric:1
          RX packets:6556 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1247706 (1.2 MB)  TX bytes:5193 (5.1 KB)
          Interrupt:219 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:72 errors:0 dropped:0 overruns:0 frame:0
          TX packets:72 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3600 (3.6 KB)  TX bytes:3600 (3.6 KB)


```

to connect i use:
ADSL modem Thompson tcm425
Realtek RTL8168/8111 PCI-E Gigabit Ethernet NIC

Any suggestions?
please help

---

### Post by lswb on 2008-11-25
Isn't the Thompson TCM425 a cable modem? If so it probably doesn't use pppoe. Your ifconfig output is already showing that an ip address has been assigned from the private 172.x.x.x range. It looks like you have a working connection. 

What kind of errors are returned when you try to connect to a web site? How about if you open a terminal and type 

ping google.com

or 

ping 66.233.187.99

---

### Post by medusgovs on 2008-11-25
thanx for responce

> sn't the Thompson TCM425 a cable modem?
you are right i have a cable conection

> ping google.com
```
trip@mint445:~$ ping google.com
PING google.com (213.57.1.13) 56(84) bytes of data.
--- google.com ping statistics ---
225 packets transmitted, 0 received, 100% packet loss, time 224013ms

```

> ping 66.233.187.99
```

trip@mint445:~$ ping 66.233.187.99
PING 66.233.187.99 (66.233.187.99) 56(84) bytes of data.
--- 66.233.187.99 ping statistics ---
199 packets transmitted, 0 received, 100% packet loss, time 198013ms

```

How could it work if i haven't input the pswd and user name from my internet provider? how can i do it?

I also found that i should use 
[http://cables.org.il/ik/cable.tar.gz](http://cables.org.il/ik/cable.tar.gz)
script for my connection for connection but it also didn't work

thx

---

### Post by lswb on 2008-11-25
Try opening a terminal and issue these commands:

sudo dhclient -r eth0

then

sudo dhclient eth0

Copy the output if you can and paste it into your next post.

---

### Post by medusgovs on 2008-11-26
here u go )
> sudo dhclient -r eth0
```
trip@mint445:~$ sudo dhclient -r eth0
[sudo] password for trip: 
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:1b:fc:2a:8f:86
Sending on   LPF/eth0/00:1b:fc:2a:8f:86
Sending on   Socket/fallback


```

> sudo dhclient -r eth0
```
trip@mint445:~$ sudo dhclient eth0
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:1b:fc:2a:8f:86
Sending on   LPF/eth0/00:1b:fc:2a:8f:86
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPOFFER of 172.20.32.218 from 10.168.192.1
DHCPREQUEST of 172.20.32.218 on eth0 to 255.255.255.255 port 67
DHCPACK of 172.20.32.218 from 10.168.192.1
bound to 172.20.32.218 -- renewal in 198270 seconds.
trip@mint445:~$ 


```

thx

---

### Post by medusgovs on 2008-11-26
my working windows conection ipconfig output:
```
Windows IP Configuration

        Host Name . . . . . . . . . . . . : mint445
        Primary Dns Suffix  . . . . . . . : 
        Node Type . . . . . . . . . . . . : Unknown
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No

Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . : 
        Description . . . . . . . . . . . : Realtek RTL8168/8111 PCI-E Gigabit Ethernet NIC
        Physical Address. . . . . . . . . : 00-1B-FC-2A-8F-86
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        IP Address. . . . . . . . . . . . : 172.26.81.127
        Subnet Mask . . . . . . . . . . . : 255.255.224.0
        Default Gateway . . . . . . . . . : 172.26.64.1
        DHCP Server . . . . . . . . . . . : 213.57.35.2
        DNS Servers . . . . . . . . . . . : 192.168.101.101
                                            192.168.101.102
        Lease Obtained. . . . . . . . . . : Wednesday, November 26, 2008 2:42:48 PM
        Lease Expires . . . . . . . . . . : Monday, December 01, 2008 4:06:28 AM


PPP adapter 012 L2TP:

        Connection-specific DNS Suffix  . : 
        Description . . . . . . . . . . . : WAN (PPP/SLIP) Interface
        Physical Address. . . . . . . . . : 00-53-45-00-00-00
        Dhcp Enabled. . . . . . . . . . . : No
        IP Address. . . . . . . . . . . . : 77.126.180.48
        Subnet Mask . . . . . . . . . . . : 255.255.255.255
        Default Gateway . . . . . . . . . : 77.126.180.48
        DNS Servers . . . . . . . . . . . : 80.179.52.100
                                            80.179.55.100
        NetBIOS over Tcpip. . . . . . . . : Disabled

```

---

### Post by lswb on 2008-11-26
I'm sorry but your connection appears more complicated than I first thought and is getting beyond my knowledge level. Apparently it does use some form of ppp or tunneling over ethernet contrary to what I first thought. IS your service provider able to help at all? BTW are you in Israel?

One thing I did see in the tar file you posted, if it is accurate, is that you'll need the pptp-linux package installed. You can get this from the windows side by opening your browser and going to [http://packages.ubuntu.com](http://packages.ubuntu.com). Navigate to networking section for hardy or whatever your version is, and download pptp-linux. Copy the file from windows to your ubuntu desktop or ~/home and you can install it by double-clicking it from the gui or from a terminal by "dpkg -i pptp-linux" while in the same directory the file is located in.

If I can find out anything else I will post again, and please do post if you find the solution. Good luck.

---

### Post by medusgovs on 2008-11-26
Yes i am in Israel. 
I'll keep on googling, the problem is that i have used already about 5 "recepies" and reinstalled the system couple of times this week. I start to feel quite desperate about it. 
The tar file i found was posted in 2006 so i am not sure if it should work in ubuntu 8.1, it didn't work for me.

Probably i'll try to ask some native forums.
thanx
dan

---

### Post by medusgovs on 2008-11-29
Resolved:

1. Download the [dialer]("http://upload-il.com/file/78686/cable.zip.html") (by default made for 012 IP, but can be used with any other)

2. Save it in Home directory and open archive.
```
unzip cable.zip
```

3. Copy the file /cable/scripts/pptp-linux to /usr/sbin
```
sudo cp ./scripts/pptp-linux /usr/sbin
```

4. install (in cable dir)
```
sudo ./Install
```

5. Provide all data you'll be asked in GUI, like:

   IP provided pass
   IP provided username
   IP adress (IP providers in israel you can find [here]("http://penguin.org.il/%D7%9E%D7%93%D7%A8%D7%99%D7%9B%D7%99%D7%9D/%D7%9E%D7%99%D7%93%D7%A2_%D7%A9%D7%99%D7%9E%D7%95%D7%A9%D7%99_%D7%9C%D7%97%D7%99%D7%91%D7%95%D7%A8_%D7%9C%D7%90%D7%99%D7%A0%D7%98%D7%A8%D7%A0%D7%98"))

6.to start the connection 
```
sudo cable-start
```
to stop the connection
```
sudo cable-stop
```

---

### Post by kiran.tambe08 on 2008-11-29
i live in india. hav the same problem do i need a dialer too? plz gimme the link to the driver

---

### Post by medusgovs on 2008-11-29
I am really not sure if you need it.
what driver are you looking for? all the stuff (dialers, and so on) i used besides ubuntu installation cd (downloaded from ubuntu.com) i posted in my previous reply.

---

