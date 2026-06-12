---
title: "No Connection, No Buttons"
date: 2005-07-03
forum: Networking &amp; Wireless
---

### Post by revolutio on 2005-07-03
Alright, I built a computer out of spare parts while I was at college and bored.  I decided to use Ubuntu because I had heard good things and was rather tired of Windows.  I had no prior experience with Linux.  I installed the old Warty and bing-bang-boom everything goes great.  No problems that I could see.  Then I get back home form college...

When I tried to set it up again for my folks the internet just doesn't work.  The ethernet card won't stay active.  I can't ping anything.  I decide that while I am working on it I might as well reformat and install Hoary since I wanted to start fresh.  It gets worse.  I still can't get on to the internet and now the Network Connections menu lacks buttons to even add an internet connection.  ](*,) 

Alright, the info:
I connect to the internet through a router (Netgear RP614v2, with the latest Firmware).  The three other windows machines that connect to the router all run fine and have dynamic IPs.  The CAT5 cable that plugs into my Ubuntu machine works because I tested one of the other machines on it.

The NIC card is a Realtek RTL8139.  The lights come on and it was working when I removed it from the last computer.  Also while browsing the forums I saw that some other Ubuntu users had this card and it worked fine with no tweaking they said.  It does show up in device manager.

Alrighty, when I installed Hoary and went to work on the problem again I found the Network Connections menu **completely lacking a button to add an ethernet connection**.  All the tutorials I checked sounded like it should be there and it was there in Warty.  I don't know where to even begin on this problem, hence I resort to the forums.

Please help me.  Let me know what other information you need.  And sorry if this isn't the correct forum.   :-? 

I would really love to use Ubuntu, but without net access it isn't worth it.  Thanks for your time.

---

