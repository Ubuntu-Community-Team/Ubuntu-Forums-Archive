---
title: "Sick of Aircrack-ng"
date: 2008-04-06
forum: Networking &amp; Wireless
---

### Post by ASAHU on 2008-04-06
I\'ve tried numerous ways to get airodump-ng to work. This includes: 
using the KILL command on the NM applet.
Trying to use kismet and destroying the ath0 connection and starting a new ath1 connection.
Looking around the ubuntu forums for a new way to find a solution to this problem.

Info: I only use NM applet and that\'s it. I have a TP LINK card that has an atheros chipset. Aircrack-ng works in other Linux oses. Just ubuntu doesn\'t like me. Can anyone help me?

---

### Post by equity on 2008-04-06
Could you please be a little bit more specific.
What exactly does not work with airodump-ng for you??

To kill the nm-applet, write "sudo killall nm-applet" in a shell.
Then:

sudo ifconfig <interface> down
sudo ifconfig <interface> up
sudo iwconfig <interface> mode monitor
sudo airodump-ng <interface>


^^ write these commands in a shell and post the output. Then we will see where is the problem.

---

### Post by ASAHU on 2008-04-06
I don\'t understand your method. Neither does Ubuntu. Why do you ifconfig device down, then ifconfig device up? Personal details have been left out in the following shell and MAC Addresses and AP\'s have been changed to bogus values:
xxxxx@Linux:~$ sudo killall nm-applet
[sudo] password for xxxxx:
xxxxx@Linux:~$ sudo ifconfig ath0 down
xxxxx@Linux:~$ sudo ifconfig ath1 up
ath1: ERROR while getting interface flags: No such device
xxxxx@Linux:~$ wlanconfig ath1 create wlandev wifi0
wlanconfig: ioctl: Operation not permitted
xxxxx@Linux:~$ sudo wlanconfig ath1 create wlandev wifi0
wlanconfig: ioctl: Input/output error
xxxxx@Linux:~$ sudo ifconfig ath0 up
xxxxx@Linux:~$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:11:22:33:44:55  
          inet addr:192.168.1.106  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::219:e0ff:fe68:60b3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:20369 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16448 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:22100604 (21.0 MB)  TX bytes:3156378 (3.0 MB)

eth0      Link encap:Ethernet  HWaddr 00:11:22:33:44:55  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:18 Base address:0x2800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wifi0     Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:93902 errors:0 dropped:0 overruns:0 frame:35209
          TX packets:17564 errors:9 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:29885872 (28.5 MB)  TX bytes:3659702 (3.4 MB)
          Interrupt:16 

xxxxx@Linux:~$ sudo iwconfig ath0 mode monitor
Error for wireless request \"Set Mode\" (8B06) :
    SET failed on device ath0 ; Invalid argument.
xxxxx@Linux:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:\"xxxxxxxx\"  Nickname:\"\"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:11:22:33:44:55   
          Bit Rate:36 Mb/s   Tx-Power:18 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=23/70  Signal level=-67 dBm  Noise level=-90 dBm
          Rx invalid nwid:9223  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

xxxxx@Linux:~$ iwconfig --help
Usage: iwconfig [interface]
                interface essid {NNN|any|on|off}
                interface mode {managed|ad-hoc|master|...}
                interface freq N.NNN[k|M|G]
                interface channel N
                interface bit {N[k|M|G]|auto|fixed}
                interface rate {N[k|M|G]|auto|fixed}
                interface enc {NNNN-NNNN|off}
                interface key {NNNN-NNNN|off}
                interface power {period N|timeout N|saving N|off}
                interface nickname NNN
                interface nwid {NN|on|off}
                interface ap {N|off|auto}
                interface txpower {NmW|NdBm|off|auto}
                interface sens N
                interface retry {limit N|lifetime N}
                interface rts {N|auto|fixed|off}
                interface frag {N|auto|fixed|off}
                interface modulation {11g|11a|CCK|OFDMg|...}
                interface commit 
       Check man pages for more details.
xxxxx@Linux:~$ sudo airodump-ng ath0
ioctl(SIOCSIWMODE) failed: Invalid argument
Error setting monitor mode on ath0

*#%)#%)#)%#)%(#%*)#(%*#()*($)*()@*_!*($)*@#)(*$()@#*$()#
This is what I used to do to get my card to use airodump-ng:

airmon-ng start wifi0 
airodump-ng --ivs --write Dumpfile ath1

Oh, the joys and perils of Ubuntu make it the best OS ever ^_^. (sarcasm)

---

### Post by equity on 2008-04-06
Lol, you permanently confused ath0 and ath1. "iwconfig" is only for configuring wireless adapters, you cannot use this program on a wired ethernet device.
To me it looks like ath0 is your wired connection and ath1 is your wireless extension, isn't it?

In the past I found out when restarting an interface it is more likely to work, so when someone got trouble I first suggest to restart the device.

So shut down your wired device "ath0" and type all the commands I posted in my previous post replacing "<interface>" with "ath1" and post the output.


P. S.: Please disable smileys, especially when posting code.

---

### Post by ASAHU on 2008-04-06
If you can explain to me how an athX atheros chipset can ever be a wired connection, I\'d love to hear about it.

---

### Post by equity on 2008-04-06
Aaaah.. damn...

