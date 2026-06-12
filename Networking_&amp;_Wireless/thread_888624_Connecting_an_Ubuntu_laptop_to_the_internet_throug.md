---
title: "Connecting an Ubuntu laptop to the internet through an XP  PC"
date: 2008-08-13
forum: Networking &amp; Wireless
---

### Post by Tobis84 on 2008-08-13
hi
I hope someone can help me. I'm rather new at networking, but I'm trying to connect my new Zepto 6025WD running Ubuntu 8.04 to the internet via crossover cable through my desktop XP pc.
I have run the XP guide to sharing my internet connection making it the host.
The network icon in my ubuntu taskbar says it has cabled connection, but Firefox makes a timeout trying to connect to any website.

the ifconfig-command in Terminal says
>  ifconfig

eth0      Link encap:Ethernet  HWaddr 00:a0:d1:c2:d3:1b  

          inet addr:192.168.0.219  Bcast:192.168.0.255  Mask:255.255.255.0

          inet6 addr: fe80::2a0:d1ff:fec2:d31b/64 Scope:Link

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:132 errors:0 dropped:0 overruns:0 frame:0

          TX packets:200 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:24499 (23.9 KB)  TX bytes:23849 (23.2 KB)

          Interrupt:19 



lo        Link encap:Local Loopback  

          inet addr:127.0.0.1  Mask:255.0.0.0

          inet6 addr: ::1/128 Scope:Host

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:2014 errors:0 dropped:0 overruns:0 frame:0

          TX packets:2014 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:101284 (98.9 KB)  TX bytes:101284 (98.9 KB)



---

### Post by prshah on 2008-08-13
> **Tobis84 said:**
> but I'm trying to connect my new Zepto 6025WD running Ubuntu 8.04 to the internet via crossover cable through my desktop XP pc. Firefox makes a timeout trying to connect to any website.


You can start by disabling ipv6. Press Alt+F2, then give the command```
gksudo gedit /etc/modprobe.d/blacklist
```, and at the end of the file, add the phrase```
blacklist ipv6
``` Reboot; does the Internet work now? If not, post back, with the results of ifconfig again, as well as the IP address of your Windows PC.

---

### Post by Tobis84 on 2008-08-13
thanks your reply, but it made no change
the new output is here:

> 
eth0      Link encap:Ethernet  HWaddr 00:a0:d1:c2:d3:1b  
          inet addr:192.168.0.219  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3167 (3.0 KB)  TX bytes:5015 (4.8 KB)
          Interrupt:19 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:216 errors:0 dropped:0 overruns:0 frame:0
          TX packets:216 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10800 (10.5 KB)  TX bytes:10800 (10.5 KB)



---

### Post by prshah on 2008-08-13
> **Tobis84 said:**
> thanks your reply, but it made no change
the new output is here:

OK, now lets go to step 2: Are you able to ping your Windows PC? To find out the ipaddress of your Windows PC, Click Start-Run type ```
cmd
```, then press enter. In the black box (command prompt) give the command ```
ipconfig /all
``` (Please post the output here as well, for step 3 if required). 

Now, from your ubuntu pc, open a terminal, then give the command ```
ping -c 5 xxx.xxx.x.xxx
``` (Replace xxx.xxx.x.xxx with the IP address of the Windows machine; if should be  192.168.0.xxx, ie, only the last part should be different). You should get 5 replies with 0% loss in the summary; if you have any doubts, please post the output here.

---

### Post by jimv on 2008-08-13
The address for your Windows machine will be 192.168.0.1.  Try pinging it and see if you get a response.

---

### Post by Tobis84 on 2008-08-13
hi
I pinged the 192.168.0.1 as the adress of my ethernet LAN-connection and got 100% packet loss.

my "ipconfig /all" is in danish so I'll give you the summary in english:

Win IP-configuration:
Hostname:      XX
Primary DNS-suffiks:  (none)
Nodetype: unknown
IP-routing: activated
WINS-proxy: not active

LAN - ethernet :
connection DNS-suffiks: (none)
description: Intel...
MAC:  xx-xx-xx-xx-xx-xx
DHCP: not active
IP: 192.168.0.1
supnet: 255.255.255.0
standard gateway: (none)

Hope that is usefull.

---

### Post by jimv on 2008-08-13
Hrm.  To tell you the truth, I never used a crossover cable when using ICS in Windows, and it works fine.  Do you have a regular cable?

---

