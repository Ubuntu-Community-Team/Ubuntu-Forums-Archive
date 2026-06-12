---
title: "wireless problems"
date: 2008-07-02
forum: Networking &amp; Wireless
---

### Post by nobbydog on 2008-07-02
hi all
i have ubuntu installed in windows and when i plug it in to my wired network ,it shows as connected but firefox  will not launch , keeps saying website not avaible.Could firefox be turned off.
also i cannot pick up my wireless connection.
i am a newbie and do not understand the command line yet.
can anyone help.
nobbydog

---

### Post by kdcoetzee on 2008-07-02
Firefox can be turned off, but then the page would say something like "offline", go check under "File" for "Work Offline"

if you open up the terminal and type : 

```
ping www.google.com 
```

do you get a reply . it should look something like this :

```
:~$ ping www.google.com
PING www.l.google.com (72.14.205.103) 56(84) bytes of data.
64 bytes from qb-in-f103.google.com (72.14.205.103): icmp_seq=1 ttl=238 time=336 ms
64 bytes from qb-in-f103.google.com (72.14.205.103): icmp_seq=2 ttl=238 time=337 ms
64 bytes from qb-in-f103.google.com (72.14.205.103): icmp_seq=3 ttl=238 time=333 ms
64 bytes from qb-in-f103.google.com (72.14.205.103): icmp_seq=4 ttl=238 time=347 ms
```

when you are connected to wired network.
If the result looks the same check Firefox' network settings. does your network go thru a proxy ?


what do you mean by "installed in windows" did you install it on a Virtual Machine , like virtualbox or Vmware. Or did you install Ubuntu with wubi.

I am not that good with wireless troubleshooting. But I will give it a shot if I get more info.

---

### Post by superprash2003 on 2008-07-02
go to the terminal and type ifconfig and post output here.. before doing that go to system->admin->network and set your ethernet card to DHCP

---

### Post by nobbydog on 2008-07-02
hi juggernaut
installed with wubi.
if i click on the network manager it says wired on line ,but still cannot get on internet and its not picking up wireless at all.
regards nobbydog

---

### Post by nobbydog on 2008-07-02
hi superprash
i am trying to get the wireless connection to work do youstill want me to type ifconfig in the terminal
nobby

---

### Post by superprash2003 on 2008-07-02
the reason im asking for an ifconfig output is to see if you are getting an ip address or not

---

### Post by nobbydog on 2008-07-04
superprash
sorry about delay in answering away for a wedding will reply sunday'
nobby

---

### Post by nobbydog on 2008-07-07
hi superprash
I will be back on line monday nite, but i noticed that my roaming button in network manager is not active how can this be turned on
nobby

---

### Post by nobbydog on 2008-07-07
hi superprash or anyone that can help!!!!!!!!!!
typed in ifconfig and got the folowing
eth0 LINK ENCAP :ETHERNET HWADDER 00: LE 68 :61:43:13
     UP BROADCAST MULTICAST  MTU:1500 Metric1
     RX packets:0 errors:0 dropped:0 overuns:0 frame:0
     TX packets) errors:0 dropped :0 overuns:0 carrier:0
     collissions:0 txqueueen:1000
     rx bytes:0 (0.0 b)tx bytes:0 (o.o.b)
     interupt: 16 base address:0x2000

lo   link encap: local loopback
     inet addr:127.o.o.1 mask:225.0.0.0
     inet6 addr: ::1/128 scope: host
     UP LOOPBACK RUNNING  MTU:16436 Metric:1
     RX packets : 156 errors:0 dropprd:0 overuns:0 frame:0
     TX packets:156 errors:0 dropped:0 overuns:0 carriers:0
     collissions:0 txqueuelen:0
     RXbytes:7800(7.6kb)  TXbytes:7800(7.6kb)

also notice the roam button not working in network settings.
thanks nobbydog

---

### Post by superprash2003 on 2008-07-08
is eth0 your wifi device?? go to the terminal and type iwconfig and post output

---

### Post by nobbydog on 2008-07-08
hi superprash
typed iwconfig following output

lo no wireless extensions

etho no wireless extensions
nobby

---

### Post by superprash2003 on 2008-07-08
ok. go to the terminal and type lshw -class network and post output here

---

### Post by nobbydog on 2008-07-09
hi superprash
inputed lshw-class
Hradware lister (lshw) - B.02.12.01
USAGE: LSHW [-FORMAT] [-OPTIONS ...]
       lshw - version

       -version     print program version (B.02.12.01)
 format can be
         -html       output hardware tree as HTML
         -xml        output hardware tree as XML
         -short      output hardware paths
         -businfo    output bus information