The point is for me airodump-ng works as good as all other programs of the aircrack suite do and when I type these commands I have given to you airodump-ng shows me all APs and clients connected to them with a lot of details.

Just shut down your wired ethernet device (however it is called in your system) and precede the commands I have already given to you.

---

### Post by ASAHU on 2008-04-07
I don\'t use an ethernet cable, even though the port is there. Nevertheless, I tried to use ifconfig eth0 down, and it did nothing at all to help.

---

### Post by equity on 2008-04-07
I have not said anything about some ethernet cable. I said shut down your device for cabled ethernet.

Look, just shut down any network interfaces except loopback "lo" so that when you type the command **ifconfig** the only shown network interface is your loopback device.

Then type these commands:

[B]sudo ifconfig ath0 up
sudo iwconfig ath0 mode monitor
sudo airodump-ng ath0[/B]

and post the in- and output if it does not work.

---

### Post by equity on 2008-04-07
Okay, I have just had a closer look on your code.
Looks like the exact problem is that your WLAN adapter does not switch to monitor mode.

Type:
[B]sudo ifconfig ath0 up
sudo iwconfig ath1 mode monitor[/B]

If this works, procede with the commands I posted in my prior post. If it does not, ask some network expert why your card is unable to switch to monitor mode.

---

### Post by wieman01 on 2008-04-07
Have you patched your wireless device so that it understands monitor mode & packet reinjection? If not, you won't succeed.

---

### Post by ASAHU on 2008-04-08
xxxxx@Linux:~$ sudo ifconfig ath0 up
[sudo] password for xxxxx:
xxxxx@Linux:~$ ifconfig
ath0      Link encap:Ethernet  HWaddr xxxxxxxxxxxxxxxx  
          inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: xxxxxxxxxxxxxxxx Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:49560 errors:0 dropped:0 overruns:0 frame:0
          TX packets:33869 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:58472885 (55.7 MB)  TX bytes:4328282 (4.1 MB)

eth0      Link encap:Ethernet  HWaddr xxxxxxxxxxxxxxxxxxxx 
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:18 Base address:0x800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wifi0     Link encap:UNSPEC  HWaddr xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:420500 errors:0 dropped:0 overruns:0 frame:5429
          TX packets:38501 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:94514167 (90.1 MB)  TX bytes:5539823 (5.2 MB)
          Interrupt:16 

xxxxx@Linux:~$ sudo iwconfig ath1 mode monitor
Error for wireless request "Set Mode" (8B06) :
    SET failed on device ath1 ; No such device.


Wieman, it worked on other linux oses out of the box.

---

### Post by aeiah on 2008-04-08
you did:
sudo ifconfig ath0 up

so why did you then do:
sudo iwconfig ath1 mode monitor?

it should be ath0 surely

---

### Post by equity on 2008-04-08
^^ this is exactly the point that confused me once.

ath0 (for atheros, his wireless chipset manufacterer) for his WLAN adapter
and
eth0 (for ethernet) for his wired network device.

Normally Ubuntu calls the wired ethernet device "eth0" and the WLAN one "eth1". That is the difference that confused us all.

---

### Post by wieman01 on 2008-04-08
> **equity said:**
> ^^ this is exactly the point that confused me once.

ath0 (for atheros, his wireless chipset manufacterer) for his WLAN adapter
and
eth0 (for ethernet) for his wired network device.

Normally Ubuntu calls the wired ethernet device "eth0" and the WLAN one "eth1". That is the difference that confused us all.
Interface names mean nothing, they change at random, really.

---

### Post by Funk Phenomena on 2008-05-29
> **equity said:**
> ...

sudo ifconfig <interface> down
sudo ifconfig <interface> up
sudo iwconfig <interface> mode monitor
sudo airodump-ng <interface>


^^ write these commands in a shell and post the output. Then we will see where is the problem.
I have an Inspiron 2650 with Hardy and a Buffalo WLI-CB-G54HP pcmcia wireless card.

I was using the default b43 driver which allowed swscanner to successfully work.  But then this thread had me all messed up at the third and fourth lines above, and the other "Is your driver patched for monitoring, etc" post had me land on this thread: [http://ubuntuforums.org/showthread.php?t=766560]("http://ubuntuforums.org/showthread.php?t=766560")
Now the card seems to work more properly, it is recognized and I went through that lengthy process with no errors.  But now I get a third of the connections I originally got in swscanner.  Provided it's almost 2am local time...

*sudo iwconfig wlan0 mode monitor*
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Invalid argument
*sudo airodump-ng wlan0*
Ndiswrapper doesn't support monitor mode

Here's a description of the innards, I xx'd out the serial number.

       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 02
       serial: xxxxx  <-edited by me
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,10/12/2006, 4.100. ip=192.168.0.4 latency=64 module=ndiswrapper multicast=yes wireless=IEEE 802.11g

So I guess my question would be, how do I patch ndiswrapper to support monitor mode?  My brain is mush from browsing and trying tutorials.  I don't feel as hopelessly lost as earlier today, but just wanted to get a post in before I zonked out.  In that regard, this may not be the right thread to ask that question...  but any help is appreciated :)

---

### Post by Funk Phenomena on 2008-05-29
Solved... and now I really am going to sleep.  Will post links when I rise from the dead... on the eee, while the other beast listens quietly.

---

