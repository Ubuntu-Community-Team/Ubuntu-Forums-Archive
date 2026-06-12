---
title: "Problems in connecting to internet"
date: 2009-07-01
forum: New to Ubuntu
---

### Post by parth.s on 2009-07-01
I just installed ubuntu 9.04 a few days back with windows XP in dual-boot.And as this might tell i am totally new to ubuntu.I read the "ubuntutip-do this first of all" and the first step itself is establishing an internet connection.
I use a broadband internet connection,which is provided by my isp through LAN,my ip address is dynamic using dhcp.So to connect to the internet i have to dial up with username and password etc.I want to know what is the method of connecting to the net in ubuntu.
i also read somewhere that i have to release my ip address in xp and then log in ubuntu to recognize my ip address.Ubuntu aotomatically connects to the network...the network manager shows it as Auto etho0.But when i go to network tools and select my ethernet card (my mobo is asus p5nmx with nvidia chipset) this is some of the info it shows...i have attached screenshots.Please guide me about the next step.

---

### Post by Michael.Godawski on 2009-07-01
hey,

wired (LAN) connections are usually configured automatically as explained here:


[LIST]
[*][https://help.ubuntu.com/9.04/internet/C/connecting-wired.html](https://help.ubuntu.com/9.04/internet/C/connecting-wired.html)
[/LIST]
Can you please post some more info, just open up the terminal and run these commands, copy the output and post it here:

```
ifconfig
cat /etc/network/interfaces
sudo lshw -C network
```

The last command requires your login password (which will not be display as you type).

---

### Post by parth.s on 2009-07-01
parth@parth-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1f:c6:11:31:d7  
          inet addr:192.168.0.183  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fec0::9:21f:c6ff:fe11:31d7/64 Scope:Site
          inet6 addr: 2002:cbc0:ee85:9:21f:c6ff:fe11:31d7/64 Scope:Global
          inet6 addr: fe80::21f:c6ff:fe11:31d7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:537 errors:0 dropped:0 overruns:0 frame:0
          TX packets:44 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:66081 (66.0 KB)  TX bytes:7303 (7.3 KB)
          Interrupt:251 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)
parth@parth-desktop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

parth@parth-desktop:~$ sudo lshw -C network
[sudo] password for parth: 
  *-network               
       description: Ethernet interface
       product: MCP73 Ethernet
       vendor: nVidia Corporation
       physical id: f
       bus info: pci@0000:00:0f.0
       logical name: eth0
       version: a2
       serial: 00:1f:c6:11:31:d7
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 duplex=full ip=192.168.0.183 latency=0 link=yes maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: e2:e7:80:3e:38:aa
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes



also this is the output of the ipconfig in windows
Windows IP Configuration



        Host Name . . . . . . . . . . . . : spur-94fbe14f9a

        Primary Dns Suffix  . . . . . . . : 

        Node Type . . . . . . . . . . . . : Mixed

        IP Routing Enabled. . . . . . . . : No

        WINS Proxy Enabled. . . . . . . . : No



Ethernet adapter Local Area Connection:



        Connection-specific DNS Suffix  . : 

        Description . . . . . . . . . . . : NVIDIA nForce Networking Controller

        Physical Address. . . . . . . . . : 00-1F-C6-11-31-D7

        Dhcp Enabled. . . . . . . . . . . : Yes

        Autoconfiguration Enabled . . . . : Yes

        Autoconfiguration IP Address. . . : 169.254.34.58

        Subnet Mask . . . . . . . . . . . : 255.255.0.0

        Default Gateway . . . . . . . . . :

---

### Post by carml on 2009-07-01
> **parth.s said:**
> 
I use a broadband internet connection,which is provided by my isp through LAN,my ip address is dynamic using dhcp.So to connect to the internet i have to dial up with username and password etc.

Install Gnome PPPon from Applications->Add/remove to automate your connection to the isp,or get a look at System->Help & Support->Internet for more info and/or instructions.
I hope this can help you :)

---

### Post by parth.s on 2009-07-01
Whenever is try to intall any app. it demands connection to the internet.
also why does it show "never" besides the connection name (i have attached the screen shot) in network connections.Also when i try to edit it in the Ipv4 settings it needs dhcp client Id..what is it?

i have all posted the ipconfig output...please guide me.

---

### Post by carml on 2009-07-01
You have to type```
sudo pppoeconf
``` in order to run the wizard to allow the connection to your ISP,once you've done,if you install Gnome PPPon you'll automate this procedure,so you'll connect with a single click.

---

### Post by parth.s on 2009-07-02
i cannot install a single app. without internet connection...

plzz guys this is my first problem with ubuntu and im stuck already

---

### Post by carml on 2009-07-02
Connect your cable to the Ethernet.turn on the modem or whatelse you use,then under Ubuntu go to Applications->Accessories->Terminal and type```
sudo pppoeconf
``` follow the instructions on screen and you'll get connected to the web.
Once you've done install Gnome PPPon to automate the process.
If all go well you've done with your ISP :).

---

### Post by parth.s on 2009-07-03
Thanks for replying carml..i did as you specified.It created a new connection...a dsl one..and also the network is now showing disconnected...which was connected previously....also now it shows a new network device in the network tools..plus the commands "poff" and "pon-dslprovider"(i aslo typed my isp provider name),result in "kill command cannot be performed"

---

### Post by carml on 2009-07-03
If I recall correctly PPPoeconf is a script,not a process,so you can't kill it.
I'm glad you solved your problem :).

---

