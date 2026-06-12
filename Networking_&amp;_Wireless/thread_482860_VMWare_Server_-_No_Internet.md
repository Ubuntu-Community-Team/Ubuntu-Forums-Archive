---
title: "VMWare Server - No Internet"
date: 2007-06-24
forum: Networking &amp; Wireless
---

### Post by Simple Man on 2007-06-24
Hello!
I have a litte problem with VMWare Server 1.0.2 build-39867.

I have running a Windows XP Pro in VMWare Server under Ubuntu Feisty. It works great, but I cannot get the internet running!
The virtual ethernet device is "bridged" to wlan0 on my ubuntu. If I type "ipconfig" in WinXP i have an IP-Address from my router but I can't ping it. I also cannot ping my ubuntu-pc.
The strange thing is, that I can connect to my VMWare XP from ubuntu. I can access the files via Samba.
But the worst thing for me is:** I cannot connect to the internet.**

I hope someone can help me.

Greeting from Switzerland
*Excause my bad english... ;)*

Simple Man

> **vmware-config.pl:**
(...)
The following bridged networks have been defined:
. vmnet0 is bridged to wlan0

(...)
Starting VMware services:
Virtual machine monitor --> done
Virtual ethernet --> done
Bridged networking on /dev/vmnet0 --> done
Host-only networking on /dev/vmnet8 (background) --> done
NAT service on /dev/vmnet8 --> done
Starting VMware virtual machines... --> done 

---

### Post by mungojerrie2 on 2007-06-24
have the same problem, so I am just listening in ;)

---

### Post by sheepfunk on 2007-06-29
Me too... I'm having the same problem, I've run the vmware-config.pl script 3 times and tried all the different networking options (bridged, NAT, etc.). My main machine is connecting just fine grabing a dhcp ip from my router, but my virtual windows machine doesn't want to connect, and I've tried a bunch of different configurations of my local area connection on it. When I try to ping my router, all my requests time out, but oddly enough my local area connection on the virtual says it's sending and receiving packets, so long story short, I dunno what's happening, and am jumping on this thready bandwagon.

---

### Post by wreichard on 2007-06-29
Me too. Incidentally, I switched over to VMWware when VirtualBox seemed to have the same problem. Virtual XP can't seem to find anything to bridge.

---

