---
title: "internet connection"
date: 2011-01-27
forum: New to Ubuntu
---

### Post by Je'an-Jacq on 2011-01-27
Hi everyone.

I'm new to Ubuntu10.10 so I'm a total newb...
I've got a problem, I am not able to connect to the internet or download any apps... BUT my internet cable is connected correctly to my computer and I can use the internet on WindowsXP service pack2(Im running windows and ubuntu on the same hardrive)anyways I've tried googling it and I cant find a solution:mad: any help to get the intetnet and so on working would be great
Here is some useful information:
 Network adapter-Realtek RTL8139/810x Family PCI Fast Ethernet NIC
 The router I use is a NETGEAR and is DSL
 Oh and I use ADSL

Thanks!

---

### Post by Yougo on 2011-01-27
in the top right corner of your screen, there should be a network indicator. left-click it to see if your network is enabled. in the menu that folds out there should be one or two options at the top. if they are enabled, there's a checkmark in front. if not, left-click once to enable

did that help?

if not, can you open a terminal, and type the commands
```
lspci
```
and
```
ifconfig
```

and copy the output of each to a post, in [code ]puttexthere[/code ] tags?

---

### Post by Je'an-Jacq on 2011-01-27
j[EMAIL="jj@Zoltan:~$"]j@Zoltan:~$[/EMAIL] lspci
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a2)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a2)
00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a2)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:0e.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev 80)
02:00.0 VGA compatible controller: nVidia Corporation GT216 [GeForce GT 220] (rev a2)
02:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)
 

[EMAIL="jj@Zoltan:~$"]jj@Zoltan:~$[/EMAIL] ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:e6:40:bb:7b  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:23 Base address:0xa000 
eth1      Link encap:Ethernet  HWaddr 00:a1:b0:a0:56:af  
          inet6 addr: fe80::2a1:b0ff:fea0:56af/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:194 errors:161 dropped:0 overruns:0 frame:0
          TX packets:35 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:17351 (17.3 KB)  TX bytes:5207 (5.2 KB)
          Interrupt:17 Base address:0x9000 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:328 errors:0 dropped:0 overruns:0 frame:0
          TX packets:328 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:25776 (25.7 KB)  TX bytes:25776 (25.7 KB)
 
 
 
Is this what I was meant to do?

---

### Post by Yougo on 2011-01-27
i'm sorry, i made a slight mistake in my first post. correct instructions are:

in the top right corner of your screen, there should be a network indicator. **right-click **it to see if your network is enabled. in the menu that folds out there should be one or two options at the top. if they are enabled, there's a checkmark in front. if not, left-click once to enable
did this work?

the info you posted tell me ubuntu does see your network cards, but they aren't connected.
could you give me the output of the following command:

```
hwinfo --netcard
```

---

### Post by Je'an-Jacq on 2011-01-28
jj@Zoltan:~$  hwinfo --netcard
The program 'hwinfo' is currently not installed.  You can install it by typing:
sudo apt-get install hwinfo
jj@Zoltan:~$ sudo apt-get install hwinfo
[sudo] password for jj: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package hwinfo
jj@Zoltan:~$ 

I don't think thats right....
If there is a solution to this please let me know 
But I think I just install Ubuntu 10.04 instead, do u think I will have the same problem then??

---

### Post by alphacrucis2 on 2011-01-28
> **Je'an-Jacq said:**
> jj@Zoltan:~$  hwinfo --netcard
The program 'hwinfo' is currently not installed.  You can install it by typing:
sudo apt-get install hwinfo
jj@Zoltan:~$ sudo apt-get install hwinfo
[sudo] password for jj: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package hwinfo
jj@Zoltan:~$ 

I don't think thats right....
If there is a solution to this please let me know 
But I think I just install Ubuntu 10.04 instead, do u think I will have the same problem then??

Well you can't easily install hwinfo without a network connection:lolflag:. Try this command instead:

```
sudo lshw -C network
```

This is just to get information to help diagnose the problem.

By the way, you don't need to install Ubuntu to see if a particular version will work ok with your network card. The Ubuntu live CD has a "try" option where it will boot Ubuntu from the CD without actually installing. It runs slow but allows you to see if it is happy with your hardware.

---

### Post by runeh76 on 2011-01-28
Hi
Try to reset ur router.

---

