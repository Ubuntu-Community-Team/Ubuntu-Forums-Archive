---
title: "Problem with ReakTek 8168 Ethernet Card"
date: 2008-04-29
forum: Networking &amp; Wireless
---

### Post by faminator on 2008-04-29
Brand new HP Pavilion Desktop
Just installed Hardy, Dual booting with Vista
Using the Live CD the ethernet worked OK but it did take a long time to configure apt.

After install network card doesn't work.
It has worked once but stopped after a restart.

Manually configured IP

** In Vista Wake On Lan after shutdown is enabled.

> famine@six:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1e:8c:de:b5:fc  
          inet addr:192.168.1.106  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:8cff:fede:b5fc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:4294967287 overruns:0 frame:0
          TX packets:0 errors:0 dropped:46 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:220 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2552 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2552 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:128008 (125.0 KB)  TX bytes:128008 (125.0 KB)


> lspci -nn | grep Ethernet
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev ff)


> famine@six:~$ sudo ethtool eth0
[sudo] password for famine: 
Settings for eth0:
	Supported ports: [ TP ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Advertised auto-negotiation: Yes
	Speed: 1000Mb/s
	Duplex: Full
	Port: Twisted Pair
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: on
	Supports Wake-on: pumbg
	Wake-on: pumbg
	Current message level: 0x00000033 (51)
	Link detected: yes


> famine@six:~$ lshw -C network
WARNING: you should run this program as super-user.
PCI (sysfs)  
  *-generic               
       description: Ethernet interface
       product: Illegal Vendor ID
       vendor: Illegal Vendor ID
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: ff
       serial: 00:1e:8c:de:b5:fc
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master vga_palette cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.2LK ip=192.168.1.106 latency=255 maxlatency=255 mingnt=255 module=r8169 multicast=yes
famine@six:~$ 
famine@six:~$ sudo lshw -C network
PCI (sysfs)  


Let me know if I need to provide any other info.

Any ideas?

Thanks 
Famine

---

### Post by faminator on 2008-04-29
New info.
I have been able to get it to work a couple of times after powering down disconnecting power for 15 seconds and powering up, but not consistently.

Seems there are many Realtek problems. Anyone have any insight?

Famine

---

### Post by faminator on 2008-04-29
So I left in unplugged for a while and it booted fine with the NIC working.
Went for dinner and after coming out of Hibernate the nic was dead again.

Can anybody help?

Famine

---

### Post by faminator on 2008-04-29
Hello....
Anybody there?

Anyways I am going to try to install 7.10 on another partition to see if this is a Hardy issue.

Any help at this point would be great.

Famine

---

### Post by AgDon92 on 2008-05-20
Hello,
I've been struggling with a problem with my Realtek 8168 card on Ubuntu 8.04 as well.  Someone finally posted a solution that worked for me...Here it is...

absolute solution

hi bud,i had the same problem with 8168 and only this solved it now all is ok... 

To compile the working r8168 driver you need to:

sudo apt-get install patch (from cd after adding cd-rom in software sources)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
This is how to add cd-rom...
sudo apt-cdrom add
sudo apt-get *package here*
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

sudo apt-get install build-essential

wget [ftp://66.104.77.130/cn/nic/r8168-8.006.00.tar.bz2](ftp://66.104.77.130/cn/nic/r8168-8.006.00.tar.bz2)

tar -xjvf r8168-8.006.00.tar.bz2

cd r8168-8.006.00/src



[http://www.jamesonwilliams.com/bin/r8168_scripts.tar.bz2(this](http://www.jamesonwilliams.com/bin/r8168_scripts.tar.bz2(this) link will provide u the necessary patch script - r8168-8.005.00.hardy.diff.txt-)Then copy the attached patch to the r8168-8.006.00/src directory



patch < r8168-8.005.00.hardy.diff.txt

cd ..

make clean

make modules

sudo make install

sudo depmod -a

sudo mkinitramfs -o /boot/initrd.img-`uname -r` `uname -r`



Then you need to black list the r8169 driver:

sudo sh -c 'echo "blacklist r8169" >> /etc/modprobe.d/blacklist-network'

gksu gedit /etc/modprobe.d/blacklist



 and add r8169 to end of d page,



sudo update-initramfs -c -k all



sudo reboot.



***************

Hope that helps.

Cheers.

Don

---

### Post by khughitt on 2008-05-28
This did the trick for me... Thanks! One thing to note though is that each time you upgrade your kernel you will have to go through most of the steps again (all except for adding the items to the blacklist). Otherwise the fix works perfectly :)

---

### Post by faminator on 2008-05-28
Thanks for the help.
Finally had a chance to apply the change yesterday.
It appears to have fixed it.
I will repost if the problem reappears.

Also thanks for the heads up about updating the kernel.

Famine

---

### Post by mabodo on 2009-01-26
Hi!

(firstly sorry for my english, and say that i'm really noob at linux)

I'm exact in the same trubble, but i can't do:

"apt-get install ********"


'cause of course I don't have internet...

What can I do???

I've tryied to add to a Cd in other linux computer, but an error happens

---

### Post by elfstone2 on 2009-10-30
Hello,
I had the same problem, and got the same solution, and it worked... until now. I updated to 9.10, and the r8168 doesnt compile with 2.6.31.. anything I can do about that? any help?

cheers,
Thomas

---

### Post by mtwomey on 2009-11-04
Yes, you can get a patch for it here: [http://www.jamesonwilliams.com/hardy-r8168](http://www.jamesonwilliams.com/hardy-r8168)

See Jameson's comment #199 

Thanks,

-Matt

---

