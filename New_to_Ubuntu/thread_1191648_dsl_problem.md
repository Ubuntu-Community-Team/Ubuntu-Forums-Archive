---
title: "dsl problem"
date: 2009-06-19
forum: New to Ubuntu
---

### Post by sadinsudin on 2009-06-19
i recently install ubuntu 9.04, it nice but i can't connect to internet , i already tried using the 'sudo pppoeconf ' but i couldn't...pls help

---

### Post by falkTX on 2009-06-19
hmm... don't the network systray/applet work?
It never failed on me

---

### Post by sadinsudin on 2009-06-19
before this i've follow one of the solution from this forum which stated below

"I've heard that (launchpad.net) if you use pppoeconf in Ubuntu 9.04 Jaunty, you cannot connect to the internet. 
You must use Network Manager ONLY to configure your internet settings.

Try this:

Code:

sudo apt-get --purge remove pppoeconf

I've tried it and it works. I can connect to the internet now."

but until now i still can't connect to internet . and even worse i can not use the terminal use the 'sudo pppoeconf' *sigh*...

---

### Post by falkTX on 2009-06-19
is it wireless?

What usually I do is click on the Network-Manager systray then choose "Auto eth0"

---

### Post by sadinsudin on 2009-06-19
> **falkTX said:**
> hmm... don't the network systray/applet work?
It never failed on me
sorry i'm new here, what u mean by network ssystray/applet , is it the small window with wired/vpn/dsl etc tabs..?
if it is, i already tried to configure in the dsl tab...but it seems no response..

---

### Post by sadinsudin on 2009-06-19
nope, i i'm using the cat5 direct from the adsl router from the provider
it work fine in win XP and before this i try ubuntu 8.01(i not remember..) and i have no prob to connect to internet..but the 9.04 version i seems cause me trouble..

---

### Post by wpshooter on 2009-06-19
> **sadinsudin said:**
> nope, i i'm using the cat5 direct from the adsl router from the provider
it work fine in win XP and before this i try ubuntu 8.01(i not remember..) and i have no prob to connect to internet..but the 9.04 version i seems cause me trouble..

Ask your DSL provider if you router/modem needs a firmware upgrade.

---

### Post by scrooge_74 on 2009-06-19
If you are using a cable diretcly it should not be giving you problems, unless it is not detecting your network card.

Open a console window and type ifconfig, and then post it here so someone can give you a hand.

Also try rebooting the router (if you havent done so already), sometimes router gets confuse when you use PC in one OS and then restart and use another OS (dont know why).

---

### Post by bobbob1016 on 2009-06-19
Open a terminal, type "ifconfig" post the results.  It will say something like "...Gateway 192.168.1.254..." (that is what mine is on Bellsouth), type that in Firefox, it should give you a page where you can enter your username and password.  Easier than dealing with pppoe.

---

### Post by sadinsudin on 2009-06-19
ok.. below are the results:

1. the router is off
   [FONT=Arial][SIZE=2]
