---
title: "Need help to make MTU=9000 permanent"
date: 2008-09-07
forum: Networking &amp; Wireless
---

### Post by gknippels on 2008-09-07
I'm running Ubuntu 8.04 Hardy Heron and use the Intel PRO 1000/GT network adapter. I have a gigabit ethernet network at home and normally use the adapter with Jumbo Frames enable at MTU=9000. This gives a signicant boost in the data transfer rates.

Whenever I boot, the default MTU = 15000, and I can change the MTU to 9000 for each session by manually typing :

sudo ifconfig eth0 mtu 9000

but would like to make it permanent. 

Can somebody tell me how to do this? :confused:

I appreciate the help

---

### Post by Winston_Smith on 2008-09-07
Found this on another forum
> 
It can be passed via /etc/sysconfig/network-scripts/ifcfg-ethX

where ethX is the interface you want to change.

Check the man pages or scripts for allowable entries...

Hint: Look at /etc/sysconfig/network-scripts/ifup-*

This was ona Mandriva forum, but it might also work for Ubuntu

---

### Post by caljohnsmith on 2008-09-07
If your NIC is listed in /etc/network/interfaces, then you can just add "mtu 9000" at the end of its listing. For instance, if your Intel Pro NIC is "eth0", then look in the interfaces file for the line beginning "iface eth0 ..." and add "mtu 9000" to the end of that stanza. Let me know how it goes or if you need more details/info. :)

---

### Post by gknippels on 2008-09-07
CalJohnSmith:
Thanks for your reply. Unfortunately my /etc/network/interfaces looks pretty empty. It contains only:

[B]auto lo
iface lo inet loopback[/B]

No entry for the intel adapter. Can I add as section to /etc/network/interfaces to descibe the adapter? What would such a section look like?

I'm pretty sure that eth0 is the intel adapter since ifconfig gives:
[B]
eth0      Link encap:Ethernet  HWaddr 00:0e:0c:c0:5c:7b  
          inet addr:192.168.1.18  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:cff:fec0:5c7b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:99 errors:0 dropped:0 overruns:0 frame:0
          TX packets:140 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13806 (13.4 KB)  TX bytes:20741 (20.2 KB)
          Base address:0xd000 Memory:f7020000-f7040000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1730 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1730 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:87140 (85.0 KB)  TX bytes:87140 (85.0 KB)[/B]

Winston Smith:
Thanks for your reply but my Ubuntu installation doesn't have a /etc/sysconfig directory

---

### Post by caljohnsmith on 2008-09-07
Did you use System > Admin > Network (Gnome's network manager) to set up your ethernet NIC? Or did you use something else? If you use the network manager to set up your eth0 interface, I believe it always saves its settings to /etc/network/interfaces. Try that and let me know if your eth0 interface then shows up in /etc/network/interfaces.

---

### Post by puppywhacker on 2008-09-07
for ubuntu / debian the network interfaces are configured in:
/etc/network/interfaces

the stanza should then look something like
[INDENT]iface eth0 inet dhcp
[INDENT]address 192.168.2.9
netmask 255.255.255.0
mtu 9000
[/INDENT][/INDENT]
the directory /etc/sysconfig/network-scripts is the equivalent for mandriva / redhat / fedora

---

### Post by gknippels on 2008-09-07
CalJohnSmith & Puppywacker,

I had no entries in my /etc/network/interfaces file, even though my network card had been automatically recognised when I install Ubuntu.
I had to 'manually' configure it in System->administration->network with a static IP to have it show up in /etc/network/interfaces.
After it showed up, I've added the line

MTU 9014 

and now it automatically sets it correctly when I start up Ubuntu! Problem solved.

Thanks all for your help! Ubuntu and this forum are great. 
All I have to do now is get my ATI card work without flickering! (problem posted in Multimedia & Video section of the forum).

---

