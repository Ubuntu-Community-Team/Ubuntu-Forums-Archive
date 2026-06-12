---
title: "d-link dhcp problems"
date: 2007-01-13
forum: Networking &amp; Wireless
---

### Post by slaroy on 2007-01-13
I have a wired ethernet card on my Ubuntu box, a Realtek 8193C.

The modules and everything are loaded correctly. 

The Ubuntu Box (UB) and Windows Box (WB) are connected together at a hub, which are in turn connected to a D-Link DI-604 router running DHCP, which is connected to the cable modem.

I can ping the router and UB from WB. 
I can ping WB from UB.
I cannot ping router from UB, or get an IP address using DHCP.

I ran ethereal to look at the packets, and the router doesn't even return any ICMP packets from UB, so it's not the UB or the ethernet card's fault.

This is driving me crazy! Any ideas?

Thanks,

Steve

---

### Post by gcordoba on 2007-01-14
I got a similar problem.
In my case by using Ubuntu as the only OS I have no problems. I am trying to install Ubuntu in a double OS laptop and in this case using the DHCP option it can not find the automatic IP.
My first thought was that this is a firewall problem, however iptables reported all ports open.
Then I start to think that this could be a bug.
Gustavo

---

### Post by maxamillion on 2007-01-14
```
sudo dhclient
```

1) does this resolve the issue?
2) if not, what output does that command give?

---

### Post by gcordoba on 2007-01-14
Thanks,
I will copy the output (The laptop is beside me):

Listening on LPF/eht1/00:12:f0:16:c5:81
Sending on  LPF/eht1/00:12:f0:16:c5:81
Listening on LPF/eht1/00:11:43:72:94:46
Sending on  LPF/eht1/00:11:43:72:94:46
Sending on  Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received
No working leases in persistent database - sleeping
-------------------------------------------------

I would like to note that  Nerworking  reports incoming trafic.

Gustavo

---

### Post by gcordoba on 2007-01-14
By the way,
Is it looking for the wrong port?
Gustavo

---

### Post by gcordoba on 2007-01-14
Here the ifconfig output:

eth0      Link encap:Ethernet  HWaddr 00:11:43:72:94:46
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:4759 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:315496 (308.1 KiB)  TX bytes:4498 (4.3 KiB)
          Interrupt: 201

eth1      Link encap:Ethernet  HWaddr 00:02:2D:69:18:A9
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14558 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7943 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:177 Base address:dfdfd000-dfdfdfff

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:66 errors:0 dropped:0 overruns:0 frame:0
          TX packets:66 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:5140 (5.0 KiB)  TX bytes:5140 (5.0 KiB)
-------------------------------------------------------------------

Please, note that there is not a inet address in eth0 and there is some RX and TX packets in eth1!

This problem happened when in Dapper and the same happenning after I moved to Edgy.

Gustavo

---

### Post by gcordoba on 2007-01-14
I produced a copy mistake when I copied the dhclient output: The last Listeningg and Sending are directed to eth0 ratehr than eth1. The correct vales are:
Listening on LPF/eht1/00:12:f0:16:c5:81
Sending on LPF/eht1/00:12:f0:16:c5:81
Listening on LPF/eht0/00:11:43:72:94:46
Sending on LPF/eht0/00:11:43:72:94:46
Sending on Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received
No working leases in persistent database - sleeping
----------------------------------------------------------------
Sorry for the mistake,
Gustavo

---

### Post by slaroy on 2007-01-14
I get very similar results from a "sudo dhclient"

```
...
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received
No working leases in persistent database - sleeping
```

Sounds like we have the same problem. Any more ideas?

---

### Post by slaroy on 2007-01-14
Solved!

I poked around at the dhcp packets for Windows and Ubuntu, and I noticed they differed slightly. I tried making the Ubuntu packets the same using /etc/dchp3/dhclient.conf, but that didn't work. So I moved on to the router...

The problem was an old firmware in the D-Link DI-604 router. I upgraded from version 2.18 to 2.20, and "sudo dhclient" worked immediately!

Good luck!

Steve

---

