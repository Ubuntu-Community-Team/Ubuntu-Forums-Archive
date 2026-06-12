---
title: "Please help, im hopeless!!!"
date: 2007-09-16
forum: Networking &amp; Wireless
---

### Post by dollarside on 2007-09-16
Dear people,
   i installed ubuntu couple of times now, now i did it again, but the internet doesnt work. im using a router and my ubuntu is fiesty fawn. i did not do anything to anything yet, and the connection icon on the top right (with two little computer screen) as this exclamation mark sign on it. my roaming mode is enabled (i dint enable it, it was like that already) and my DNS has nothing in it. and the host and stuff is confusing. i know all u experts out there know how to do this, please just help me!:confused:

Thanks in advance,

TG

---

### Post by overdrank on 2007-09-17
> **dollarside said:**
> Dear people,
   i installed ubuntu couple of times now, now i did it again, but the internet doesnt work. im using a router and my ubuntu is fiesty fawn. i did not do anything to anything yet, and the connection icon on the top right (with two little computer screen) as this exclamation mark sign on it. my roaming mode is enabled (i dint enable it, it was like that already) and my DNS has nothing in it. and the host and stuff is confusing. i know all u experts out there know how to do this, please just help me!:confused:

Thanks in advance,

TG

HI could you give us some information on your system, are you using wireless or a wired connection? Also what is the model of your networking card? You can use the command in the terminal  ```
lspci
``` the terminal is located under applications, accessories, terminal  and paste the output here and maybe we can help.

---

### Post by Junglizer on 2007-09-17
lspci, then recompile the kernel... well thats how *I* fix stuff. But to start post the *lspci* out put, along with *ifconfig* output. That way we can get a handle on what hardware you have and how you are trying to connect.

---

### Post by dollarside on 2007-09-18
aright thanks ill do it now

---

### Post by dollarside on 2007-09-18
here is what was on my whole terminal:






joe@ubuntu:~$ lspci


00:00.0 Host bridge: ALi Corporation M1697 HTT Host Bridge
00:01.0 

PCI bridge: ALi Corporation PCI Express Root Port
00:02.0 PCI bridge: ALi Corporation 

PCI Express Root Port
00:03.0 PCI bridge: ALi Corporation PCI Express Root Port
00:04.0 

PCI bridge: ALi Corporation PCI Express Root Port
00:11.0 PCI bridge: ALi Corporation 

M5249 HTT to PCI Bridge
00:12.0 Ethernet controller: ALi Corporation ULi 1689,1573 

integrated ethernet. (rev 60)
00:13.0 USB Controller: ALi Corporation USB 1.1 Controller 

(rev 03)
00:13.1 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:13.2 USB 

Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:13.3 USB Controller: ALi 

Corporation USB 2.0 Controller (rev 01)
00:14.0 Audio device: ALi Corporation High 

Definition Audio/AC'97 Host Controller (rev 01)
00:15.0 ISA bridge: ALi Corporation PCI to 

LPC Controller (rev 10)
00:15.1 Bridge: ALi Corporation M7101 Power Management 

Controller [PMU]
00:16.0 IDE interface: ALi Corporation M5229 IDE (rev c7)
00:16.1 IDE 

interface: ALi Corporation ULi M5288 SATA
00:18.0 Host bridge: Advanced Micro Devices 

[AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host 

bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host 

bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 

Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: ATI Technologies Inc RV515 [Radeon X1300]
01:00.1 

Display controller: ATI Technologies Inc RV515 [Radeon X1300] (Secondary)

---

### Post by dollarside on 2007-09-20
I tried some commands but it still doesnt work

---

### Post by callan79 on 2007-09-20
> **dollarside said:**
>  i installed ubuntu couple of times now, now i did it again, but the internet doesnt work. im using a router and my ubuntu is fiesty fawn. i did not do anything to anything yet, and the connection icon on the top right (with two little computer screen) as this exclamation mark sign on it. my roaming mode is enabled (i dint enable it, it was like that already) and my DNS has nothing in it. and the host and stuff is confusing.


Hi dollarside,

Couple of questions :

 - are you connected to your router via ethernet cable, and is the corresponding router status
   light on to show you have link?
 - what sort of router do you have? do you have access to the router's control panel?

As a general rule, most ADSL/Cable routers run NAT internally. The router has an IP Address, say 192.168.1.1 as a default. The router will automatically assign an IP Address (say 192.168.1.2) to your computer when the computer starts.

But sometimes this feature can be turned off so you might need to manually specify the settings.

So what you need to find out :

 - What is the IP Address and Subnet Mask of your router. Example 192.168.1.1 and 255.255.255.0
 - Set your computer up (in System >> Administration >> Network) with the SAME SUBNET
   MASK, and the IP Address should have the first 3 numbers the same, then the last numbers
   different (so, 192.168.1.5). Set your GATEWAY to the router's IP Address.


If you can post some more details about your router perhaps I can help more.

Also, I have no idea what ROAMING MODE does - mine is disabled, and my router works fine.

Good luck!
Callan

---

### Post by Somnus07 on 2007-09-20
Hello, I think I have a similar problem, my NIC is also an ALi integrated ethernet and I can not connect to a network/internet from Kubuntu 7.04 (Feisty) but can from windows xp.

I have attached a file with some common requests to connection problems.  I have just joined a university network and should be able to get the IP from the DHCP.  I have tried manually configuring the connection but then it looses the default gateway and goes back to an old IP address (ie the 169.254.7.218).  I used the numbers that were in windows for the gateway and even for the IP, but to no avail.

If anyone could help that would be great.  I have only been using linux for the last few months, so be gentle please.

Thanks,
Somnus

---

### Post by Somnus07 on 2007-09-25
Hey i sorted my problem by buying a new network card (for about £7) and using that instead of the integrated Ali one on the motherboard.  Apparently the integrated one can be a bit funny on ubuntu when connected by wire (ie ethernet cable).

hope this helps,
Somnus

---

