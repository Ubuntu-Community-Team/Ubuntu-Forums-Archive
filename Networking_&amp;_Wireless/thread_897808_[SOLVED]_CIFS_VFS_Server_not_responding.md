---
title: "[SOLVED] CIFS VFS Server not responding"
date: 2008-08-22
forum: Networking &amp; Wireless
---

### Post by MacDuff on 2008-08-22
Added a PCI 10/100/1000 network adapter to one of my desktop machines which had been running Ubuntu 7.10 satisfactorily with the on-board network adapter, but I wanted to take advantage of my new router capacity. I then installed Ubuntu 8.04 on the machine.

I should also mention that I have a NAS box on the network which is formatted NTFS because it still contains Windows Files for a virtual machine. I mention it only in case it may be pertinent that I am using Samba/CIFS.

The computer LAN throughput does not seem any faster and when I do a shutdown an error message appears:
[13329.017775] CIFS VFS: server not responding
[13329.017823] CIFS VFS: no response for cmd 50 mid 531

Must I disable the on-board network adapter? Or is there some other setting I should be changing? If so how?

Can anyone shed any light on how I can address this?

Thanks

---

### Post by bab1 on 2008-08-22
The errors are from the smbfs/cifs not being able to communicate.  is the new card integrated with your virtual host? Bridged?

---

### Post by MacDuff on 2008-08-22
bab1

I don't know if it is bridged.  I did not do anything to bridge it.  How can I tell if it is and how can I bridge it, if necessary?

Thanks

---