### Post by Je'an-Jacq on 2011-01-28
jj@Zoltan:~$ sudo lshw -C network
[sudo] password for jj: 
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:01:07.0
       logical name: eth1
       version: 10
       serial: 00:a1:b0:a0:56:af
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: irq:17 ioport:9000(size=256) memory:f6000000-f60000ff memory:80000000-8001ffff
jj@Zoltan:~$

---

### Post by alphacrucis2 on 2011-01-28
> **Je'an-Jacq said:**
> jj@Zoltan:~$ sudo lshw -C network
[sudo] password for jj: 
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:01:07.0
       logical name: eth1
       version: 10
       serial: 00:a1:b0:a0:56:af
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: irq:17 ioport:9000(size=256) memory:f6000000-f60000ff memory:80000000-8001ffff
jj@Zoltan:~$

Curious that it is only showing eth1. eth0 a no show. I presume this PC has two ethernet ports according to the ifconfig you listed. What happens if you try plugging the cable into the second port.

---

### Post by 101011010010 on 2011-01-28
Hello. I run a Realtek RTL-8110SC/8169SC and for some unknown (to me) reason every now and then after a reinstall, 
I have to unplug the ethernet cable from the back of my pc and plug it back in, so it gets recognized.
I hope this helps.

---

### Post by Je'an-Jacq on 2011-01-28
Didn't work:(

---

### Post by runeh76 on 2011-01-28
Did u try to reset router?

---

### Post by Je'an-Jacq on 2011-01-28
I'm not allowed to reset the router because the rest of my family connected to the router will have network issues cause there settings will be messed up


BUT I had the same issue when I installed windows and I found out I needed to change my Link Speed/Duplex Mode to "10 Half Mode" from "100 Full Mode" then it worked...could this have anything to do with my issue...?

---

### Post by runeh76 on 2011-01-28
> **Je'an-Jacq said:**
> I'm not allowed to reset the router because the rest of my family connected to the router will have network issues cause there settings will be messed up


BUT I had the same issue when I installed windows and I found out I needed to change my Link Speed/Duplex Mode to "10 Half Mode" from "100 Full Mode" then it worked...could this have anything to do with my issue...?

"Network adapter-Realtek RTL8139/810x Family PCI Fast Ethernet NIC"

Just becouse that u should try. I think router is problem somehow..

---

### Post by Je'an-Jacq on 2011-01-28
Okay well I'm going away now for the weekend will try when I come back Sunday night:guitar:

---

