---
title: "Ethernet help please"
date: 2005-11-13
forum: Networking &amp; Wireless
---

### Post by %hMa@?b&lt;C on 2005-11-13
I have verizon dsl and a westell modem... it wont work
```
crowell@ubuntu:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface
iface eth0 inet dhcp

auto eth0
crowell@ubuntu:~$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:40:2B:67:44:6F
          inet addr:192.168.1.47  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::240:2bff:fe67:446f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:51 errors:0 dropped:0 overruns:0 frame:0
          TX packets:99 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:5348 (5.2 KiB)  TX bytes:10467 (10.2 KiB)
          Interrupt:17 Base address:0x2000

crowell@ubuntu:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
crowell@ubuntu:~$

```
Ive got that stuff... any suggestions/help this is a linux only machine that i want to use and cant wait to get it up and running

---

### Post by %hMa@?b&lt;C on 2005-11-13
if it helps my modem is a westell 2200, and i am really very new to linux (2nd day) and really need to connect to the internet. Please just give me the simpliest way possible.

---

### Post by TimelessRogue on 2005-11-13
Okay, folks ... it couldn't be any simpler:  Plug in all together per Verizons ample instructions and boot up Ubuntu.  That's just how simple it is ... and was when I hooked up just three weeks ago.  They even supply all the ethernet cable and such.  Now, I can't recall if the process insisted on using IE or not but I don't so didn't.  I didn't even need to edit my /etc/network/interfaces file!

Oh, and don't get antsy ... wait 'til Verizon notifies you that your DSL account has been activated else you won't get anything anyway and you'll think you did it all wrong.

Have fun !!!

PS:  This is what my interfaces file looks like:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth1

# The primary network interface
iface eth1 inet dhcp
	# wireless-* options are implemented by the wireless-tools package
	wireless-mode managed
	wireless-essid any

auto eth1

iface eth0 inet dhcp

auto eth0

---

### Post by %hMa@?b&lt;C on 2005-11-13
my account has been activated months ago... and i cant get it to work... it is working right now on my XP computer, but wont work on my linux one. also i cant run the installer because i dotn have wine, because i cant connect

---

### Post by %hMa@?b&lt;C on 2005-11-13
also when i am plugged in and am starting up, it hangs on connecting to the clock at ubuntu.org or something like that... it leaves the GUI and goes to only text and wont continue booting

---

### Post by mips on 2005-11-13
jeffc313,

Does the modem/router run in bridged or routed mode ? ie. Did you have to install PPPoE on the XP machine or is it simply configured for dhcp & auto DNS ?

If you are connected via Ethernet cable and the westell device is running in routed mode then the only things you should have to configure the LAN card TCP/IP settings for is to obtain an IP address & DNS servers via dhcp.

---

### Post by %hMa@?b&lt;C on 2005-11-13
sorry for being a total noob, but how do you tell what mode it is running in? and could you please give me instructions on how to do both?
[QUOTE=mips]jeffc313,

Does the modem/router run in bridged or routed mode ? ie. Did you have to install PPPoE on the XP machine or is it simply configured for dhcp & auto DNS ?

If you are connected via Ethernet cable and the westell device is running in routed mode then the only things you should have to configure the LAN card TCP/IP settings for is to obtain an IP address & DNS servers via dhcp.[/QUOTE]

---

### Post by mips on 2005-11-14
> sorry for being a total noob, but how do you tell what mode it is running in?

answer:
> Does the modem/router run in bridged or routed mode ? **[COLOR="Red"]ie. Did you have to install PPPoE on the XP machine or is it simply configured for dhcp & auto DNS ?[/COLOR]**

> also i cant run the installer because i dont have wine, because i cant connect

What installer are you referring to and what does it install ?


Please turn your router/modem over and give me the model number B90-2200xx-04 where xx=10 or 15 or 30. I need the model number to get the manual for your device. That way we both have the same frame of reference.

The verizon support site is pretty useless for a non verzon subscriber as it requires the first 6 digits of a phone number...

---

### Post by %hMa@?b&lt;C on 2005-11-14
I have no idea what it installs... i think nothing as i tried it with my xp box and all it did is tell me how to connect the ethernet cable.
THe router is exactly this
Model: A90-220015-04
Rev: R

Thanks so much for the help
[QUOTE=mips]answer:




What installer are you referring to and what does it install ?


Please turn your router/modem over and give me the model number B90-2200xx-04 where xx=10 or 15 or 30. I need the model number to get the manual for your device. That way we both have the same frame of reference.

The verizon support site is pretty useless for a non verzon subscriber as it requires the first 6 digits of a phone number...[/QUOTE]

---

### Post by mips on 2005-11-14
Does the XP machine connect via USB or Ethernet ???

Open a terminal session from Application->Accesories->Terminal and enter the following 'ping xxx.xxx.xxx.xxx" commands

Can you ping the router ?
ping 192.168.0.1

Can you ping the following two sites:
ping 64.233.161.147
ping 198.133.219.25
ping 151.203.0.85

Can you ping the following host names:
ping [www.google.com](www.google.com)
ping [www.cisco.com](www.cisco.com)
ping boston2-qwest.bellatlantic.net

---

### Post by %hMa@?b&lt;C on 2005-11-14
XP machine connects via ethernet
ill try the pings and report back


[QUOTE=mips]Does the XP machine connect via USB or Ethernet ???

Open a terminal session from Application->Accesories->Terminal and enter the following 'ping xxx.xxx.xxx.xxx" commands

Can you ping the router ?
ping 192.168.0.1

Can you ping the following two sites:
ping 64.233.161.147
ping 198.133.219.25
ping 151.203.0.85

Can you ping the following host names:
ping [www.google.com](www.google.com)
ping [www.cisco.com](www.cisco.com)
ping boston2-qwest.bellatlantic.net[/QUOTE]