### Post by bab1 on 2008-08-22
Usually the virtual interface ([COLOR="Red"]vrt0[/COLOR] ?) is bridged ([COLOR="Sienna"]br0[/COLOR] ?)to the physical NIC ([COLOR="DarkGreen"]ethO[/COLOR] ?).  If you have added another physical interface ([COLOR="Green"]eth1[/COLOR] ?) then it stands to reason it need to be bridged also ( ([COLOR="DarkOrange"]br1[/COLOR]?).

How does your VM  talk to the physical NIC used by the host OS??  What are the IP addresses (w/subnet masks) fo the various devices?  What are the results of: **ifconfig -a** for the linux host and **ipconfig /all** for the Windows host.

---

### Post by MacDuff on 2008-08-23
mac@DHLWRK:~$ ifconfig -a 
eth0      Link encap:Ethernet  HWaddr 00:0c:76:3e:c7:d2  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Base address:0xe800 

eth1      Link encap:Ethernet  HWaddr 00:18:e7:17:d3:20  
          inet addr:192.168.0.196  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::218:e7ff:fe17:d320/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13108 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14583 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10859387 (10.3 MB)  TX bytes:2936990 (2.8 MB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:688 (688.0 B)  TX bytes:688 (688.0 B)

mac@DHLWRK:~$ 

Windows IP Configuration
Host Name . . . . . . . . . . . . : UBU-XP
Primary Dns Suffix  . . . . . . . : 
Node Type . . . . . . . . . . . . : Unknown
IP Routing Enabled. . . . . . . . : No
WINS Proxy Enabled. . . . . . . . : No
DNS Suffix Search List. . . . . . : DHLTD
Ethernet adapter Local Area Connection 2:
Connection-specific DNS Suffix  . : DHLTD
Description . . . . . . . . . . . : AMD PCNET Family PCI Ethernet Adapter #2    
Physical Address. . . . . . . . . : 08-00-27-8B-36-20
Dhcp Enabled. . . . . . . . . . . : Yes
Autoconfiguration Enabled . . . . : Yes
IP Address. . . . . . . . . . . . : 10.0.2.15
Subnet Mask . . . . . . . . . . . : 255.255.255.0
Default Gateway . . . . . . . . . : 10.0.2.2
DHCP Server . . . . . . . . . . . : 10.0.2.2
DNS Servers . . . . . . . . . . . : 10.0.2.3
Lease Obtained. . . . . . . . . . : Saturday, August 23, 2008 7:19:41 AM
Lease Expires . . . . . . . . . . : Sunday, August 24, 2008 7:19:41 AM

I am using VirtualBox, if that helps
By the way there are quite a few lines displayed that roll by before the two CIFS VFS that remain on screen.  I do not know how to capture them but if they might shed light, advise me how to record them so I can forward it in a posting.

Thanks

---

### Post by bab1 on 2008-08-23
I assume that the [COLOR="DarkGreen"]Linux host[/COLOR] has the 2 NIC's.  My guess is the one with the ip address is the new 10/100/1000 NIC.

I see eth0 is **not** been configured:> eth0 Link encap:Ethernet HWaddr 00:0c:76:3e:c7:d2
UP BROADCAST MULTICAST MTU:1500 Metric:1
And that eth1 has:> Link encap:Ethernet HWaddr 00:18:e7:17:d3:20
inet addr:[COLOR="DarkGreen"]192.168.0.196 ... Mask:255.255.255.0[/COLOR]


The [COLOR="Indigo"]other device[/COLOR] (I'm not sure what it is) has the NIC configured as such:> Physical Address. . . . . . . . . : 08-00-27-8B-36-20
Dhcp Enabled. . . . . . . . . . . : Yes
Autoconfiguration Enabled . . . . : Yes
IP Address. . . . . . . . . . . . : [COLOR="Indigo"]10.0.2.15[/COLOR]
Subnet Mask . . . . . . . . . . . : [COLOR="Indigo"]255.255.255.0[/COLOR]

If these to devices are on the same segment (physical wire (LAN)), they can't talk to each other via TCP/IP.  If they are on the **same physical machine**, the [COLOR="Indigo"]10.0.2.15[/COLOR] address is configured to a virtual NIC and has no way to send packets to the physical NIC and then onto the wire.

Bridging associates th IP addresses by the physical addresses (MAC).  The [COLOR="DarkGreen"]Linux eth1[/COLOR] MAC [COLOR="Magenta"]Ethernet HWaddr 00:18:e7:17:d3:20[/COLOR] and the [COLOR="Indigo"]other device[/COLOR] MAC [COLOR="Magenta"]Physical Address: 08-00-27-8B-36-20[/COLOR].

If we are talking about the NAS and a Linux host, then I would reconfigure one of them so the IP network is the same ie: use either 192.168.0.0/24 or 10.0.2.0/24 (255.255.255.0 = /24).

If we are talking about a VM host then we can use a bridge interface from the virtual NIC to the physical NIC  ie; br0.
See [[COLOR="DarkOrange"]**this**[/COLOR]]("http://lifehacker.com/367714/run-windows-apps-seamlessly-inside-linux") for more information.

Again, let me know if this works or you need any more help.

---

### Post by MacDuff on 2008-08-24
bab1

Your information is WAY over my head.  I have only the very SLIGHTEST idea of what it means.

The setup is that I have an on-board NIC which did not provide gigabit speed so I added a new 10/100/1000 network card and have it connected to my network.  I do not have any cable plugged into the old network receptical (outlet).

I do have a DNS-323 NAS on the network but it is connected through a router.

The computer has VirtualBox installed and the virtual OS is connecting to the network fine (but not providing gigabit speed). 

When I look at the Virtualbox network settings it does not complain and seems happy.

VirtualBox is always shut down when I exit from it and before I shut down the computer.

This is frustrating because I have much the same problem with my laptop which is configured similarly to the desktop machine and it only has one network card in it.  I have a second desktop machine also with Virtualbox but no second network card and it shuts down gracefully with no problem.  GRRRR

If you could provide some simple step by step guidance of what to look for and how to test/change settings, I would be most grateful.  If that is too much trouble, please direct me to somewhere that I might find such information, bearing in mind that I am far from being a penguinista:(.

Thank you

---

### Post by bab1 on 2008-08-24
Ahhhh, a router connecting the network together.

Tell me the following:[LIST]
[*]The IP address of the NAS
[*]The IP address of the host OS we are working with (is it Ubuntu ??)
[*]The IP address of the guest OS we are working with (is it Windows ??)
[*]Confirm that the host OS and the guest OS are on the same physical machine
[*]Confirm that you know how to configure your router
[/LIST]

I'm not even sure we are using the same terms for the various devices at this point.  What do you use VirtualBox for?  Describe the network for me.  Who made the router; what model?

As you can see it's real hard to just give you a step by step check list of things to do.

---

### Post by MacDuff on 2008-08-24
The network consists of two Ubuntu (8.04) machines connected by cable (and having Static IPs) to the router which is a D-Link DIR-655.

Also connected (by cable) to the router is a D-Link DNS-323 NAS device which serves as the main data storage and as a print server for an ink-jet printer

Also connected to the router (by cable) is a laser printer.

In addition there two laptop computers connected to the network by WiFi, from time to time.  One of them is a Lenovo with a recently installed Ubunut 8.04 OS and the other is an Asus EEE machine.

Both of the desktop machines and the Lenovo laptop have VirtualBoxes with Windows XP installed.  The Virtual machines are used only for three applications for which I cannot find Linux replacements and they are seldom used.

Everything was working fine with Ubuntu 8.04 on one of the desktop machines and 7.10 on the other and on the Lenovo laptop. The problem started when I did a clean install of 8.04 on the 2nd desktop and on the Lenovo and at the same time, I installed the gigabit NIC in the same desktop machine that got the fresh installation of 8.04. 

All machines currently function fine on the network (including Virtual XP machines) BUT they do not exchange data over the LAN as fast as they should, given the high speed router, and shutdown takes a very long time on the standard laptop and on the freshly installed 8.04 desktop.  At shutdown, pages of error messages scroll past, ending up with the two that I provided in my first posting. 

The only other thing I can tell you is that I tried to set up a wireless static IP on the Lenovo and had so much difficulty that I finally gave up and went with the roaming option.

The DNS-323 is supposed to support gigabit transfer speeds by the way.

I appreciate the time you are spending on this problem.  I know how frustrating it can be to try to solve a problem when you can't get your hands on the equipment.

---

### Post by bab1 on 2008-08-24
Yes it can be a bit frustrating, but it helps you (knowledge) and me (keeps my skills sharp).  Lets start with your initial problem.  > CIFS VFS Server not responding
This says: "windows sharing" (CIFS) "virtual filesystem" (VFS) "Sever" (the NAS) is not answering to calls.  To me that means your Ubuntu and/or XP host can't talk to the NAS or possibly the attached printer.  This is what I have been trying to solve.   

I don't have enough info to tell for sure, but it looks like your VM hosts (XP ) can see the internet and each other, but I'll bet they don't see or talk to the Ubuntu hosts.  Why? Because you are running two networks on the same physical infrastructure.  I have done that for years at a medical practice I managed.  There just isn't any intercommunication.  That's why I mentioned the bridge.  It connects two different network hosts together.

The D-Link DIR-655 has a switch incorporated with 4 external ports.  The wireless is connected to the switch too.  You should be able to configure most of your network from this device and the computers themselves.

---

### Post by MacDuff on 2008-08-24
BINGO!
The virtual XP box on the new 8.04 install does not see the Ubuntu System on the same computer.  I have not checked further but I think that confirms what you are saying. 

Now I am beginning to get a glimmer (just a glimmer, mind you) of what it is you are telling me.

I guess my next step it to print out the IPCONFIG contents of the Virtualboxes and the IFCONFIGS of the Ubuntu machines, then go in search of the place(s) in which to enter that information.

I am guessing that Ubuntu will need to be told to accept the Virtual machine as a host, and Windows will need to be told to accept the Ubuntu machine as a host.  Do I just assign an IP to the VirtualXP and where do I do that.

Funny I don't recall having to do all this back when 7.10 was installed but I was in such a flap trying to learn all the new "stuff" about Ubuntu, that I may have forgotten much of what I experienced.  The mind suppresses terrible memories, or so I am told:)

Is there anything more you can tell me (in simple terms) before I start on my quest?

Thanks
Mac

---

### Post by bab1 on 2008-08-24
Before you do anything, go back to post #6 and click on the link "This".  It's at the bottom and its in bright yellow!

---

### Post by bab1 on 2008-08-24
Here is a good starting point for bridging VirtualBox on 8.04: [http://samiux.wordpress.com/2008/07/30/bridging-virtualbox-162-on-ubuntu-8041/]("http://samiux.wordpress.com/2008/07/30/bridging-virtualbox-162-on-ubuntu-8041/")

---

### Post by MacDuff on 2008-08-24
Thanks bab1

I have to get back to some other work but I will read the references you provided and get back to solving the problem tomorrow, time permitting.

You have been very kind.

Mac

---

### Post by MacDuff on 2008-08-27
After trying several suggestions without success, I find that quite a few others have had this problem.  It is a bug that has been around for quite a few months and affects some systems with 7.10 and a lot more with 8.04.  

It relates to the shutdown sequence when Samba shares are un-mounted.  For anyone who is interested here is a posting about the subject:
[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/211631](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/211631).

Although not fatal it is a major annoyance and I would have thought it would be addressed by now considering that it appears to have a simple fix.. but what would I know about that?

Until the powers that be get around to fixing the bug here is a workaround that I found at:
[http://blog.avirtualhome.com/2008/03/10/ubuntu-shutdown-problem-cifs-related/](http://blog.avirtualhome.com/2008/03/10/ubuntu-shutdown-problem-cifs-related/)

I will reprint the solution here with a bit of expansion for anyone (like me) who is new to the world of Linux and needs a great deal a hand-holding:

You can use the following work around:
Open a terminal:
Code:   cd /etc/rc6.d   {to change to the directory containing the file to be modified}
Code:   ls -la     {to display the contents of the file}

You will see quite a few lines of type displayed.  Look down the list and on the right side of one of the lines you should see :
" S<nr>wpa-ifupdown  "   and  the "number" will probably  be a value of 15
and
" S<nr>umountnfs.sh " and its  "number" will probably be a value of 31

To fix this problem the "number" of the " umountnfs.sh " must be lower than the number of  your " wpa-ifupdown.sh "
Code:
sudo mv S31umountnfs.sh S14umountnfs.sh

Repeat the above steps also for /etc/rc0.d 
Code:
cd /etc/rc0.d  
Code
ls-la
Code:
sudo mv S31umountnfs.sh S14umountnfs.sh

This worked to fix the problem on a laptop and a desktop machine.  Funny but I did not have the problem with a second desktop machine... go figure.

---

### Post by bab1 on 2008-08-27
I'm curious.  I do not "hard mount" (via fstab) Windows shares at all.  The only hard mounts I have are the partitions I use for serving Samba shares.  I have no problems with bookmarked Windows shares (mappped) or the hard mounts of Samba shares.

Why do you need to "hard mount" the Windows shares?  MS includes both the server and client in their shares. The SMB protocol that MS uses should (and in my case does) interact with smbfs/cifs.  This should be all you need for the Windows shares.  

I don't see the bug at all.  What do the folks at Samba.org have to say?  I think there is a common misconception of the smbfs /cifs protocol.  Am I missing something?

EDIT: I would [COLOR="Red"]*not*[/COLOR] mount the the NAS shares.  See if the NAS is in the same workgroup as the Ubuntu hosts (all should be there).  Then, without the shares mounted, see if you can browse to the shares on the NAS.  I think you can.  If so bookmark them.

---

### Post by MacDuff on 2008-08-27
The reason I mount the drives is because I use a Network Accessible Server as a common data repository for all the computers on my LAN.  It has mirrored drives to reduce the chance of data loss due to mechanical failure and it simplifies backing up to removable media.

By the way bab1, the business of getting the Virtual Machines to speak to Ubuntu that you addressed, is another matter and I have kept your suggestions for when I get around to that.  However it is not pressing because almost all our files, including those used by the virtual machines, are on the NAS and the Virtual Machines have no problem seeing them.  I will get around to it in the next week or so.

Thanks for your input, It was (will be) valuable and had you been fully aware of my situation, it might have been more to the exact point.  That is the problem with providing help from a distance.  There are SO MANY things to take into account.

Cheers
Mac

---