[/SIZE][/FONT]
[FONT=Arial][SIZE=2]zahir@tuanpunya-laptop:~$ sudo ifconfig[/SIZE][/FONT]
    [FONT=Arial][SIZE=2][sudo] password for zahir: [/SIZE][/FONT]
    [FONT=Arial][SIZE=2]eth0      Link encap:Ethernet  HWaddr 00:16:d3:aa:35:a9  [/SIZE][/FONT]
    [FONT=Arial][SIZE=2]          inet6 addr: fe80::216:d3ff:feaa:35a9/64 Scope:Link[/SIZE][/FONT]
    [FONT=Arial][SIZE=2]          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1[/SIZE][/FONT]
    [FONT=Arial][SIZE=2]          RX packets:0 errors:0 dropped:0 overruns:0 frame:0[/SIZE][/FONT]
    [FONT=Arial][SIZE=2]          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0[/SIZE][/FONT]
    [FONT=Arial][SIZE=2]          collisions:0 txqueuelen:1000 [/SIZE][/FONT]
    [FONT=Arial][SIZE=2]          RX bytes:0 (0.0 B)  TX bytes:492 (492.0 B)[/SIZE][/FONT]
    [FONT=Arial][SIZE=2]          Interrupt:17 [/SIZE][/FONT]
    [FONT=Arial][SIZE=2] [/SIZE][/FONT]
  [FONT=Arial][SIZE=2] [/SIZE][/FONT]
  [FONT=Arial][SIZE=2]lo        Link encap:Local Loopback  [/SIZE][/FONT]
    [FONT=Arial][SIZE=2]          inet addr:127.0.0.1  Mask:255.0.0.0[/SIZE][/FONT]
    [FONT=Arial][SIZE=2]          inet6 addr: ::1/128 Scope:Host[/SIZE][/FONT]
    [FONT=Arial][SIZE=2]          UP LOOPBACK RUNNING  MTU:16436  Metric:1[/SIZE][/FONT]
    [FONT=Arial][SIZE=2]          RX packets:20 errors:0 dropped:0 overruns:0 frame:0[/SIZE][/FONT]
    [FONT=Arial][SIZE=2]          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0[/SIZE][/FONT]
    [FONT=Arial][SIZE=2]          collisions:0 txqueuelen:0 [/SIZE][/FONT]
    [FONT=Arial][SIZE=2][FONT=&quot]          RX bytes:1424 (1.4 KB)  TX bytes:1424 (1.4 KB)[/FONT][/SIZE][/FONT]

2. the router is on[FONT=Arial][SIZE=2]

[/SIZE][/FONT]    [FONT=Arial][SIZE=2]zahir@tuanpunya-laptop:~$ sudo pon dsl-provider[/SIZE][/FONT]
    [FONT=Arial][SIZE=2]Plugin rp-pppoe.so loaded.[/SIZE][/FONT]
    [FONT=Arial][SIZE=2]RP-PPPoE plugin version 3.8p compiled against pppd 2.4.5[/SIZE][/FONT]
    [FONT=Arial][SIZE=2]zahir@tuanpunya-laptop:~$ sudo ifconfig[/SIZE][/FONT]
    [FONT=Arial][SIZE=2]eth0      Link encap:Ethernet  HWaddr 00:16:d3:aa:35:a9  [/SIZE][/FONT]
    [FONT=Arial][SIZE=2]          inet6 addr: fe80::216:d3ff:feaa:35a9/64 Scope:Link[/SIZE][/FONT]
    [FONT=Arial][SIZE=2]          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1[/SIZE][/FONT]
    [FONT=Arial][SIZE=2]          RX packets:10 errors:0 dropped:0 overruns:0 frame:0[/SIZE][/FONT]
    [FONT=Arial][SIZE=2]          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0[/SIZE][/FONT]
    [FONT=Arial][SIZE=2]          collisions:0 txqueuelen:1000 [/SIZE][/FONT]
    [FONT=Arial][SIZE=2]          RX bytes:606 (606.0 B)  TX bytes:1132 (1.1 KB)[/SIZE][/FONT]
    [FONT=Arial][SIZE=2]          Interrupt:17 [/SIZE][/FONT]
    [FONT=Arial][SIZE=2] [/SIZE][/FONT]
  [FONT=Arial][SIZE=2] [/SIZE][/FONT]
  [FONT=Arial][SIZE=2]lo        Link encap:Local Loopback  [/SIZE][/FONT]
    [FONT=Arial][SIZE=2]          inet addr:127.0.0.1  Mask:255.0.0.0[/SIZE][/FONT]
    [FONT=Arial][SIZE=2]          inet6 addr: ::1/128 Scope:Host[/SIZE][/FONT]
    [FONT=Arial][SIZE=2]          UP LOOPBACK RUNNING  MTU:16436  Metric:1[/SIZE][/FONT]
    [FONT=Arial][SIZE=2]          RX packets:20 errors:0 dropped:0 overruns:0 frame:0[/SIZE][/FONT]
    [FONT=Arial][SIZE=2]          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0[/SIZE][/FONT]
    [FONT=Arial][SIZE=2]          collisions:0 txqueuelen:0 [/SIZE][/FONT]
    [FONT=Arial][SIZE=2]          RX bytes:1424 (1.4 KB)  TX bytes:1424 (1.4 KB)[/SIZE][/FONT]
    [FONT=Arial][SIZE=2] [/SIZE][/FONT]
  [FONT=Arial][SIZE=2] [/SIZE][/FONT]
  [FONT=Arial][SIZE=2]ppp0      Link encap:Point-to-Point Protocol  [/SIZE][/FONT]
    [FONT=Arial][SIZE=2]          inet addr:2.2.2.119  P-t-P:1.1.1.1  Mask:255.255.255.255[/SIZE][/FONT]
    [FONT=Arial][SIZE=2]          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1[/SIZE][/FONT]
    [FONT=Arial][SIZE=2]          RX packets:4 errors:0 dropped:0 overruns:0 frame:0[/SIZE][/FONT]
    [FONT=Arial][SIZE=2]          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0[/SIZE][/FONT]
    [FONT=Arial][SIZE=2]          collisions:0 txqueuelen:3 [/SIZE][/FONT]
    [FONT=Arial][SIZE=2][FONT=&quot]          RX bytes:46 (46.0 B)  TX bytes:52 (52.0 B)