### Post by revolutio on 2005-07-15
Any ideas?  last call  :-(

---

### Post by gruepig on 2005-07-15
Open up a terminal window, run the following commands at the command line and post the results:

/sbin/ifconfig -a
/sbin/route -n

---

### Post by revolutio on 2005-07-17
/sbin/ifconfig -a output:
lo    Link encap: Local Loopback
       inet addr: 127.0.0.1     Mask: 255.0.0.0
       UP LOOPBACK RUNNING  MTU:16436   Metric: 1
       RX packets: 600   errors:0   dropped:0   overruns:0   frame:0
       TX packets: 600   errors:0   dropped:0   overruns:0   carrier:0
       collisions: 0   txqueuelen: 0
       RX bytes: 53396  (52.1 Kib)   TX bytes: 53396  (52.1 Kib)

/sbin/route -n output:
Kernel IP routing table
Destination      Gateway     Genmask     Flags Metric Ref     Use Iface

---

### Post by gruepig on 2005-07-21
Odd that your ethernet card shows up in the device manager, but then isn't showing up in the output of ifconfig at all.  Are there any errors listed for it in the device manager?  Another way to check that it was detected is to run 'dmesg | less'. This will show you a bunch of hardware detection and boot messages.  It's moderately interesting to read if you understand it, but otherwise overwhelming; I recommend just browsing it looking for word like ethernet, eth0, realtek, etc.  An easier thing to do if your ethernet card is a PCI card is to run lspci. This gives you information about all of your PCI devices, so you can use this to verify that your ethernet card is there (should say something like 'Ethernet controller: Realtek').

(By the way, I'm assuming the interface name of your first ethernet card would be eth0.  The only thing showing up in ifconfig is lo, which is the loopback interface, or roughly speaking, the interface the computer uses to talk to itself.) 

Have you configured the ethernet card to use DHCP or specified a manual IP address?  You can do this through the Network settings program. If DHCP is available, use that.

While graphical programs are sometimes easier to use and understand than editing config files directly, text files really are the heart of Linux/Unix systems.  Your network settings are in /etc/network/interfaces.  Take a look at this file (using gedit or the command-line viewer less).  You should have a stanza which read something like:

auto eth0
iface eth0 inet dhcp

(Pretty self-explanatory: the first line means to bring up the interface automatically on boot; the second line means use DHCP.  If you aren't using DHCP, the second line will be 'iface eth0 inet static' and will be followed by lines which specify IP address, netmask, gateway, etc.)

To bring your ethernet interface up without rebooting, run 'ifdown eth0' from the command line to make sure it's down and then 'ifup eth0' to bring it up.  Note errors, if there are any.  Run '/sbin/ifconfig -a' again; hopefully you have eth0 now.  You should also see your route table when you run '/sbin/route -n'.  (Post the output of both again if it has changed, but you are still having problems.)

For the sake of being thorough, the other file to check is /etc/resolv.conf.  This file contains your name servers, one line at a time.  These will almost certainly be set by DHCP (but if they aren't, you need to add them here either directly or through the network settings program).  Check this after (and only after) ifconfig and route are giving you reasonable output and you can ping machines by IP address.

---

### Post by revolutio on 2005-07-21
Okay the NIC card is a pci device and showed up when I ran lspci.  For what its worth the entry was this:
Ethernet controller:  Realtek Semiconductor Co., Ltd.   RTL-8139/8139C/8139C+   (rev 10)

Device manager told me it didn't recognize the device type (but the same goes for my CPU and RAM so this doesn't concern me).  There were no errors listed that I could tell.

Alrighty, I cannot configure the card to DHCP since the graphical interface is apparently defunct.  When I go to System > Administration > Networking Connections the field has just the greyed out box for a Modem (something I don't have).  Everything else seems to be greyed out as well.  :/  (I tried running the Network program from the command line once and was able to get a long error message which I am guessing is a result of the GUI problem, let me know if you want to see it)

Is there a way to add and configure my ethernet card from the terminal? 

Anyway so I looked up the /etc/network/interfaces file.  I had checked this out several times before when I was browsing for solutions on my own.
It's contents are:
auto lo eth0 eth1 eth 2
iface lo inet loopback
Now, correct me if I am wrong, but doesn't that mean the computer is trying to talk with itself when it should be talking with the internet?  How can I edit this file?  gedit was being a punk and complaining about it being read only.

I tried the 'ifdown eth0' command and the response was "interface eth0 not configured"   :???: 

Grrr... thank you for lending me your brains on this gruepig.

---

### Post by gruepig on 2005-07-22
You need root privileges to edit the file.  Try 'sudo gedit /etc/network/interfaces'.  Leave all the lines that are there, but add the following:

auto eth0
iface eth0 inet dhcp

Save the file and then run 'ifup eth0'.

---

### Post by revolutio on 2005-07-22
[QUOTE=gruepig]You need root privileges to edit the file.  Try 'sudo gedit /etc/network/interfaces'.  Leave all the lines that are there, but add the following:

auto eth0
iface eth0 inet dhcp

Save the file and then run 'ifup eth0'.[/QUOTE]
 Okay I edited the file with gedit.  ( had to just use the first line since it wouldn't let me have two 'auto' lines)

The autput to ifup eth0 was:
Internet Systems Consortium DHCP client V3.0.1
blah blah legal stuff blah blah

SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: no such device
eth0: ERROR while getting interface flags: no such device
bind socket to interface: no such device
failed to bring up eth0

>_<  I am thinking this means that my NIC isn't eth0 since 'ifdown eth0' says that eth0 isn't configured yet.

---

### Post by gruepig on 2005-07-22
Alright, let's try to figure out what the name of your ethernet device is.  dmesg should tell you.  Skim through the output of dmesg and/or try 'dmesg | grep eth'.

---

### Post by revolutio on 2005-07-23
Okay I browsed through dmesg and found this:

8139too   Fast Ethernet driver 0.9.27
ACPI:  PCI Interrupt Link [LNKB] enabled at IRQ 11
PCI:  Setting IRQ 11 as level-triggered
ACPI:  PCI interrupt 0000:00:09:0 [A]  ->  GSI 11 (level, low)  ->  IRQ 11
8139too:  0000:00:09.0:  Chip not responding,  ignoring board
8139too:  Probe of 0000:00:09.0 failed with error -5
8139cp:  10/100 PCI Ethernet driver v1.2
8139cp:  pci dev 0000:00:09.0 (id 10ec:8139  rev 10) is not 8139C+ compatible chip
8139cp:  try the "8139too" driver instead

Methinks the ethernet card is dead.

---

### Post by revolutio on 2005-07-23
Yatta!  I dug through my computer graveyard and found a computer with a NIC card (they all had these weird devices labeled "mo-dems").  I swapped that out with the one that was in my PC and viola it has internet connectivity.  I haven't tried out that old NIC card on another computer yet so I don't know if it is faulty or just grumpy when paired with my router.

Regardless, thank you very much for your assistance gruepig, I learned quite a bit from my frustrations.

---

### Post by bmargulies on 2005-07-24
The installation process left me with this. It does not handle eth1, my wireless.
How should I modify it? Should I add a map eth1 to the hotplug list?



auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface
iface eth0 inet dhcp

---

### Post by gruepig on 2005-07-24
No problem.  Glad you've found a way to have a working network.

[QUOTE=revolutio]
8139cp: try the "8139too" driver instead
Methinks the ethernet card is dead.
[/QUOTE]

It's possible the card is bad.  It's also possible that using a different module (83139too) with the old card would work.  Loading kernel modules can be done by running 'modconf' and selecting the appropriate module.  Or with 'modprobe 83138too' or 'insmod 8138too' (if you don't want the module to be loaded automatically on boot).

---