### Post by runeh76 on 2011-01-28
Ok
Here is useful link to check [https://help.ubuntu.com/community/Router](https://help.ubuntu.com/community/Router)
Check network settings also, u should use eth1 and configure it, so u have way to the router.
I did found lots of problems in google, about NETGEAR..
[URL="https://help.ubuntu.com/community/Router"] 
[/URL]**4.4. Configuring the Internal Network Interfaces**

  
**4.4.1. Wired Only**

 **Append** the following to /etc/network/interfaces and follow the commented out instructions carefully. 
# Set up the internal wired network
#
# Don't forget to change eth1 to the proper name of the internal
# wired network interface if applicable.
#
auto eth1
iface eth1 inet static
    address 192.168.0.1
    network 192.168.0.0
    netmask 255.255.255.0
    broadcast 192.168.0.255[URL="https://help.ubuntu.com/community/Router"]
[/URL]

---

### Post by Je'an-Jacq on 2011-01-31
Sorry dude just remember Im a noob so I might not understand a few things:oops:
BUT what is meant by "/etc/networking/interfaces"?

---

### Post by theozzlives on 2011-01-31
Did you setup your DSL? Right click on the Network Manager (upper right), go to Edit Connections, click the DSL tab and click add. That's where you setup your username, etc. you can click Connect Automatically to maintain your connection.

---

### Post by Je'an-Jacq on 2011-01-31
I'm really confused on what to do....
SO if I cant figure this out, tomorrow I'm going to install Ubuntu 10.04 and check if I don't get the same problem.

---

### Post by runeh76 on 2011-01-31
[https://help.ubuntu.com/7.04/internet/C/connect-to-internet.html#internet-basic-procedure]("https://help.ubuntu.com/7.04/internet/C/connect-to-internet.html#internet-basic-procedure")

---

### Post by Je'an-Jacq on 2011-01-31
Oh Okay =D>
Gonna try this will tell you if it worked soon[-o<

---

### Post by Je'an-Jacq on 2011-01-31
Sorry, but u really cannot figure out what to do....
I need step by step instructions

---

### Post by runeh76 on 2011-01-31
:lolflag:

To connect to the Internet:

Open System &#8594; Administration &#8594; Networking.

Select the connection you wish to use, then click Properties.

Ensure Enable this connection is turned on.

If your ISP or network administrator has given you an IP address, set Configuration to Static IP address, then enter the address in the IP address field and click OK. Otherwise, set Configuration to DHCP and click OK.

To activate or deactivate network connections, select your connection, then click Activate/Deactivate.

---

### Post by Je'an-Jacq on 2011-01-31
When they say Networking are they reffering to "network tools" cause i see no option saying "networking"

---

### Post by runeh76 on 2011-01-31
[http://www.ubuntugeek.com/ubuntu-networking-configuration-using-graphical-tool.html](http://www.ubuntugeek.com/ubuntu-networking-configuration-using-graphical-tool.html)

---

### Post by spook1980 on 2011-01-31
type in ifconfig in terminal n post the output

---

### Post by Je'an-Jacq on 2011-01-31
Busy trying...

---

### Post by spook1980 on 2011-01-31
ok so what is the ip address of your router?
if it's 192.168.0.1 then try this

open up a terminal type in

sudo gedit /etc/network/interfaces

delete whats in there and copy n paste this in the file

auto eth0
iface eth0 inet static
address 192.168.0.25
netmask 255.255.255.0
network 192.168.0.0
broadcast 192.168.0.255
gateway 192.168.0.1

this will give your computer a static ip address of 192.168.0.25
but it should connect to the network

---

### Post by runeh76 on 2011-01-31
> **Je'an-Jacq said:**
> Busy trying...

Im running 10.10 too  ;)
u can install it from package manager, just search "network manager"

---

### Post by Je'an-Jacq on 2011-01-31
Im using ehto 1 and what must i do after I have copied and pasted that?

---

### Post by spook1980 on 2011-01-31
> **spook1980 said:**
> ok so what is the ip address of your router?
if it's 192.168.0.1 then try this

open up a terminal type in

sudo gedit /etc/network/interfaces

delete whats in there and copy n paste this in the file

auto eth0
iface eth0 inet static
address 192.168.0.25
netmask 255.255.255.0
network 192.168.0.0
broadcast 192.168.0.255
gateway 192.168.0.1

this will give your computer a static ip address of 192.168.0.25
but it should connect to the network

you may need to restart your computer to see the effects, if it doesn't work try changing the eth0 to eth1 since i saw that earilyer in the thread it was reporting your network card as eth1

---

### Post by Je'an-Jacq on 2011-01-31
Okay i will try that but what im asking after typing that must i just presss enter or save it or what?

---

### Post by spook1980 on 2011-01-31
just click on file and save then restart your computer

---

### Post by Je'an-Jacq on 2011-01-31
Please stand by will try it now

---

### Post by runeh76 on 2011-01-31
lol 

I was just saying "U need ETH1"

---

### Post by Je'an-Jacq on 2011-01-31
Okay something is wrong now, I did what u said spook and now after restating my PC and booting Ubuntu there is no icon in the top right corner of my screen where the network thing should be

---

### Post by spook1980 on 2011-01-31
> **Je'an-Jacq said:**
> Okay something is wrong now, I did what u said spook and now after restating my PC and booting Ubuntu there is no icon in the top right corner of my screen where the network thing should be
no thats whats supossed to happan as ur no longer using the network manager to manage your connection,did your connection problem get fixed though?

---

### Post by Je'an-Jacq on 2011-01-31
Cant get onto the internet....

---

### Post by spook1980 on 2011-01-31
> **Je'an-Jacq said:**
> Cant get onto the internet....
ok try it again replace the eth0 with eth1 like so since it was stated earilyer in the thread that your computer was using eth1 as the network addaptor
 like so

auto eth1
iface eth1 inet static
address 192.168.0.25
netmask 255.255.255.0
network 192.168.0.0
broadcast 192.168.0.255
gateway 192.168.0.1

and 1 question i got for u, does your computer have 2 network cards in it?

---

### Post by Je'an-Jacq on 2011-01-31
Yes It does, the one is for internet (etho 1) the other for when I LAN computer games with my friends

---

### Post by Je'an-Jacq on 2011-01-31
Internet still not working

---

### Post by spook1980 on 2011-01-31
> **Je'an-Jacq said:**
> Yes It does, the one is for internet (etho 1) the other for when I LAN computer games with my friends

ok if what i gave u with the last time with eth1 don't work try taking out the 2nd ethernet card and then in a terminal type in ifconfig again and post the output,

i once had two ethernet cards in my computer when i duel booted windows as it was almost imposable for me to find a windows driver for my onbored graphics card, i had to remove the 2nd graphics card n run windows in a virtual machine do to the problems i was having

---

### Post by Je'an-Jacq on 2011-01-31
i cant remove the other one cause it is connected to my mother board, and if i remove the other one it wont be able to go onto the internet at all

---

### Post by spook1980 on 2011-01-31
> **Je'an-Jacq said:**
> i cant remove the other one cause it is connected to my mother board, and if i remove the other one it wont be able to go onto the internet at all

can't u plug in the ethernet cord into the onboard ethernet port?

---

### Post by Je'an-Jacq on 2011-01-31
Yes I can

---

### Post by Je'an-Jacq on 2011-01-31
What now?:confused:
oh ya I'm stuck with 10.10 cause  my computer for some reason cant download big files anymore

---

### Post by runeh76 on 2011-01-31
Dude go to package manager (System > Administration > Synaptic Package Manager) and install network manager. When u get that icon (upper right), then u can easily configure ur adsl. Just look this what i allready posted. [http://www.ubuntugeek.com/ubuntu-networking-configuration-using-graphical-tool.html]("http://www.ubuntugeek.com/ubuntu-networking-configuration-using-graphical-tool.html")

Im not router expert, but i think ur router should give u IP, so u can try to make "default" adsl-connection with automatic DHCP. If its not working like that, u should try to Static IP address settings, same what u did from terminal, but now type those IP.s (IP,Subnet mask,Gateway) to network manager. Everything this u find from that link. Somebody correct this if im wrong.

If u dont know ur router IP (gateway), have a look at this [http://www.adslrouter.co.za/ip-address.html]("http://www.adslrouter.co.za/ip-address.html")

---

### Post by Je'an-Jacq on 2011-02-01
Searched for network mannager and all the "Network Mangers" are already installed...

---

### Post by runeh76 on 2011-02-01
Oh...

Right-click top-panel and select **add to panel**
Next choose second from top **application starter** (dont know if its exactly right those words) and click forward-button.
Next find **Settings** and under that is **Network-manager**

Now u SHOULD have that icon..?

---

### Post by Je'an-Jacq on 2011-02-01
Cant find the heading "settings"

---

### Post by runeh76 on 2011-02-01
preferences?

---

### Post by Je'an-Jacq on 2011-02-01
okay found it
 
First step: Add DSL??

---

### Post by runeh76 on 2011-02-01
If u have icon now?? Yeah add Wired (first left) and check (IPV4) if DHCP is set automatic. Close network-manager and left-click icon and choose ur connection. If u dont have it..reboot and try again.

---

### Post by Je'an-Jacq on 2011-02-01
Still dont have it...
I couldn't find the right one.
Think its time i download 10.04........10.10 has to many bugs
what do u think?

---

### Post by runeh76 on 2011-02-01
dang..did u reboot?? U have that NETGEAR-router, check this link..there is same problem and router [http://ubuntuforums.org/showthread.php?t=488779]("http://ubuntuforums.org/showthread.php?t=488779")
Dont give up yet! :)

---

### Post by heron7 on 2011-02-01
try this ,turn your router off close your pc , wait 5min  ,restart your outer let it find a 'connection'  1min, start up your pc ):P

---

### Post by runeh76 on 2011-02-01
Founded another trick, how to add that icon to panel.
Same thing, click top-panel and add "Notification Area" OR System -> Preferences -> Startup Applications

---

### Post by Je'an-Jacq on 2011-02-02
Did something really stupid, I by mistake deleted the top thing.... So Im really screwed

---

### Post by Je'an-Jacq on 2011-02-06
So what now? Will i have to reinstall Ubuntu?

---

### Post by Je'an-Jacq on 2011-02-13
Hello??????????

---