---

### Post by %hMa@?b&lt;C on 2005-11-14
```
crowell@ubuntu:~$ ping 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
From 192.168.1.1 icmp_seq=1 Destination Host Unreachable
From 192.168.1.1 icmp_seq=2 Destination Host Unreachable

--- 192.168.0.1 ping statistics ---
2 packets transmitted, 0 received, +2 errors, 100% packet loss, time 1000ms

crowell@ubuntu:~$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=0.464 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=64 time=0.438 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=64 time=0.447 ms

--- 192.168.1.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 1999ms
rtt min/avg/max/mdev = 0.438/0.449/0.464/0.026 ms
crowell@ubuntu:~$ ping 64.233.161.147
PING 64.233.161.147 (64.233.161.147) 56(84) bytes of data.
From 192.168.1.1 icmp_seq=1 Destination Host Unreachable
From 192.168.1.1 icmp_seq=2 Destination Host Unreachable
From 192.168.1.1 icmp_seq=3 Destination Host Unreachable

--- 64.233.161.147 ping statistics ---
3 packets transmitted, 0 received, +3 errors, 100% packet loss, time 2001ms

crowell@ubuntu:~$ ping www.google.com

```
thats what i got

---

### Post by mips on 2005-11-15
Ok, do me a favour.

Startup XP while connected to the network, open a command prompt and enter "**ipconfig /all**", copy the output and paste it here please.

Things are going to slow at the current rate, need to speed things up a bit.

I assume your router IP address is 192.168.1.1 from the ping outputs ?

---

### Post by mips on 2005-11-15
Ok, looks like the problem lies on the router side. Please still provide the above info. Thing is I have no idea how the XP machine connects, PPPoE or straight IP via DHCP ?

Have the following information ready, you dont have to post sensitive info:
Router manual
Router Username & Password.
Verizon Username & Password
Connection Type: PPPoE, PPPoA etc
VPI & VCI values
DNS info.

---

### Post by %hMa@?b&lt;C on 2005-11-15
[QUOTE=mips]Ok, do me a favour.

Startup XP while connected to the network, open a command prompt and enter "**ipconfig /all**", copy the output and paste it here please.

Things are going to slow at the current rate, need to speed things up a bit.

I assume your router IP address is 192.168.1.1 from the ping outputs ?[/QUOTE]
my router is 192.168.1.1
and 
from ipconfig /all nothing shows up
I had to do ipconfig /eth0 to get anything to show up
```
Microsoft Windows XP [Version 5.1.2600]
(C) Copyright 1985-2001 Microsoft Corp.

C:\Documents and Settings\Owner>ipconfig /all
^C
C:\Documents and Settings\Owner>ipconfig
^C
C:\Documents and Settings\Owner>ipconfig/all
^C
C:\Documents and Settings\Owner>ipconfig /eth0

Error: unrecongnized or incomplete command line.

USAGE:
    ipconfig [/? | /all | /renew [adapter] | /release [adapter] |
              /flushdns | /displaydns | /registerdns |
              /showclassid adapter |
              /setclassid adapter [classid] ]

where
    adapter         Connection name
                   (wildcard characters * and ? allowed, see examples)

    Options:
       /?           Display this help message
       /all         Display full configuration information.
       /release     Release the IP address for the specified adapter.
       /renew       Renew the IP address for the specified adapter.
       /flushdns    Purges the DNS Resolver cache.
       /registerdns Refreshes all DHCP leases and re-registers DNS names
       /displaydns  Display the contents of the DNS Resolver Cache.
       /showclassid Displays all the dhcp class IDs allowed for adapter.
       /setclassid  Modifies the dhcp class id.

The default is to display only the IP address, subnet mask and
default gateway for each adapter bound to TCP/IP.

For Release and Renew, if no adapter name is specified, then the IP address
leases for all adapters bound to TCP/IP will be released or renewed.

For Setclassid, if no ClassId is specified, then the ClassId is removed.

Examples:
    > ipconfig                   ... Show information.
    > ipconfig /all              ... Show detailed information
    > ipconfig /renew            ... renew all adapters
    > ipconfig /renew EL*        ... renew any connection that has its
                                     name starting with EL
    > ipconfig /release *Con*    ... release all matching connections,
                                     eg. "Local Area Connection 1" or
                                         "Local Area Connection 2"

C:\Documents and Settings\Owner>
```
im not really sure why it just hangs on ipconfig /all, it works only on ipconfig /?

---

### Post by mips on 2005-11-15
Something here is not right.

Let me think about this and get back to you.

Do you have a second machine connected to the internet and maybe we can do this live via IRC ?

---

### Post by %hMa@?b&lt;C on 2005-11-15
sorry, i have two machines, but they share the same power supply... so i really couldn't do it via irc adn work on my linux one

---

### Post by BionicBigfoot on 2005-11-23
This may sound silly but have you tried booting up as admin and going into the terminal and typing

sudo pppoeconf

That worked for me. It prompts you to enter your user name and your passoword for your ppoe connection.

---

### Post by %hMa@?b&lt;C on 2005-11-25
[QUOTE=BionicBigfoot]This may sound silly but have you tried booting up as admin and going into the terminal and typing

sudo pppoeconf

That worked for me. It prompts you to enter your user name and your passoword for your ppoe connection.[/QUOTE]
i will try this, i know that my machine is pppoe.

---

### Post by %hMa@?b&lt;C on 2005-11-25
[QUOTE=BionicBigfoot]This may sound silly but have you tried booting up as admin and going into the terminal and typing

sudo pppoeconf

That worked for me. It prompts you to enter your user name and your passoword for your ppoe connection.[/QUOTE]
thanks bigfoot, I am up and running wiht ubuntu now!

---

