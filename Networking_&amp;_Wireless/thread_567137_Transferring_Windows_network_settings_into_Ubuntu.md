---
title: "Transferring Windows network settings into Ubuntu"
date: 2007-10-04
forum: Networking &amp; Wireless
---

### Post by starbase1 on 2007-10-04
Hello All,
I have two PC's side by side. When I boot both into Windows they network nicely over a crossover Lan cable, using basic networking, and being able to read and write each others disks, and the one without a modem can use the other ones modem connection to access the internet.

I want to boot one of them into Ubuntu, (the one with no modem), and have it connect to the XP machine, in the same way it does under XP. So I can then get at the disks shared on the Ubunu box, and the Ubuntu box can get at the shares and the internet connection on the XP box.

Is there a step by step guide, suitable for an Ubuntu newbie to achieve this?

I have not yet moved onto the Gutsy Gibbon. (But I am looking forward to it!)
Cheers,
Nick

---

### Post by soul_rebel on 2007-10-04
it may work with no configuration at all... have you tried?

---

### Post by starbase1 on 2007-10-04
It did not spot anything as it came up, and I was not sure how to start a 'probe' or whatever to make it look around...

As I said i's about as simple and standard as a network can get!

---

### Post by soul_rebel on 2007-10-04
you are trying to do many things. Here are the single steps:
1: plug the network cable and get an IP address (the network-manager in ubuntu pops a message saying that you are connected)
2: access the internet
3: access the shares of the win pc from ubuntu
4: access ubuntu from windows

1 and 2 involve correct routing in the windows pc and a dhcp server (windows or modem), ubuntu should need no configuration for that.

Can you test point 1 and possibly 2?

---

### Post by starbase1 on 2007-10-04
Hi Sr, and thanks for the input. I thought it might help to describe the end state I am aiming for, it would be seriously handy to share data across the machines, but I think I need to get the internet connected, (and Ubuntu does not like my old adsl modem!), so I was hoping to get that started over the lan...

Anyway, when I bring  up Ubuntu, I do not see any messages about the LAN.

When I select places / network I can see an icon for Windows Network, but when I double click it I get 0 items shown.

When I look at network settings under system, there's a tick by 'wired connection' so I guess it has detected something...

Sorry, I am completely clueless with this!
Nick

---

### Post by loneduke on 2007-10-05
for sharing internet, you just bridge your network with your modem and set the ip adress and the dns for the bridged connection, but to share files, i think someone who better in networking can help..

---

### Post by soul_rebel on 2007-10-05
step one: plug the cable... that should do something in the upper right corner of your screen. Possibly post the connection informations (right click on the 2 tiny computers).
step two: try to access the internet, eg open a web page.

These are the things I need you to try first.

---

### Post by starbase1 on 2007-10-05
Loneduke - Err, I reverse the polarity on the dilithium crystals?!?! Sorry, don't understand.

Soul-Rebel

Ok, I booted into Linux with the cable out. Ubuntu reported "no network connection" near the top right.
I put the cable in, it changed to a small animated icon for about 30 seconds, then put up the message "You are now connected to a wired network", and when I wave the mouse over it, I get "wired network connection", so I think the everything is connected successfully.

And when I do the equivalent at the windows end, that too shos the network is connected.