### Post by Tobis84 on 2008-08-13
yes. I have. I just switched it and tried pinging my Win-machine. with no luck.

---

### Post by jimv on 2008-08-13
Lets do this:

Run this command:

sudo gedit /etc/network/interfaces

Then look for this:

```
auto eth0
iface eth0 inet dhcp
```

and replace it with this

```

#auto eth0
#iface eth0 inet dhcp

auto eth0
iface eth0 inet static
address 192.168.0.101
netmask 255.255.255.0
network 192.168.0.0
broadcast 192.168.0.255
gateway 192.168.0.1
```

then run this command
```

/etc/inet.d/networking restart
```

---

### Post by Tobis84 on 2008-08-13
all this file says is:

auto lo
iface lo inet loopback

EDIT: and the file and directory for the final command of your guide isn't on my system

---

### Post by jimv on 2008-08-13
Oops, typo in that last command.

Add this to that /etc/network/interfaces file:
```

auto eth0
iface eth0 inet static
address 192.168.0.101
netmask 255.255.255.0
network 192.168.0.0
broadcast 192.168.0.255
gateway 192.168.0.1
```

Then run this command
```

/etc/init.d/networking restart
```

---

### Post by Tobis84 on 2008-08-13
I hate to say it, but pinging my WinXP after this still fails

EDIT: When Firefox tries to connect it says "Address could not be found"
Somethind about the URL couldn't be loaded. It might be something with the DNS-server.
XP's TCP/IP settings for the LAN-connection to the UBUNTU laptop is missing a name for a DNS-server.

---

### Post by prshah on 2008-08-14
> **Tobis84 said:**
> I hate to say it, but pinging my WinXP after this still fails

EDIT: When Firefox tries to connect it says "Address could not be found"
Somethind about the URL couldn't be loaded. It might be something with the DNS-server.
XP's TCP/IP settings for the LAN-connection to the UBUNTU laptop is missing a name for a DNS-server.

Even if it is a DNS server issue, it should still ping the Windows machine successfully. If the Windows machine ping fails:

a) The cable is not proper
b) The hardware (ethernet port) on either end is not proper
c) Windows XP's firewall (or 3rd party equivalent) is blocking pings (unlikely).

Step 3: Give the following command to check cable connectivity```
sudo mii-tool eth0
ifconfig eth0
``` Please post back output of both commands.

---

### Post by Tobis84 on 2008-08-14
I ran the commands and this is the output:

> hje@hje-laptop:~$ sudo mii-tool eth0
[sudo] password for hje: 
eth0: negotiated 1000baseT-FD flow-control, link ok
hje@hje-laptop:~$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:a0:d1:c2:d3:1b  
          inet addr:192.168.0.101  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:106 errors:0 dropped:0 overruns:0 frame:0
          TX packets:41 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:16067 (15.6 KB)  TX bytes:4501 (4.3 KB)
          Interrupt:19 



Is it possible that the encryption on the wlan connection (XP) is conflicting?

---

### Post by Tobis84 on 2008-08-14
Just tried to ping the Ubuntu laptop from the XP-machine and it did OK. No problems there...

---

### Post by jimv on 2008-08-14
Did you enable internet connection sharing on your internet connection, or on the connection to the Ubuntu machine?  Because it needs to be on the internet connection.

---

### Post by Tobis84 on 2008-08-14
yes I did that. but the internet connection is a WLAN connection to an access point.

---

### Post by jimv on 2008-08-14
Ok, lets try this on the XP box.  These steps are off a Microsoft article that says that the Network Setup Wizard sometimes works best for setting up ICS.

1. Click Start, point to All Programs, point to Accessories, point to Communications, and then click Network Setup Wizard.

2. Click Next until you see the Select a connection method screen.

3. Click This computer connects directly to the Internet, and complete the wizard to install ICS.

4.  Reboot when finished.

---

### Post by Tobis84 on 2008-08-17
Hi again.
I have realized that my XP connection to the internet is not a direct connection, but a WLAN connection an Accesspoint. Now I have switched to the crossed cable, reinstalled UBUNTU and typed in a static IP 192.168.0.1 to both the ethernet-connection in XP and the eht0-properties in Ubuntu. 
Now I'm able to ping succesfully fra Ubuntu. But the remaining issue is the DNS settings. They might be wrong... Firefox can't get an adress right

EDIT: Is the final sollution to make a bridge-connection from the WLAN to the wired LAN? in addition to those DNS-settings?

---