### Post by gcordoba on 2007-01-15
good news.
Unfortunatelly I am at work and the problem is on a home laptop.
This evening I will try with your solution. 
However I do not know how to deal with the router. I need to read a bit...
Gustavo

---

### Post by gcordoba on 2007-01-16
The problem sounds very similar than yours. However,  I couldnt find which version of the firmware I am using. Please, how can I know the kind of network card installed on the computer?
Which firmare I need to download?
Thanks,
Gustavo

---

### Post by slaroy on 2007-01-16
The problem was on the router... In your web browser, go to the address of your router, probably 192.168.0.1, and enter the user name and password. Check the manual for the default settings. 

One of the screens (under tools, I think) will show you the firmware version and give you the option to update it. You will have to download the new firmware from the d-link website. The firmware for the DI-604 wasn't available on the website and I had to email tech support to get it. Once you have the firmware saved, select it from the router's update page, hit the update button, and you're done.

Good luck!

Steve

---

### Post by gcordoba on 2007-01-16
Hi,
sorry for my ignorance, but I have no internet in the laptop source of the problem.
Actally I really do not understand clearly how to get the router data.
netstat -nr produces only blank information:

Kernel   IP   routering   table
Destination   Gateway   Genmask  Flags   MSS Window  irtt  Iface
nortiz@nortiz-laptop:~$

Thanks,
Gustavo

---

### Post by slaroy on 2007-01-16
Are you using a D-link router? Do you have another computer with web access to configure your router?

---

### Post by gcordoba on 2007-01-17
Thanks for your reply Steve,
I have no idea which router I am using. 
I have a commertial broad band service at home and I can use the web in a second laptop which works fine with Ubuntu as the only OS. In that case the same Ubuntu configurates the network automatically, and now with a laptop with double OS Ubuntu seems that it can not deal with it.
Yesterday I tryied http:/192..... without success. How can I know which web address should I use to know the router?
Thanks for your time,
Gustavo

---

### Post by slaroy on 2007-01-18
Do you know if you even have a router? Does your setup look like this?
```

             Cable/DSL Line              Ethernet  Cable               |----PC1
Internet---------------------Modem----------------------Router |----PC2
                                                                                      |----PC3

```
If you don't have a router then your problem is different than mine was. If you do have a router, you'll need to find the user's manual for it in order to find out how to access it. I really can't help you if you don't have that info.

The address to access it will likely be the "gateway address". Fire up your working computer and try to find the gateway address. In Windows, you can find this out by doing start->run->cmd. This will open a command prompt. Then type "ipconfig". I think the command "ifconfig" will show you this info in Linux. Otherwise, check the graphical network setup, and the gateway info should be there.

Cheers,

Steve

---

### Post by gcordoba on 2007-01-18
Thanks, Steve,
I have only one computer:

Internet--------modem-------Laptop

I know the gateway (255.255.248.0). 

Maybe I need to force Ubuntu to accept this gateway by modify some files, however, there are several files with the DNS, gateway, etc, information and I do not know which ones I should modify.

Maybe, any other advice?
Thanks,
Gustavo

---

### Post by slaroy on 2007-01-18
Hi Gustavo,

Sounds to me like your problem is nothing like mine. I started this post because I was having problems with my D-link router, but you don't have a home router at all... 

You said it sounds like you're having the same problem as I am... if the problem is the same, (i.e. the network interface connected your DHCP server doesn't understand your DHCP requests) then the problem is with your ISP's DHCP server, and there's nothing you can do except contact your ISP and ask for their support.

I see that you have two eth interfaces connected (eth0 and eth1). I've never tried running two interfaces at the same time, so maybe the problem is there? Do you have two cards? If so, try removing/unplugging one of them. If you only have one ethernet card connected, then your configuration has a problem and you need to remove one of them from the system.

This is where my expertise runs out. I would suggest trying to post to your own forum and seeing if anyone else can help.

Cheers!

Steve

---

### Post by gcordoba on 2007-01-19
You are all right Steve.
Thanks for your help. I will try to find help neither through a new threat or at other forums.
In all the ways, thanks for your kindness.
Gustavo

---