I went to the "network" and "windows network" was found, but nothing that helped me underneath. I took a screen grab, and have stick it on my web pages here:
[http://www.starbase1.co.uk/screenshot.jpg](http://www.starbase1.co.uk/screenshot.jpg)

I tried using the web, but it did not get through...

'm guessing everything is connected OK, but there perhaps I need to tell each end about the other? Being thick, I did not set up my own windows network!

---

### Post by soul_rebel on 2007-10-06
I don't think that the connection is ok. After a long time a network-manager will use some "plug and play" settings, so that two computers can network with no configuration. This will not work with windows and internet access, so we have to investigate the issue.
We need to check what IP addresses the pcs are using.

let's do it in text mode, ok? 
fire up a terminal and write:
```
ifconfig eth0
```
you can copy that into a file or make a screenshot or anything else that you can show me.

while on windows you do: start, run, write "cmd" in the box. The terminal pops out and in that you do:
```
ipconfig
```
and also a ```
route print
```
(note iPconfig vs iFconfig)

This will give me all the infos about your network settings. We won't try the rest until we have networking functional.

I am sorry it's taking so long, but don't worry I am going to help you to the end of this.

---

### Post by Sturmeh on 2007-10-06
I too have a primarly windows network, when booted into windows, I can interface with 5 other Windows PC's ( 4 XP, 1 Vista )...

How ever when I boot into ubuntu, I can only see workgroups, and have no luck accessing them, even though i have passwords to most of the windows boxes on the network.

I connect to the internet using a Wireless Router, so i'm not sharing a internet connection with windows, but it works.

I'm trying to get samba to work, I would like access to Windows Shares on my network.

( When I try to add shares manually, the computers come up, and request passwords, even if i put correct details, nothing ever happens. :/ )

Any insight?

---

### Post by starbase1 on 2007-10-06
Hi Soul Rebel, much appreciated!

Here is the info:

From Ubuntu:
ubuntu@ubuntu:~$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:18:F3:5D:D2:54  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14 errors:0 dropped:0 overruns:0 frame:0
          TX packets:51 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:1621 (1.5 KiB)  TX bytes:10931 (10.6 KiB)

ubuntu@ubuntu:~$ 

And from the windows end:
C:\DOCUME~1\OWNER>ipconfig

Windows IP Configuration


Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . :
        IP Address. . . . . . . . . . . . : 192.168.1.1
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . :

PPP adapter Pipex connection:

        Connection-specific DNS Suffix  . :
        IP Address. . . . . . . . . . . . : 212.241.132.79
        Subnet Mask . . . . . . . . . . . : 255.255.255.255
        Default Gateway . . . . . . . . . : 212.241.132.79

C:\DOCUME~1\OWNER>

C:\DOCUME~1\OWNER>route print
===========================================================================
Interface List
0x1 ........................... MS TCP Loopback interface
0x10003 ...00 0e a6 86 c1 aa ...... VIA Rhine II Fast Ethernet Adapter - Determ
nistic Network Enhancer Miniport
0x20004 ...00 53 45 00 00 00 ...... WAN (PPP/SLIP) Interface
===========================================================================
===========================================================================
Active Routes:
Network Destination        Netmask          Gateway       Interface  Metric
          0.0.0.0          0.0.0.0   212.241.132.79  212.241.132.79       1
    62.72.136.140  255.255.255.255   212.241.132.79  212.241.132.79       1
        127.0.0.0        255.0.0.0        127.0.0.1       127.0.0.1       1
      192.168.1.0    255.255.255.0      192.168.1.1     192.168.1.1       20
      192.168.1.1  255.255.255.255        127.0.0.1       127.0.0.1       20
    192.168.1.255  255.255.255.255      192.168.1.1     192.168.1.1       20
   212.241.132.79  255.255.255.255        127.0.0.1       127.0.0.1       50
  212.241.132.255  255.255.255.255   212.241.132.79  212.241.132.79       50
        224.0.0.0        240.0.0.0      192.168.1.1     192.168.1.1       20
        224.0.0.0        240.0.0.0   212.241.132.79  212.241.132.79       1
  255.255.255.255  255.255.255.255      192.168.1.1     192.168.1.1       1
  255.255.255.255  255.255.255.255   212.241.132.79  212.241.132.79       1
Default Gateway:    212.241.132.79
===========================================================================
Persistent Routes:
  None

C:\DOCUME~1\OWNER>

Hope that makes sense!
Nick

---

### Post by soul_rebel on 2007-10-06
@Sturmeh adding shares manually *should* work, I don't know what to say...

@starbase1
ok, it's seems that ubuntu has no IP configured. The cable was in, right?
If yes we are going to create a manual configuration.
Here's an howto: [http://www.ubuntugeek.com/ubuntu-networking-configuration-using-graphical-tool.html]("http://www.ubuntugeek.com/ubuntu-networking-configuration-using-graphical-tool.html")

you need to put in:
address 192.168.1.2
mask. 255.255.255.0
gateway: 192.168.1.1

in the dns tab you should put your dns servers, which can be found somewhere in the windows settings, I don't remember where...
Anyhow if you don't find them just use these two: 208.67.222.222 and 208.67.220.220 (opendns)

After this you should have internet access, and possibly "see" the other pc. Try this command: nautilus smb://192.168.1.1

---

### Post by starbase1 on 2007-10-06
I'm sure the cable is plugged in, the icon top right of screen reacts when I plug it in or pull it out.


Ok, found the web page, found the tab.

I select connection settings, choose static IP. I type in the IP address you told me to, it prompts with the subnet mask you told me, which I accept.

Initially it greyed out the OK button when I tried to enter the final number, but I did verything carefully again and I now have a working net connection! 

Brilliant,thanks and I owe you a generous dose of the beverage of your choice if you ever come to London!

And after tying the other command you told me, I find I can see shared folders on the other Windows machine. This is really great!

What is involved in sharing folders on the Ubuntu machine so the Windows machine can see them?

Nick

---

### Post by soul_rebel on 2007-10-06
I appreciate your gratitude... Should I come to London the beverage would be beer :)

For sharing folders from ubuntu, the program is samba. System -> Administration -> shared folders will install and configure everything. 

For later customizations you will find plenty of howtos on the web (now you can surf it!)
see you

---

### Post by starbase1 on 2007-10-06
An excellent choice sir!

The link to Samba worked just fine - all if a sudden I can really see the strengths of Ubuntu, as it updates stuff it needs over the net. I had a ciuple of trys before, but without a net connection it was frustrating to say the least.

Anyway, I have a new CPU and motherboard, and what with the next final release of Ubuntu due really soon, I think it is sensible for me to go for the full hard disk installation with the new version, on the new hardware.

I really wanted to be confident this would work before I started, not least because I strongly suspect that those nice people at Microsoft will expect me to pay for another copy of XP if I upgrade my hardware... And I'm really hoping that they won't see money for an OS from me again...

---

