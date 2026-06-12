---
title: "How do you put IP addresses on Multiple NICs."
date: 2007-03-18
forum: Networking &amp; Wireless
---

### Post by swainstm on 2007-03-18
I am using Feisty Desktop 64bit with Multiple NICs, however Feisty only seems to allow 1 NIC to have an active IP address. All the interfaces seem to be in ifconfig and I can configured IP addresses on the the interfaces in :-

System\Administration\Network Settings

tool, and activated with a tick next to each interface, however ifconfig shows all the interfaces, but an IP address on only 1 of the interfaces as follows :-

swainstm@perc-syd-fw1:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:19:B9:26:7E:5E  
          inet addr:192.168.10.8  Bcast:192.168.10.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:943 errors:0 dropped:0 overruns:0 frame:0
          TX packets:820 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:79229 (77.3 KiB)  TX bytes:69269 (67.6 KiB)
          Interrupt:16 

eth1      Link encap:Ethernet  HWaddr 00:50:8B:6F:B8:FC  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

eth2      Link encap:Ethernet  HWaddr 00:50:8B:6F:B8:FD  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:200 (200.0 b)  TX bytes:200 (200.0 b)

I can change the interface that has the IP address, by selecting a different interface in the "Wired Network Connection" icon in the top right hand end of the taskbar. However, while this puts the configured IP address on the interface, it takes the IP address of the other interface.

Does anyone have any ideas on how to fix this? Thanks in advance.

---

### Post by lloyd_b on 2007-03-18
Just for clarification:  Are all three NIC attached to the same network?   If so, then you're not actually going to be able to use more than one at a time (although I do recall something called "bonding" that I believe will allow multiple NIC's to act as a single interface).

Could you post the contents of the file "/etc/networking/interfaces"?  This is the file that actually controls most of your network configuration (the GUI tools are just front-ends that modify it and run the necessary commands to activate the changes).

Lloyd B.

---

### Post by swainstm on 2007-03-18
Yes, all NICs are on a different physical layer 2 network, with each interface with different network address, from different networks.

See bellow for the file created automatically with the "Network" config tool.

Finally, is this something I should raise somehow in "Launchpad" or keep working on here. I have no idea how to raise in Launchpad, but if it is the most appropriate option, let me know.

Thanks heaps.

root@perc-syd-fw1:~# cat /etc/network/interfaces 
auto lo
iface lo inet loopback


iface eth0 inet static
address 192.168.10.8
netmask 255.255.255.0
gateway 192.168.10.1


iface eth1 inet static
address 192.168.107.2
netmask 255.255.255.252


iface eth2 inet static
address 192.168.107.5
netmask 255.255.255.252

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

auto eth0

auto eth2

auto eth1

---

### Post by Mr. C. on 2007-03-18
Try adding the **auto** *interface* keyword before each interface in /etc/network/interfaces file, as in :

auto eth0
iface eth0 inet static
...

or

auto eth0 eth2 eth1
iface eth0 inet static
...

No data on this one - just playing a weak hunch.

I wonder if the configuration script is having trouble with your subnetted 92.168.107.x/30 space.

MrC

---

### Post by swainstm on 2007-03-19
I tried moving the "auto eth?" but this made no different. I also tried using using completely different class C networks, but this also made no difference.

I built a brand new box on VMWare and confirmed exactly the same problem. It was interesting to note, when I first installed from CD (Feisty Herd5 64 bit Desktop) with no updates installed, initially it was looking like showing the same problem. However, when I configured the 3rd interface, the Network icon in the task bar showed disabled, but ifconfig showed all interfaces configured and indead they appeared to be working. I rebooted and confirm the same result. I then installed all the waiting updates, after which the Networking Icon in the taskbar once again enabled itself, and coupled with this, only 1 interface in ifconfig had an IP address.

It even looks like it might be meant to work like this as the "Network" icon in the task bar appears to have a radio type button which suggest you can only select 1 interface. I can also use this to select the interface that is to have the IP address. The question comes as to how I disable this as in my case I need multiple interfaces?????

Do you think this Is this something I need to log as a bug?

Thanks once again.

---

