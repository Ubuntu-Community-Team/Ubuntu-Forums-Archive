---
title: "YAICP-yet another internet connection problem"
date: 2007-02-24
forum: Networking &amp; Wireless
---

### Post by entropyfoe on 2007-02-24
I have searched these forums for a few days, and tried several things so far with no luck.
I have a new fast machine using an Asus M2NPV-VM MB with on board ethernet.  I connect through a D-LINK router to a DSL line.  The set up works under XP, and used to work under Mepis (though Mepis stopped working claiming a Bios bug some ACIP timer thing). I can browse with Firefox, GAIM and so forth with XP and Mepis.

But under Kubuntu, no connection at all. (sorry if spacing is messed up, since the net is down, I have to transfer text on a USD drive, and import into XP)
Here is ifconfig -a


eth0      Link encap:Ethernet  HWaddr 00:18:F3:D1:27:66          
inet6 addr: fe80::218:f3ff:fed1:2766/64 Scope:Link          
UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1          
RX packets:120 errors:0 dropped:0 overruns:0 frame:0          
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0          
collisions:0 txqueuelen:1000          
RX bytes:40163 (39.2 KiB)  TX bytes:0 (0.0 b)          
Interrupt:209 Base address:0x400
lo        

Link encap:Local Loopback        
inet addr:127.0.0.1  Mask:255.0.0.0         
inet6 addr: ::1/128 Scope:Host
          
UP LOOPBACK RUNNING  MTU:16436  Metric:1          
RX packets:67 errors:0 dropped:0 overruns:0 frame:0       
 TX packets:67 errors:0 dropped:0 overruns:0 carrier:0        
collisions:0 txqueuelen:0        
RX bytes:5212 (5.0 KiB)  TX bytes:5212 (5.0 KiB)

sit0      
Link encap:IPv6-in-IPv4
NOARP  MTU:1480  Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0         
collisions:0 txqueuelen:         
RX bytes:0 (0.0 b)  
TX bytes:0 (0.0 b)

entropyfoe@AMDX2:~$ ping 208.67.222.222
connect: Network is unreachable

entropyfoe@AMDX2:~$ sudo ifdown eth0
Password:

Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:18:f3:d1:27:66

Sending on   LPF/eth0/00:18:f3:d1:27:66
Sending on   Socket/fallback

entropyfoe@AMDX2:~$ sudo ifup eth0
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:18:f3:d1:27:66
Sending on   LPF/eth0/00:18:f3:d1:27:66
Sending on   Socket/fallback

DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


SO, I cant ping. I have tried static IP using the setup from Win XP, its dual boot so it is the same hardware.  In the System->Networking eth0 is active, but  the DNS tab has nothing listed in the box (no servers).  If I ping google.com, it says I get "unknown host".
I notice I am getting an ipv6 address-what does this mean?  How does that happen?

In other posts people have asked to see :

entropyfoe@AMDX2:~$ route -n

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

entropyfoe@AMDX2:~$ cat /etc/network/interfaces

auto lo
iface lo inet loopback
auto eth0
iface eth0 inet dhcp
auto eth1
iface eth1 inet dhcp
auto eth2
iface eth2 inet dhcp
auto ath0
iface ath0 inet dhcp
auto wlan0
iface wlan0 inet dhcp

I thought the ipv6 stuff was bad, so I deleted from the hosts a bunch of ipv6 stuff leaing only 127.0.0.1 local host AMDX2 and 127.0.1.1 AMDX2.

I know the hardware is good, the eth0 seems active, but I cannot get out?
Any ideas?  I have seen several threads with similar problems, and they solved it, but failed to post the winning recipe.  (I will not make that error !)

Is there a firewall that could be blocking me?

Thanks in advance!  I really dig Xubuntu, powerful and boots faster than XP, if only I can connect.

Thanks 
Jay

---

### Post by spd106 on 2007-02-24
The main problem is that you are not receiving an IP address from the DHCP server. You can see this because dhclient times out after several dhcp-discovers.

Since it works okay with XP, it's safe to assume that the router is not at fault. So the most likely problem is the ethernet card's driver.

Could you please post the output of **sudo lshw -C network**.

---

### Post by entropyfoe on 2007-02-24
spd106,

Thanks for the lead, it appears there is nothing when I lshw.   All I get is the instructions for lshw-did I screw up the command somehow?

entropyfoe@AMDX2:~$ sudo lshw -c network
Hardware Lister (lshw) - B.02.06
usage: lshw [-format] [-options ...]
       lshw -version

        -version        print program version (B.02.06)

format can be
        -html           output hardware tree as HTML
        -xml            output hardware tree as XML
        -short          output hardware paths
        -businfo        output bus information

options can be
        -class CLASS    only show a certain class of hardware

So now what can I do to get a driver loaded (with no connection)?

According to the motherboard manual I have a Nvidia nForce 430 built in Gigabit MAC with external Marvell PHY.

In my earlier messing around I think I saw a Forcedeath but I don't know why it does not appear here.

Thanks for your help, I am kind of stuck here, and I really want to get this fine OS going on the fast HW.  I am tired of running Linux on old slow boxes.

-Jay
        -C CLASS        same as '-class CLASS'
        -disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
        -enable TEST    enable a test (like pci, isapnp, cpuid, etc. )

---

### Post by spd106 on 2007-02-24
Try **sudo lshw -class network**.

Also check if the forcedeth driver has been loaded with **lsmod**. You can filter the output like so **lsmod | grep force**.

Are you using Dapper 6.04 or Edgy 6.10? It is probably worth updating since the newer kernel has better hardware support for more recent devices.

---