[/FONT][/SIZE][/FONT]
3. when i put pppoeconfig command in the terminal


   [FONT=Arial][SIZE=2]zahir@tuanpunya-laptop:~$ sudo pppoefconfig[/SIZE][/FONT]
    [FONT=Arial][SIZE=2]sudo: pppoefconfig: command not found[/SIZE][/FONT]
    [FONT=Arial][SIZE=2]zahir@tuanpunya-laptop:~$ sudo pppoefconf[/SIZE][/FONT]
    [FONT=Arial][SIZE=2]sudo: pppoefconf: command not found[/SIZE][/FONT]
    [FONT=Arial][SIZE=2]zahir@tuanpunya-laptop:~$ sudo pppoeconf[/SIZE][/FONT]
    [FONT=Arial][SIZE=2]sudo: pppoeconf: command not found[/SIZE][/FONT]
    [FONT=Arial][SIZE=2][FONT=&quot]zahir@tuanpunya-laptop:~$ [/FONT][/SIZE][/FONT]
  
[SIZE=2][FONT=Arial]>> hope this will help you guys out there to help me...thx..[/FONT][/SIZE]

---

### Post by scrooge_74 on 2009-06-19
I'm not sure if this applies to your situation, check post #5 in the following thread,

[http://ubuntuforums.org/showthread.php?p=3619063#post3619063](http://ubuntuforums.org/showthread.php?p=3619063#post3619063)

---

### Post by bobbob1016 on 2009-06-19
1st, really bad habit to add "sudo" infront of commands.  I meant run "ifconfig" not "sudo ifconfig".

2nd, do you have a router AND a modem, or just a modem?  Basically, I am checking if you even need pppoeconf, since you can probably set the modem to connect for you, like I've been doing since 2003 when I got my 2nd DSL modem.

Run "ifconfig" with the PC right into the modem, and the modem turned on.  You should see something with "192.168.x.x" the x's will be replaced with numbers, the last one will probably be either 1 or 254.  Punch that into firefox, for example, 192.168.1.254, with the modem on, and plugged right into your computer.  You should get a screen that lets you enter your username and password in there, then click connect.  You now won't have to worry about pppoeconf.

---

### Post by sadinsudin on 2009-06-20
i'll already done what u told me to do..i think i've been followed the instructions accordingly but yet the results are not as aspected...below is the result when i entered the ifconfig in the terminal..

   [FONT=Arial][SIZE=2]zahir@tuanpunya-laptop:~$ ifconfig[/SIZE][/FONT]
    [FONT=Arial][SIZE=2]eth0      Link encap:Ethernet  HWaddr 00:16:d3:aa:35:a9  [/SIZE][/FONT]
    [FONT=Arial][SIZE=2]          inet6 addr: fe80::216:d3ff:feaa:35a9/64 Scope:Link[/SIZE][/FONT]
    [FONT=Arial][SIZE=2]          UP BROADCAST MULTICAST  MTU:1500  Metric:1[/SIZE][/FONT]
    [FONT=Arial][SIZE=2]          RX packets:16 errors:0 dropped:0 overruns:0 frame:0[/SIZE][/FONT]
    [FONT=Arial][SIZE=2]          TX packets:22 errors:0 dropped:0 overruns:0 carrier:0[/SIZE][/FONT]
    [FONT=Arial][SIZE=2]          collisions:0 txqueuelen:1000 [/SIZE][/FONT]
    [FONT=Arial][SIZE=2]          RX bytes:966 (966.0 B)  TX bytes:1516 (1.5 KB)[/SIZE][/FONT]
    [FONT=Arial][SIZE=2]          Interrupt:17 [/SIZE][/FONT]
    
  
  [FONT=Arial][SIZE=2]lo        Link encap:Local Loopback  [/SIZE][/FONT]
    [FONT=Arial][SIZE=2]          inet addr:127.0.0.1  Mask:255.0.0.0[/SIZE][/FONT]
    [FONT=Arial][SIZE=2]          inet6 addr: ::1/128 Scope:Host[/SIZE][/FONT]
    [FONT=Arial][SIZE=2]          UP LOOPBACK RUNNING  MTU:16436  Metric:1[/SIZE][/FONT]
    [FONT=Arial][SIZE=2]          RX packets:20 errors:0 dropped:0 overruns:0 frame:0[/SIZE][/FONT]
    [FONT=Arial][SIZE=2]          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0[/SIZE][/FONT]
    [FONT=Arial][SIZE=2]          collisions:0 txqueuelen:0 [/SIZE][/FONT]
    [FONT=Arial][SIZE=2]          RX bytes:1424 (1.4 KB)  TX bytes:1424 (1.4 KB)[/SIZE][/FONT]
    
  
  [FONT=Arial][SIZE=2]ppp0      Link encap:Point-to-Point Protocol  [/SIZE][/FONT]
    [FONT=Arial][SIZE=2]          inet addr:**2.2.2.139**  P-t-P:1.1.1.1  Mask:255.255.255.255[/SIZE][/FONT]
    [FONT=Arial][SIZE=2]          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1[/SIZE][/FONT]
    [FONT=Arial][SIZE=2]          RX packets:4 errors:0 dropped:0 overruns:0 frame:0[/SIZE][/FONT]
    [FONT=Arial][SIZE=2]          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0[/SIZE][/FONT]
    [FONT=Arial][SIZE=2]          collisions:0 txqueuelen:3 [/SIZE][/FONT]
    [FONT=Arial][SIZE=2][FONT=&quot]          RX bytes:46 (46.0 B)  TX bytes:52 (52.0 B)

>> what i can found is the "[/FONT][/SIZE][/FONT][FONT=Arial][SIZE=2]inet addr:**2.2.2.139" .. **(but i myself doubt it..since it not as you told me).. and i all also paste the numbers in the add box in the firefox..and below is the result

[/SIZE][/FONT]    The server at 2.2.2.139 is taking too long to respond.

---

### Post by sadinsudin on 2009-06-20
by the way..i found it weird when i plug in the cable into the network card..there seems no graphic changes at the right upper side of the desktop( where suppose it shows the "flying light" to show that the machine is receiving signals from the modem-as i experienced in ubuntu 8.10) 

>> or should i reinstall it or even use the ubuntu 8.10( but i really hope that ubuntu experts out there could solve this problem for goods..)

---

### Post by bobbob1016 on 2009-06-20
> **sadinsudin said:**
> i'll already done what u told me to do..i think i've been followed the instructions accordingly but yet the results are not as aspected...below is the result when i entered the ifconfig in the terminal..

   [FONT=Arial][SIZE=2]zahir@tuanpunya-laptop:~$ ifconfig[/SIZE][/FONT]
    [FONT=Arial][SIZE=2]eth0      Link encap:Ethernet  HWaddr 00:16:d3:aa:35:a9  [/SIZE][/FONT]
    [FONT=Arial][SIZE=2]          inet6 addr: fe80::216:d3ff:feaa:35a9/64 Scope:Link[/SIZE][/FONT]
    [FONT=Arial][SIZE=2]          UP BROADCAST MULTICAST  MTU:1500  Metric:1[/SIZE][/FONT]
    [FONT=Arial][SIZE=2]          RX packets:16 errors:0 dropped:0 overruns:0 frame:0[/SIZE][/FONT]
    [FONT=Arial][SIZE=2]          TX packets:22 errors:0 dropped:0 overruns:0 carrier:0[/SIZE][/FONT]
    [FONT=Arial][SIZE=2]          collisions:0 txqueuelen:1000 [/SIZE][/FONT]
    [FONT=Arial][SIZE=2]          RX bytes:966 (966.0 B)  TX bytes:1516 (1.5 KB)[/SIZE][/FONT]
    [FONT=Arial][SIZE=2]          Interrupt:17 [/SIZE][/FONT]
    
  
  [FONT=Arial][SIZE=2]lo        Link encap:Local Loopback  [/SIZE][/FONT]
    [FONT=Arial][SIZE=2]          inet addr:127.0.0.1  Mask:255.0.0.0[/SIZE][/FONT]
    [FONT=Arial][SIZE=2]          inet6 addr: ::1/128 Scope:Host[/SIZE][/FONT]
    [FONT=Arial][SIZE=2]          UP LOOPBACK RUNNING  MTU:16436  Metric:1[/SIZE][/FONT]
    [FONT=Arial][SIZE=2]          RX packets:20 errors:0 dropped:0 overruns:0 frame:0[/SIZE][/FONT]
    [FONT=Arial][SIZE=2]          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0[/SIZE][/FONT]
    [FONT=Arial][SIZE=2]          collisions:0 txqueuelen:0 [/SIZE][/FONT]
    [FONT=Arial][SIZE=2]          RX bytes:1424 (1.4 KB)  TX bytes:1424 (1.4 KB)[/SIZE][/FONT]
    
  
  [FONT=Arial][SIZE=2]ppp0      Link encap:Point-to-Point Protocol  [/SIZE][/FONT]
    [FONT=Arial][SIZE=2]          inet addr:**2.2.2.139**  P-t-P:1.1.1.1  Mask:255.255.255.255[/SIZE][/FONT]
    [FONT=Arial][SIZE=2]          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1[/SIZE][/FONT]
    [FONT=Arial][SIZE=2]          RX packets:4 errors:0 dropped:0 overruns:0 frame:0[/SIZE][/FONT]
    [FONT=Arial][SIZE=2]          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0[/SIZE][/FONT]
    [FONT=Arial][SIZE=2]          collisions:0 txqueuelen:3 [/SIZE][/FONT]
    [FONT=Arial][SIZE=2][FONT=&quot]          RX bytes:46 (46.0 B)  TX bytes:52 (52.0 B)

>> what i can found is the "[/FONT][/SIZE][/FONT][FONT=Arial][SIZE=2]inet addr:**2.2.2.139" .. **(but i myself doubt it..since it not as you told me).. and i all also paste the numbers in the add box in the firefox..and below is the result

[/SIZE][/FONT]    The server at 2.2.2.139 is taking too long to respond.

Well, no, "sudo ifconfig" and "ifconfig" isn't the same thing, and definitely not the same when you do it with the cable unplugged.  It seems like pppoeconf has changed some settings, but someone else with more experience with pppoeconf should be able to help with that.

---

### Post by halitech on 2009-06-20
whats the output of
```
lspci
```and ```
cat /etc/network/interfaces
```

Also, what type of modem/router do you have?

---

### Post by sadinsudin on 2009-06-20
[SIZE=2]as instructed i already put the command in the terminal, and the result as below:-

[/SIZE]    [FONT=Arial][SIZE=2]zahir@tuanpunya-laptop:~$ lspci[/SIZE][/FONT]
    [FONT=Arial][SIZE=2]00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)[/SIZE][/FONT]
    [FONT=Arial][SIZE=2]00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)[/SIZE][/FONT]
    [FONT=Arial][SIZE=2]00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)[/SIZE][/FONT]
    [FONT=Arial][SIZE=2]00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)[/SIZE][/FONT]
    [FONT=Arial][SIZE=2]00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)[/SIZE][/FONT]
    [FONT=Arial][SIZE=2]00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)[/SIZE][/FONT]
    [FONT=Arial][SIZE=2]00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)[/SIZE][/FONT]
    [FONT=Arial][SIZE=2]00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)[/SIZE][/FONT]
    [FONT=Arial][SIZE=2]00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)[/SIZE][/FONT]
    [FONT=Arial][SIZE=2]00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)[/SIZE][/FONT]
    [FONT=Arial][SIZE=2]00:05.0 VGA compatible controller: nVidia Corporation C51 [Geforce 6150 Go] (rev a2)[/SIZE][/FONT]
    [FONT=Arial][SIZE=2]00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)[/SIZE][/FONT]
    [FONT=Arial][SIZE=2]00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)[/SIZE][/FONT]
    [FONT=Arial][SIZE=2]00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)[/SIZE][/FONT]
    [FONT=Arial][SIZE=2]00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)[/SIZE][/FONT]
    [FONT=Arial][SIZE=2]00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)[/SIZE][/FONT]
    [FONT=Arial][SIZE=2]00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)[/SIZE][/FONT]
    [FONT=Arial][SIZE=2]00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)[/SIZE][/FONT]
    [FONT=Arial][SIZE=2]00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)[/SIZE][/FONT]
    [FONT=Arial][SIZE=2]00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)[/SIZE][/FONT]
    [FONT=Arial][SIZE=2]00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)[/SIZE][/FONT]
    [FONT=Arial][SIZE=2]00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)[/SIZE][/FONT]
    [FONT=Arial][SIZE=2]00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration[/SIZE][/FONT]
    [FONT=Arial][SIZE=2]00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map[/SIZE][/FONT]
    [FONT=Arial][SIZE=2]00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller[/SIZE][/FONT]
    [FONT=Arial][SIZE=2]00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control[/SIZE][/FONT]
    [FONT=Arial][SIZE=2]05:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller[/SIZE][/FONT]
    [FONT=Arial][SIZE=2]05:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)[/SIZE][/FONT]
    [FONT=Arial][SIZE=2]05:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)[/SIZE][/FONT]
    [FONT=Arial][SIZE=2]05:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)[/SIZE][/FONT]
    [FONT=Arial][SIZE=2]05:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)[/SIZE][/FONT]
    [FONT=Arial][SIZE=2] [/SIZE][/FONT]
  [FONT=Arial][SIZE=2]zahir@tuanpunya-laptop:~$ cat /etc/network/interfaces[/SIZE][/FONT]
    [FONT=Arial][SIZE=2]auto lo[/SIZE][/FONT]
    [FONT=Arial][SIZE=2]iface lo inet loopback[/SIZE][/FONT]
          [FONT=Arial][SIZE=2]  