### Post by netztier on 2007-03-19
> **swainstm said:**
> 
```
root@perc-syd-fw1:~# cat /etc/network/interfaces 
auto lo
iface lo inet loopback


iface eth0 inet static
address 192.168.10.8
netmask 255.255.255.0
gateway 192.168.10.1


iface eth1 inet static
address 192.168.107.2
netmask 255.255.255.252


iface eth2 inet static
address 192.168.107.5
netmask 255.255.255.252


```

This is looking good & reasonable.

What does the routing table on your system look like (**netstat -rn** or **route**)? Is there some instance of iptables and/or firestarter active on the box? If yes, deactivate them (temporarily) to see if it makes any difference.

best regards

Marc

---

### Post by swainstm on 2007-03-19
With the exemption of the 169.254.0.0 (which I have no idea who that is there, but assume it is not much to worry about as it is a local, zero config address), netstat -nr looks pretty normal as if I only have 1 interface and IP address configured :-

swainstm@perc-syd-fw1:~$ netstat -nr
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.10.0    0.0.0.0         255.255.255.0   U         0 0          0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0
0.0.0.0         192.168.10.1    0.0.0.0         UG        0 0          0 eth0
swainstm@perc-syd-fw1:~$ 

However, I have 3 configured interfaces and there is no sign of there.

No I don't have any iptables configured beyond the default allow everything. I have also build a box from scratch, with just the default Feisty Desktop build, and nothing else configured besides the 3 interfaces and I have the same problem.

It is probably worth asking, if there is anyone out there who is running a Feisty build with more than 1 interface active and with an IP address at 1 time??

Thanks heaps.

---

### Post by netztier on 2007-03-19
> **swainstm said:**
> With the exemption of the 169.254.0.0 (which I have no idea who that is there, but assume it is not much to worry about as it is a local, zero config address), netstat -nr looks pretty normal as if I only have 1 interface and IP address configured :-


You should be able to get rid of it by disabling or uninstalling zeroconf. Not sure what other implications this might have on your system.

> **swainstm said:**
> 
```
swainstm@perc-syd-fw1:~$ netstat -nr
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.10.0    0.0.0.0         255.255.255.0   U         0 0          0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0
0.0.0.0         192.168.10.1    0.0.0.0         UG        0 0          0 eth0
swainstm@perc-syd-fw1:~$ 

```

Hm. This looks "normal" as one could expect with a single interface. :confused: 

> **swainstm said:**
> 
However, I have 3 configured interfaces and there is no sign of there.


You're right. Is there any news about eth1 and eth2 in **dmesg** or **/var/log/syslog**, after a (re)boot or after a manual **sudo ifup eth1** or **sudo ifdown eth1**?

Best regards

Marc

---

### Post by Mr. C. on 2007-03-19
I didn't think my weak hunch would pay off.

But something you said now intrigues me.  I know that others with multiple NICs were getting into situations where they enabled both NICs, and this screwed up their default route.

Was there an update that corrected this problem, by simply changing Network to use Radio buttons?

In my opinion, the Network applet is too simplistic as it is today to handle multiple NIC situations correctly.

But still, your manual configuration should be ok.  Try also the --force option to ifup to ensure the state file is updated to match your configuration.

MrC

---

### Post by swainstm on 2007-03-19
Thanks for the suggestions. I did some of this and a bit more and connected the following information that might give some more clues :-

* Nothing particularly unusual in dmesg file.
* I did not think of ifdown/ifup because if config suggested it was up, but when I tried this, ifdown was as expected, but ifup gave the error bellow :-

swainstm@perc-syd-fw1:~$ sudo ifup eth1
RTNETLINK answers: File exists
run-parts: /etc/network/if-up.d/avahi-autoipd exited with return code 2
swainstm@perc-syd-fw1:~$ 

After this the interface was up, and there was an ip address on the interface. But after a reboot, the IP addresses are lost and we are back to square 1. I can't seem to see any difference to the above when I run with a --force. I am wondering if the error above is something to do with my problem.??

It was interesting to not that if I config the IP address manually with ifconfig, it all seems to be good and working ok, but I assume I really need /etc/networks/interface to do its thing in terms of handling linkup/linkdown etc.

Does this give any more clues.

---

### Post by Mr. C. on 2007-03-19
Avahi is the DNS/DNS-SD daemon - that's not a factor here.  The error indicates the daemon was already running.