### Post by entropyfoe on 2007-02-24
spd106

OK, some strange behavior...

sudo lshw -class network  

produces no output.  But some text flashes by so fast I cant read it, in CAPS, and then just a blank line prompt.

lsmod | grep force  returns
forcedeth 23428  0

I am running xubuntu 6.06 and am now wondering if I should reinstall with 6.10???

I get a BIOS bug error when I start up, but xubuntu boots through, whereas Mepis is killed by the error

MP-BIOS bug: 8254 timer not connected to IO-APIC

Can this cause the connection problem?

Plus, while doing the lshw, now my right click on the desktop now does not give me the menu of applications including the Quit.  Hmmm????

Thanks for your help, this is what I love with Linux in general, and Ubuntu specifically, the support from the community.

M$ can never get this kind of community, because  they are driven by money and marketing, whereas Linux is driven by a philosophy.

Should I DL 6.10 and reinstall.  I have little to lose on the xubuntu installation, as the network never worked, so I did not do much with it yet.

Thanks
Jay

---

### Post by spd106 on 2007-02-24
It's certainly worth downloading the desktop cd. It should work in the live environment so you can test it out, then if your happy proceed with installation.

---

### Post by mips on 2007-02-24
Suggestion, do a search in this forum for d-link or dlink. It might just help.

---

### Post by entropyfoe on 2007-02-24
mips-

Thanks, good Idea, I will check for others with this router.  Perhaps a firmware upgrade?

But the internet comes through fast and strong with XP and on my Mepis Linux install (until Mepis bombed out with a MP-BIOS bug 8254 timer not connected to IO-AAPIC error)

Mepis is based on Ubuntu, so I thought this would be easy.

Any other ideas?

Thanks
Jay

---

### Post by tgalati4 on 2007-02-24
You mentioned delete ipV6 stuff in the hosts table.  Did you blacklist the ipv6 module?  That could cause translation problems.

What is the output of /etc/hosts?

You should at a minimum have:

127.0.0.1 localhost
127.0.1.1 AMX2

Can you ping your DSL modem:

sudo ping 192.168.1.1

If not then try setting up a gateway:

sudo route add default gw 192.168.1.1

sudo ping 192.168.1.1

If that doesn't work, try rebooting just the router.  Sometimes it needs a kick to share the DHCP love.

Good luck

---

### Post by mips on 2007-02-24
> **entropyfoe said:**
> mips-

Thanks, good Idea, I will check for others with this router.  Perhaps a firmware upgrade?



Search for you model here. In one of my posts I dealt with a firmware issue as well.

Other things to look at are IPv6 and manual DNS configuration.

---

### Post by entropyfoe on 2007-02-26
How do I manually configure dhcp?
I have read instructions, but I must admit I am not clear.
Any good examples of how to do this?

There are many good suggestions in the posts above, and I will try them all when I can, and I may go to 6.10 in a reinstall...

But other problems now, I installed Mepis 6.5 and ripped a new grub, so I must repair the menu.lst in grub to include a xubuntu.

I know this is the wrong forum, but does any xubuntu 6.10 386 Desktop user have the entry for xubuntu  in menu.lst?  Also same for 6.06 LTS.

Could you post these few lines so I can copy into grub.
I can change the hd0,1 stuff as needed.

Thanks
Jay

---

### Post by entropyfoe on 2007-02-26
How do I manually configure dhcp?
I have read instructions, but I must admit I am not clear.
Any good examples of how to do this?

There are many good suggestions in the posts above, and I will try them all when I can, and I may go to 6.10 in a reinstall...

But other problems now, I installed Mepis 6.5 and ripped a new grub, so I must repair the menu.lst in grub to include a xubuntu.

I know this is the wrong forum, but does any xubuntu 6.10 386 Desktop user have the entry for xubuntu in menu.lst? Also same for 6.06 LTS. ( I need both, as I may reinstall with 6.10)

Could you post these few lines so I can copy into grub.
I can change the hd0,1 stuff as needed.

Thanks
Jay

---

### Post by mips on 2007-02-27
> **entropyfoe said:**
> 
I know this is the wrong forum, but does any xubuntu 6.10 386 Desktop user have the entry for xubuntu in menu.lst? Also same for 6.06 LTS. ( I need both, as I may reinstall with 6.10)

Could you post these few lines so I can copy into grub.
I can change the hd0,1 stuff as needed.


Can you not access the xubuntu partition and look in /boot for that ?

---

### Post by entropyfoe on 2007-02-27
Thanks for all your suggestions, I will investigate them all.  This thread is still alive.  And I will post the recipe once I connect !

But, I have bigger problems right now...

I installed Mepis 6.5 beta, and it wiped my grub out.  So, I must add back the xubuntu entries into menu.lst.

I know this is not the right forum, but can anyone display the correct grub/menu.lst for xubuntu 6.06 LTS i386 desktop?

I need the kernel long string/name and the initrd stugg.
I can fix the hd1,2 stuff.

Also  the same stuff for 6.10 i386, as I might just reinstall with the newer version to see if this clears up the connection problem.  Can I install xubuntu without installing grub, and then just add the entry into menu.lst?

Thanks
Jay

---

### Post by entropyfoe on 2007-02-27
mips,

Yes I think I can boot off of the live CD and see the file...copy then add to the Mepis grub.
Thanks

-Jay

---

### Post by entropyfoe on 2007-03-02
Thank you all for your help.

Eventually I just installed 6.10 from the alternate CD, omitting Grub install, and manually entered xubuntu into menu.lst.

Now internet connects without any configuration at all.  As easy as Mepis!

So the router was OK.

Thanks
Jay

---