[/SIZE][/FONT]
  [FONT=Arial][SIZE=2]auto dsl-provider[/SIZE][/FONT]
    [FONT=Arial][SIZE=2]iface dsl-provider inet ppp[/SIZE][/FONT]
    [FONT=Arial][SIZE=2]pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf[/SIZE][/FONT]
    [FONT=Arial][SIZE=2]provider dsl-provider[/SIZE][/FONT]
    [FONT=Arial][SIZE=2] [/SIZE][/FONT]
    [FONT=Arial][SIZE=2]auto eth0[/SIZE][/FONT]
    [FONT=Arial][SIZE=2]iface eth0 inet manual[/SIZE][/FONT]


[FONT=Arial][SIZE=2]>> for your info i'm using the ADSL router(as printed on the router..)[/SIZE][/FONT]
[FONT=Arial][SIZE=2]>>hoping a good news from u guys..8-[
[/SIZE][/FONT]
    [SIZE=2]
[/SIZE]

---

### Post by halitech on 2009-06-20
is your network card an internal card or a usb adapter?

here is my interfaces file
```
daryl@debian:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
allow-hotplug eth0
iface eth0 inet dhcp
```

---

### Post by sadinsudin on 2009-06-20
> **halitech said:**
> is your network card an internal card or a usb adapter?



i'm using the internal network card, v3415au compaq machine, it work fine with the ubuntu 8.10 before..

should i reinstall the ubuntu 9.04 (which i never done it before..) or any other advice..

---

### Post by sadinsudin on 2009-06-22
after long hours of thinking and trying, then i decided to uninstall the ubuntu 9.04 then install the ubuntu 8.04...and guess what? it works with charms!!! for those guys who try to solve my  dsl-connection problem, i'll like to say zillion thanks..pls do not hesitate to give your assistance for ubuntu newbies like me in the future yet to come!..

---

