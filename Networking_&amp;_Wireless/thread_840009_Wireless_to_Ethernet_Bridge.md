---
title: "Wireless to Ethernet Bridge?"
date: 2008-06-25
forum: Networking &amp; Wireless
---

### Post by arckeda on 2008-06-25
Hello, and first off thanks for reading this, I am afraid I haven't had much success with the forums as of late.  My problem is that I have a windows computer in my room but no spare wireless cards for it to connect to my router downstairs, I do however, have a wireless Ubuntu laptop that almost never leaves my room.  Right now, on my laptop I have a Broadcom card using ndiswrapper and an ethernet port not being used.  I am wondering if I can connect my desktop to my laptop via ethernet, and then route the connecting through my wireless card, so I can receive Internet on my desktop while maintaining internet on my laptop.  Would this be called bridging?  How can I do it?  Are their any drawbacks?  Thanks a lot.  And if you need me to be more specific, just ask.

---

### Post by kevdog on 2008-06-25
You need to set up IP forwarding on the laptop with packet routing.  To linux and the laptop, it doesnt really matter if the two networking interfaces are wireless, wired, or a combination.  You could do this with a bridge, however I think its easier with internet connection sharing.  This may help you since it using Firestarter (which isn't absolutely necessary).  Firestarter will perform the NAT routing (which it does so be interacting with iptables which is both a firewall and NAT).

Please note that the two cards should be on separate subnets. For example wirless card on 192.168.1.1 and the wired card on 192.168.0.1.  Post back if you have problems, but try to work through the example.  Its fairly straight forward.

---

### Post by kevdog on 2008-06-25
Here is another tutorial although its command line based:

[https://help.ubuntu.com/community/EasyWirelessToWiredConnectionSharing](https://help.ubuntu.com/community/EasyWirelessToWiredConnectionSharing)

Again its basically setting up the nat router with the iptables to do the port forwarding and NAT from computer #1 and computer #2.

---

### Post by arckeda on 2008-06-25
Firestarter looks great, but for some reason I keep getting eth0 busy, any ideas why?  While we are on the subject. :P  Again thanks.

---

### Post by kevdog on 2008-06-25
eth0 busy on what machine?  

Again, when asking for help please be very detail oriented since it will help me out a lot trying to explain things.  

How do you know eth0 is busy? I dont get this.  Usually ifconfig shows the state of the adapters.  Did dmesg say something about this?

---

### Post by arckeda on 2008-06-25
Eth0 on the laptop, sorry again, I know this because firestarter won't let me start networking, it's giving me that error, here is the output of ifconfig on the laptop.

And also, I misread it, it did not say it was busy, it instead said it was not ready.

arckeda@SMALL:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1b:24:d6:60:79
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:220 Base address:0x4000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:364 errors:0 dropped:0 overruns:0 frame:0
          TX packets:364 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:22405 (21.8 KB)  TX bytes:22405 (21.8 KB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:c0:00:01
          inet addr:192.168.53.1  Bcast:192.168.53.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:44 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:c0:00:08
          inet addr:172.16.243.1  Bcast:172.16.243.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:100 errors:0 dropped:0 overruns:0 frame:0
          TX packets:42 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vnet0     Link encap:Ethernet  HWaddr 32:e1:51:5d:ca:f6
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          inet6 addr: fe80::30e1:51ff:fe5d:caf6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:48 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:6244 (6.0 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1a:73:cf:e5:1f
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:73ff:fecf:e51f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1257619 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1267891 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1044009308 (995.6 MB)  TX bytes:837652795 (798.8 MB)
          Interrupt:19 Memory:f6000000-f6004000

---

### Post by kevdog on 2008-06-25
It states its not ready, but this probably isnt correct.

Can you post your /etc/network/interfaces file?

---

### Post by arckeda on 2008-06-25
auto lo
iface lo inet loopback

By the way, thanks for spending the time to help me.

---

### Post by arckeda on 2008-06-25
By the way, is there any quicker way for us to discuss this?  Like in an irc channel or something?

---

### Post by kevdog on 2008-06-25
I see you are probably connecting via Network Manager of the Gui in the toolbar.  Im not sure if everything will work but lets try

Lets just configure the wired device by hand.  We can fine tune everything later.

sudo ifconfig eth0 down
sudo ifconfig eth0 192.168.0.1 netmask 255.255.255.0


Ok now what does ifconfig show?

---

### Post by kevdog on 2008-06-25
There probably is a quicker method, however that would imply I have and IRC account --- which I do, but since I'm not a my specific computer I dont have any software installed.  I'm really doing this by memory -- you are the guinea pig!

---

### Post by kevdog on 2008-06-25
I see a bunch of vm interfaces on the ubuntu ifconfig statements?  Are you running virtual box or vmware?  vm - virtual machine interfaces.

---

### Post by arckeda on 2008-06-25
eth0      Link encap:Ethernet  HWaddr 00:1b:24:d6:60:79
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:220 Base address:0x4000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:364 errors:0 dropped:0 overruns:0 frame:0
          TX packets:364 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:22405 (21.8 KB)  TX bytes:22405 (21.8 KB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:c0:00:01
          inet addr:192.168.53.1  Bcast:192.168.53.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:44 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:c0:00:08
          inet addr:172.16.243.1  Bcast:172.16.243.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:100 errors:0 dropped:0 overruns:0 frame:0
          TX packets:42 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vnet0     Link encap:Ethernet  HWaddr 32:e1:51:5d:ca:f6
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          inet6 addr: fe80::30e1:51ff:fe5d:caf6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:48 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:6244 (6.0 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1a:73:cf:e5:1f
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:73ff:fecf:e51f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1257619 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1267891 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1044009308 (995.6 MB)  TX bytes:837652795 (798.8 MB)
          Interrupt:19 Memory:f6000000-f6004000

arckeda@SMALL:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1b:24:d6:60:79
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:220 Base address:0x4000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:576 errors:0 dropped:0 overruns:0 frame:0
          TX packets:576 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:32589 (31.8 KB)  TX bytes:32589 (31.8 KB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:c0:00:01
          inet addr:192.168.53.1  Bcast:192.168.53.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:44 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:c0:00:08
          inet addr:172.16.243.1  Bcast:172.16.243.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:100 errors:0 dropped:0 overruns:0 frame:0
          TX packets:42 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vnet0     Link encap:Ethernet  HWaddr 32:e1:51:5d:ca:f6
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          inet6 addr: fe80::30e1:51ff:fe5d:caf6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:48 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:6244 (6.0 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1a:73:cf:e5:1f
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:73ff:fecf:e51f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1291705 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1295252 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1091457730 (1.0 GB)  TX bytes:840007786 (801.0 MB)
          Interrupt:19 Memory:f6000000-f6004000


By the way, it seems like firestarter is working now, but I still am trying to connect my Desktop.

---

### Post by arckeda on 2008-06-25
Erg, seems like now my bloody windows box won't detect it's Internet, this may take awhile, but I think it's working now.

---

### Post by kevdog on 2008-06-25
Its working??

Your answer was kind of vague?

---

### Post by arckeda on 2008-06-25
I had to install the ethernet driver on my windows box, hope your still there, my problem is that firestarter seems to be working, and the ethernet on my windows machine seems to be on, but I can't connect to ethernet from my windows box, It says cable unplugged, any ideas?  And yeah, vmware.  Firestarter shows no traffic on eth0 but windows says it's unplugged when it's not.

---

### Post by kevdog on 2008-06-25
I'll have to get back to you tonight on this one.  I have a feeling its a problem with dhcp?  Is this a crossover cable?  It needs to a a crossover cable.

---

### Post by arckeda on 2008-06-25
Your right, damn it, all my cables look the same, I need to find the crossover one I bought.

---

### Post by kevdog on 2008-06-25
Also, Im not sure if your dhcp server will be working with Ubuntu b/c I'm unfamilar if Ubuntu will set this up.

From within windows just wondering if you can set a static IP address of 
192.168.0.5
netmask = 255.255.255.0

Leave gateway open.  I do not think you need to configure this parameter.

---

### Post by trimmer on 2008-06-26
I have to say that after reading this thread that I am really impressed with firestarter. I however would like to be able to configure my own devices. Anyway... Firestarter worked first try. I had already manually configured both interfaces and used Firestarter simply for internet connection sharing. I like that it turns off really easy.

Thanks for these threads! Enough of them and I will make clothes.

Keep them up!

---

### Post by kevdog on 2008-06-26
Perhaps you can share some more details.  Its possible to do this all from the command line, however I thought Firestarter which makes use of iptables nat capabilities was probably the easiest.  Did you have to set a gateway on the second machine, and if so what was the gateway?

---

### Post by arckeda on 2008-06-26
I do not have a set gateway on the second machine, I don't know how to set one on windows, if I ipconfig, it tells me that I have the cable unplugged, I need to buy a new crossover cable.

---