options can be
         -class CLASS  only show certain class of hardware
         -C CLASS     same as '-class CLASS'
     -disable TEST  disable a test (like pci, isapnp,cpuid,etc.) 
     -enable  TEST  enable a test(like pci, isapnp, cpuid,etc)
     -quiet     don't display status
     -sanitize output(remove sensitive information like serial 
numbers etc)
regards nobby

---

### Post by superprash2003 on 2008-07-09
sorry for not being clear .. the command is **lshw -class network**

---

### Post by nobbydog on 2008-07-09
hi superprash
inputed lshw-class network came up

bash:lshw-class command not found

nobby

---

### Post by superprash2003 on 2008-07-09
its lshw -class network

 there is a space between lshw and -class

---

### Post by kdcoetzee on 2008-07-10
Just want to make shore.
can your wireless see other wireless network but not your own. or does it pick up nothing.

can you please post the results:

```
iwlist scan
```

and post the output of superprash2003 command.

---

### Post by nobbydog on 2008-07-10
to superprash/ juggernaut
ubuntu installed with wubi all works fine on win doze but can't see any networks on ubuntu.
output for lshw -class network

*-network
descriptionn ethernet interface
product:MCP65 Ethernet
vendor nvidia corporation
physical id:6
bus info:pc@0000:00:06.0
logical name etho
version a3
serial:00:le:68:61:43:13
width 32 bits
clock 66Hz
capabilities; bus master cap list ethernet physical
configuration:broadcast=yes driver=forcedeth driver version=0.61
latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast yes
*-network UNCLAIMED
DESCRIPTION:ETHERNET controller
product:AR242X 802.11abg wireless pci express adapter
vendor atheros communications inc.
physical id:0
bus info:pci@0000:03.00.0
version 01
width:64 bits
clock 33Mhz
capabilities: cap_list
configuration:latency=0

output for iwlist scan
lo    interface doesnot support scanning

eth0  interface does not support scanning
regards nobby

---

### Post by kdcoetzee on 2008-07-10
> **nobbydog said:**
> 
output for iwlist scan
lo    interface doesnot support scanning

eth0  interface does not support scanning
regards nobby

Sorry can you try 

```
sudo iwlist scan
```

---

### Post by nobbydog on 2008-07-10
juggernaut
same output as b4
nobby

---

### Post by kdcoetzee on 2008-07-10
Ok that is weird.

can you please post ```
lspci
``` output

---