Try bringing down all the interfaces
```

sudo ifdown -a
sudo rm -f /etc/iftab
sudo reboot
```

See what your network looks like after the system comes up again.

Worst case and as a last resort, you can ignore the issue, and bring up all the interfaces in /etc/init.d/rc.local.

---

### Post by swainstm on 2007-03-19
Deleting the iftab and rebooted, but did not fix anything, so I recreated it.

As a side note, doing the "ifdown -a" seemed to cause the taskbar etc to hang up for some time.  This does not seem to happen if I do 1 interface at a time. I would assume this is a side issue, but thought I would mention just in case.

Seems putting into ifdown and up for all interfaces in /etc/rc.local will do the trick, but did not know whether this might have some unintended side effects with thing like iptables scripts etc etc.

---

### Post by Mr. C. on 2007-03-20
Sorry things didn't work out. I don't know what the cause of your issue is.   The iftab gets recreated - it associates a MAC address with an interface.

You can bring up the interfaces earlier if you are concerned about conflicts.  The network is brought up in /etc/rcS/S40networking.  You can place your script in /etc/network/if-up.d.  I don't really like this workaround, as its ignoring the problem, but I suppose it will have to do until the cause is identified.

With two interfaces, I haven't experienced the same trouble that you have.

MrC

---

### Post by swainstm on 2007-03-20
MrC,

Just to clarify, are you using Feist? And are you saying you don't have this issue with 2 interfaces and IP address configured and active on both interface?

Thanks heaps.

---

### Post by Mr. C. on 2007-03-20
Prior to last night, I was on Edgy.  Last night I updated to Feisty, to see how things behaved.

I also looked through thousands of bug comment entries, and this morning I spent some time tracing what is happening.  This is what I discovered.

1: Network Manager is broken - plain and simple.  It correctly handles only 1 interface at a time.  The bug reports on this piece of the software are unbelievable, and there are too few developers to resolve the problem.

2: I have verified that the system does correctly bring up all specified interfaces.  However, the broken Network Manager brings the all down again (which is entirely improper), and then only brings up one.

You can verify this by running the following command in a terminal window:

```
watch -n 1 'ifconfig eth0; ifconfig eth1; ifconfig eth2; route -n'
```

and this on a second terminal window:

```
ifdown -a
ifup -a
```

Watch how all the interfaces come up, and then they are torn down, and only one brought back up again.

3: Upon removing Network Manager, all interfaces are brought up correctly each reboot.

To remove network manager, run:

```
sudo apt-get remove network-manager network-manager-gnome
```

You can ignore the scary message about removing the Ubuntu desktop.

The only downside is not having the ability to configure the network via the GUI.  I'd rather have text-only correct behavior than eye-candied incorrect behavior.  

MrC

---

### Post by netztier on 2007-03-21
> **Mr. C. said:**
> I also looked through thousands of bug comment entries, and this morning I spent some time tracing what is happening.  This is what I discovered.
[horrible atrocities snipped]


EEEEW! Now that **is** bad news! And I had hoped they'd started to fix the thing at last. I'll be needing it for the half dozen of WPA-Enabled networks I want to be able to connect to with some comfort.

Let's hope that they get it right in time. I'm also thinking of proper static IP addressing support etc...

best regards

Marc

---

### Post by Mr. C. on 2007-03-21
There is a Roaming Profile mode (in Feisy).  I did not try it though.

MrC

---

### Post by swainstm on 2007-03-21
Thanks MrC. for your great assistance. It is greatly appreciated.

I tried your watch, and the behavior you are see, seems to be a little different to mine. ifdown/up on my PC seems to work ok, and is in fact a sort of fix to the problem. I am running all the latest upgrades, but what you where seeing sounds like it might be similar to what I saw before the updates.

For what it is worth I have logged a bug id 94068 in launchpad, so lets hope that helps people fix it.

---

### Post by Mr. C. on 2007-03-21
Thanks Swainstm.

To clarify, ifup/ifdown works fine.  It was network manager that was incorrectly calling ifup/ifdown  when a) its settings were changed, and b) during system boot.

The Network Manager applet is a bit too simplistic to handle the multitudes of configurations desired by its users.  It works for a single NIC fine.

MrC

---