### Post by Elche on 2007-06-29
I have a similar problem on my Debian Etch 4.0
I have installed VMWare Server 1.03 and then onto it a Virtual Machine with WindowsXP inside. I have a router. The network work if i use samba and windows resource sharing. I can exchange files between the VM and the Host system, but if I open the web browser i cannot navigate. The DNS translation seems working but there is no response. The request remains hanged.
I am using the bridged network virtual machine. Someone have any idea ??
I am working on this problem from two days without any results :(

Thanks
Bye

P.S: Forgot to says that internet on the Debian host system work regularly, only in the Windows VM do not work (i disabled the windows firewall too)

---

### Post by Gallows on 2007-06-30
Have you tried installing firestarter and enabling "Internet Connection Sharing" - aka. port forwarding?  If you have you may want to check your firestarter preferences and see what is the identified local network device.  If it reads eth0 it may be worth changing it to the vmnet device your VM's are using.

I'm running VMWare Server with XP VM's and they connect to the internet via firestarter over my vmnet8 virtual NIC.

---

### Post by Elche on 2007-06-30
I tried to install firestarter but vmnet0 it is not in the list of connection sharing.
vmnet0 it is a bridging device. I cannot figure out what is the problem :(

---

### Post by Gallows on 2007-07-01
Try configuring your VM to use the NAT device - vmnet8 perhaps.  If you *really* need your VM's on a bridged network you could  try setting up a web proxy service.  Check out [this]("http://ubuntuforums.org/showthread.php?t=320733&highlight=squid+howto") Squid howto for more details

---

### Post by Elche on 2007-07-02
Ok, I tried to use firestarter in NAT mode on vmnet8 and internet works. You're right.
Tonight I do not have much time, tomorrow I will try to set up a proxy on vmnet0 bridged.

But I do not understad why. is this a bug of bridged device of vmware on linux? I do not think that this is the correct mode for vmnet0 to works. In WindowsXP (native) if I install VMWARE I do not need to install a proxy too. Although in WindowsXP i tried VMWARE Workstation trial and not the Server.

Thanks,
Bye.

---

### Post by tom17 on 2007-07-03
I too am having a similar problem.

Machine A - Host machine running Ubuntu feisty with VMWare server 1.0.3 (using eth1 as onboard eth0 is unused)
Machine B - Laptop with Ubuntu feisty & VMWare (using wlan)

VM 1 - XP Pro using vmnet0 and running on Machine A
VM 2 - XP Pro using vmnet0 and running on Machine B

vmnet0 on Machine A - bridged network using eth1

Both VMs can ping Machine A using ip address fine
Both VMs can reach the internet fine
VM 2 is able to make successful TCP connections to services running on Machine A(samba, http)
VM 1 is NOT able to make any tcp connections to Machine A even with using its ip address(even though it can ping it)

tcpdump on Machine A shows very slow/occasional traffic coming from VM 1 when I try to connect to something, but shows plenty of normal traffic from VM 1 when it is accessing the net.

I have been re-installing vmware, reconfiguring the networking, all to no avail. There is something screwy with the vmnet0 bridged network and its communication with the host's ethernet connection using tcp, but not a problem with going through the same host connection to the rest of the network.

I'm out of ideas. Do any of you have ideas on what I should look at? :)

Thanks,

Tom...

---

### Post by tom17 on 2007-07-03
I forgot to add, 

I was wondering if the bridged networking in vmware has any strange routing that I could look at to fix this problem. The behaviour is almost as if its a switch dropping packets, but of course there is no real switch, just the virtual one which is vmnet0. Is there a right & wrong way of installing vmware on edgy? From what I remember I just did it using add/remove programs...

Cheers

Tom...

---

### Post by Kaso_Da_Zmok on 2007-07-03
Hello guys, i have the same problem and is generally a problem with the Wireless Driver being not able to be bridge-t, i have tried with ralink and broadcom (broadcom saks in my opinion)

And the only workaround here is to use NAT, so you do not use bridge, but NAT instead. That works w/o problem.

:popcorn:

---

### Post by tom17 on 2007-07-03
But I am not using a wireless network.

The guest os' networking DOES work, but just not tcp to the host computer.

I'll give NAT a go tonight but this is very odd behaviour. Is this a bug in VMWare?

---

### Post by Kaso_Da_Zmok on 2007-07-03
You mean the VM can ping anything after the bridge ? like your router but cannot ping the host ip of your ubuntu ?    I am using vmware server on Ubuntu , Gentoo, CentOs and never had something like that....

Does not seem to be a bug as i work in Vmware tech support. :-):popcorn:

---

### Post by tom17 on 2007-07-03
The guest OS can ping the host OS, but it cannot establish any tcp connections to the host OS. It CAn establish tcp connections to other machines or out onto the web, so tcp is working.

Just not between the host & guest :-(

---

### Post by tom17 on 2007-07-03
So I just tried using NAT and it works.

But its annoying me that the bridged networking will not work properly. I don't see why it should not. This must be some misconfiguration or bug in my setup. A shame :-(

Cheers for the help though :)

Tom...

---

### Post by Gallows on 2007-07-03
OK as Kaso_Da_Zmok says bridged networking *should* work

What IP gateway does the VM have set and is Packet Forwarding turned on?

On the XP machine run the following to get your gateway: 

```
cmd /k "ipconfig /all"
```

On the Ubuntu / VMServer box run the follwing to determine if packet forwarding is turned on

```
cat /proc/sys/net/ipv4/ip_forward
```

To HowTo's from the forums one [here]("http://ubuntuforums.org/showthread.php?t=376283&highlight=packet+forwarding+howto") and one [here]("http://ubuntuforums.org/showthread.php?t=159661&highlight=packet+forwarding+howto")

Both look like a fairly comprehensive set of instructions to setup packet forwarding on an internal LAN, as vmnet0 is just another machine (even if is is virtual) on your LAN

---

### Post by tom17 on 2007-07-04
The VM had my router set as its gateway and it could ping it and get out to the internet just fine. It can ping the host OS also, but cannot make a tcp connection to the host OS.

IP forwarding was disabled, enabling it made no difference.

Are you saying that to get VMWare to work so that the guest can talk to the host over vmnet0, I have to set up iptables and configure the bridge manually? I was under the impression that vmnet0 had all this functionality built in.

ps. I don't really see the relevance of the first link you gave as it is talking about configuring a wireless bridge - something I am not trying to do. The second link also unless I am meant to configure iptables just to get vmware working properly - a requirement I have not seen any reference to before now. Am I missing something here? :)

pps. Is there anything to do with the 'promiscuity' of the eth1 that I can look into? I have tried setting and un-setting it but that made no difference.

Thanks,

Tom...

---

### Post by tom17 on 2007-07-04
OK, so I found that this problem is a kinda hot topic on the vmware discussion forum.

[http://www.vmware.com/community/thread.jspa?threadID=78606&tstart=0]("http://www.vmware.com/community/thread.jspa?threadID=78606&tstart=0")

It appears to be a problem that others are having too, not just me, and not related to the host OS being Ubuntu, so I will take it over there :)

Thanks for your help

Tom...

---

### Post by Gallows on 2007-07-04
The VM Forum looks like the best place for this then the links were ubuntu howto's on how to setup "Internet Connection Sharing" from the Ubuntu box, however if you have your own separate router then they probably won't be much help.

Good Luck
-Gallows

---

### Post by daki on 2007-07-05
This fixed it for me.
[https://bugs.launchpad.net/ubuntu/+source/vmware-player/+bug/105697]("https://bugs.launchpad.net/ubuntu/+source/vmware-player/+bug/105697")

---

### Post by tom17 on 2007-07-06
Unfortunately this does not work for users with the Realtek card myself and some others are using.

05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10) 

Someone in the thread you linked to had the same problem, as does someone else in the thread on the VMWare forums...

[http://www.vmware.com/community/thread.jspa?threadID=78606&start=30&tstart=0](http://www.vmware.com/community/thread.jspa?threadID=78606&start=30&tstart=0)

Some of us are shitouttaluck on this one :-(

Tom...

---