### Post by superprash2003 on 2008-07-10
ok your output shows that you have atheros  AR242X  .. so you could try this link [http://ubuntuforums.org/showthread.php?t=766169](http://ubuntuforums.org/showthread.php?t=766169)

---

### Post by nobbydog on 2008-07-10
superprash
will this affect my win doze side of my laptop
aiso i cannot download on ubuntu no internet access
nobby

---

### Post by Berean on 2008-07-10
nobbydog,

I've been reading your thread as I'm having similar problems.  Might I answer your question?  No, it won't affect windows if you're doing this in Ubuntu.  You're effectively enabling two pieces of hardware to communicate in a different language (simplistically written) so what you do in Linux won't affect Windows.

---

### Post by nobbydog on 2008-07-10
hi berean
thanks
i installed ubuntu thru wubi.
will it still not effect my win doze
regards nobby

---

### Post by Berean on 2008-07-10
> **nobbydog said:**
> hi berean
thanks
i installed ubuntu thru wubi.
will it still not effect my win doze
regards nobby
Sorry mate, I don't have any experience of Wubi.  However, if it's a virtual machine it shouldn't have any bearing on the matter.  Windows enables your two pieces of hardware to communicate in one language, Ubuntu enables two pieces of hardware to communicate in another.  But please, check this with someone else to make sure.

---

### Post by superprash2003 on 2008-07-10
it wont affect your windows settings mate.. dont worry :D

---

### Post by nobbydog on 2008-07-10
hi superprash
is ndiswrapper already in ubuntu or do i have to downloadit.
how go i download and get.inf from the xp driver on to ubuntu with no internet connection.
nobby

---

### Post by superprash2003 on 2008-07-10
cant you connect through a wired connection? use internet like that.. if you have the xp driver with you ( in a cd or something) then the .inf file would be there itself..

---

### Post by nobbydog on 2008-07-11
hi superprash
i connected my laptop through awired connection its showing connected to wired network but firefox will not load comes up page load error any ideas.
nobby

---

### Post by kdcoetzee on 2008-07-11
> **nobbydog said:**
> firefox will not load comes up page load error any ideas.
nobby

What does the error say ?

---

### Post by kdcoetzee on 2008-07-11
> **Juggernaut_KDC said:**
> if you open up the terminal and type : 

```
ping www.google.com 
```

try to ping google tru your terminal.

---

### Post by superprash2003 on 2008-07-11
an ifconfig output would help :D to know whether you are getting an ip or not.. change your wired connection as DHCP under system->admin->network and then post ifconfig

---

### Post by nobbydog on 2008-07-12
hi juggernaut/superprash
plugged in wired lead internet now working wired! not wireless WHY!!!!!!!
nobby

---

### Post by nobbydog on 2008-07-12
also could you tell me how to down load compizconfigsettings manager
nobby

---

### Post by superprash2003 on 2008-07-12
compizfusion [http://ubuntuforums.org/showthread.php?p=2895086](http://ubuntuforums.org/showthread.php?p=2895086)
now try configuring your wifi with that link i gave you using ndiswrapper..since you have an internet connection via wired now

---

### Post by nobbydog on 2008-07-14
hi superprash/juggernaut
wired connection not working now.
going to download ndswrapper and  .inf from the XP driver on to a memory stick got the inf file where do i get ndswrapper from.
will ubuntu reconize my memory stick and can it be done this way.
nobby

---

### Post by kdcoetzee on 2008-07-14
[Ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper")
how to for ndiswrapper. the package that they list for hardy on the help.ubuntu you can download them.

and Ubuntu should recognize your memory stick.

I have never installed Ndiswrapper myself. I just googled Ubuntu help ndiswrapper.

And for why your wired connect suddenly stop working I do not now.

start the machine without the Ethernet cable 
open up a terminal and type 

```
tail -f /var/log/messages
```

then put in the Ethernet Cable and see what messages it gives you.

---

### Post by nobbydog on 2008-07-14
put in tail -f /var/log/messages
put in cable
says
johnkent laptop dhcdbd: dhco_input option: value -1 cannot be converted to type L
johnkent laptop dhcdbd: dhco_parse_option-settings: bad option setting:new-dhcp_lease time = -1
johnkent laptop dhcdbd: unreqested down ?:3
john kent laptop kernel: [186:327988} eth0 link down
regards nobby

---

### Post by superprash2003 on 2008-07-15
the driver your using is your own or from the link i gave you...(page2 or page3).. to install ndiswrapper etc.. go through this [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff) steps are similar not exact.. basically you gotta install and extract the drivers zip incase its in zip.. then cd to that directory and do this sudo ndiswrapper -i xxx.inf where xxx.inf is the name of inf file

---

### Post by theDaveTheRave on 2008-07-16
Hi Nobby and Co.

It seems that Nobby has a similar problem to mine.

A few days ago I had a "systems failure", where my laptop didn't shut down properly. In the end it turned itself off as the battery ran down.

Well the next day I rebooted my system and my wireless had failed!

here it the output of a few commads.

<quote>
davem@Dartagnon:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 88E8038 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       [COLOR="Red"]logical name: eth0[/COLOR]
       version: 14
       serial: 00:16:36:c8:51:d3
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.18 duplex=full firmware=N/A ip=192.168.2.4 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s
  [COLOR="Red"]*-network UNCLAIMED[/COLOR]
       description: Ethernet controller
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications, Inc.
       physical id: 3
       bus info: pci@0000:0a:03.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=168 maxlatency=28 mingnt=10
davem@Dartagnon:~$ 

</quote>

as you can see I have no logical names on my Atheros wifi card.

I have noticed that Nobby has a similar card and again also has no logical name for his card

<quote>
[COLOR="Red"]*-network UNCLAIMED[/COLOR]
DESCRIPTION:ETHERNET controller
product:AR242X 802.11abg wireless pci express adapter
vendor atheros communications inc.
physical id:0
bus infoci@0000:03.00.0
version 01
width:64 bits
clock 33Mhz
capabilities: cap_list
configuration:latency=0
</quote>

I don't know if this helps, but I am still searching for a solution to my problem also.

Here is the contents of my <etc/network/interfaces> file
<quote>

auto lo
iface lo inet loopback

auto eth0
#iface eth0 inet dhcp

auto eth1
#iface eth1 inet dhcp

auto eth2
#iface eth2 inet dhcp

auto wlan0
iface wlan0 inet dhcp


iface ath1 inet dhcp
wireless-essid ASHLANDS
wireless-essid Mousquetaires

auto ath1

</quote>

My feeling is that all I need is to do is get the card to have a logical name! Is this held in a file somewhere?

I have also tried removing the installed modules, reboot, reinstall modules, in the belief that this may help!

I can confirm that the restritcted drivers are enabled, but I'm still not getting the card to work.

Please help

Dave.

---

