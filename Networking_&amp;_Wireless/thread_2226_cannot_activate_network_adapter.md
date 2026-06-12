---
title: "cannot activate network adapter"
date: 2004-10-26
forum: Networking &amp; Wireless
---

### Post by jure on 2004-10-26
Hi!

I'm very new to this forum and to the linux world altogether. I just installed Ubuntu 4.10 "The Warty Warthog" Linux on my computer, and I'm having trouble installing network adapter, more specific I'm having troubles activating it. My networks adapter is located on ISA slot, and it is labeled eh0 in network setup. The problem is when I try activating it, it show filled checkbox next to adapter name, and after approx. three seconds checkbox is cleared! What could be wrong? Where should I look for solution or what should I try to do to make my network adapter to work?

Thanks in advance!

regards,
  jure

---

### Post by HungSquirrel on 2004-10-26
There could be many problems.  Your network could be down/unplugged/etc.  Most likely you have your networking set to automatically get an IP address, etc. via DHCP.  If your ISP doesn't support this (although most do now), you may have to call them and get the information for the blanks in Interface Properties manually.  (I am assuming that you are talking about the dialog box at Computer -> System Configuration -> Networking.)

Another problem could be that your card wasn't automatically detected by Ubuntu.  If you know it, tell us the model number of your card.  Another thing that may help us is the output of the *lsmod* command.  If you can, execute that command in a terminal, copy the output, and save it to a floppy or something so you can move it to a computer that has working internet and post it here.  :)

---

### Post by jdelo on 2004-10-26
Is your device eh0 or eth0?  Either way you should check your: /etc/network/interfaces file and make sure the device is listed correctly. something like this:

auto eth0
iface eth0 inet dhcp


If it is then go to terminal and type: ifconfig eth0 up <hit enter>
this should bring the device up.
 please let me know what you interfaces says.
also type iwconfig <enter> in terminal and let me know your ESSID and your Mode

Thanks,
Jeff

---

### Post by psychcom on 2004-10-27
same problem here.
ubuntu runs on a compaq EVO N1020v.
the eth0 is running ipv6 and dont have a mac add...
now i want it to run ipv4 and have a mac..
could it be that the card isnt detected ?

---

### Post by jure on 2004-10-27
Hi!

Just want to point out that I'm setting my IP configuration manually. This is computer with IP address 192.168.0.3 (subnet 255.255.255.0). This is actually second machine on my LAN, and I'm using router for internet access and I've configured router's address as a gateway on this interface. Although I'm not sure about interface name (eh0 or eth0), so I will have to look it up...

Currently I cannot try anything, since I'm not arround my computer, but I'll try it later...

And thanks everyone for your answers and guidelines!

regards,
  Jure

---

### Post by Trograin on 2004-10-30
Hi!

I am using a HomePNA card (Device: 79c978 [HomePNA]).
During isntallation Ubuntu didnt want to connect to the internet even though I manually added my static IP information (Wich I know by heart). After the installation was kind of finnished, I logged in to Ubuntu and manage to find the card in the device managaer. The information is correct in the interfaces allso and the iface shows correct information. Actually, to be hoenst all the files and the configurations are showing correct information but still no internet. Still no connecting to the net at all, I even tryed to use the DHCP, but noooo, nothing :(

PLeazze help me, anyone???

PLeaze email the information or post on the forum. I am getting desperate :(

Have tryed with slaxkware, and now Ubuntu, and still same problem :(

[email]boban@danpat.fi[/email]

---

### Post by TekMate on 2004-10-30
Have you checked this out yet?
[http://www.homepna.org/support/faqs.asp#FAQ6](http://www.homepna.org/support/faqs.asp#FAQ6)

---

### Post by Trograin on 2004-10-30
Thanx for that link but thoose drovers are supporting older versions of the linux kernel, 2.4 versions, something tells me that its waste of time trying with thoose...or?

pleazze tell me if I am wrong?

---

### Post by TekMate on 2004-10-30
It has some decent info like the name of the module is il so you could try 
modprobe il
ifconfig eth0 up
dhclient

It may work may not just throwing it out there to try.

---

### Post by wongg62 on 2004-11-20
Hi, I have the same problem as the first person above, when I configure network adapter and click activate, the check mark dissapears after a few seconds. It is configured as dhcp. This problem has kept me from using debian and some other distributions but knoppix and some other distros work. If this helps, ifconfig eth0 gives me

root@ubuntu:/home/gary #ipconfig eth0
etho 0   Link encap: Ethernet HWaddr 00:A0:CC:68:8D:00
         inet6: addr: fe80::2a0:ccff:fe68:8d00/64 Scope:Link
         UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
         RX packets:0 errors:0 dropped:0 overruns:0 frame:0
         TX packets:82 errors:11 dropped:0 overruns:0 carrier:8
         collisions:0 txqueuelen:1000
         RX bytes:0 (0.0 b) TX bytes:7652 (7.4 kiB)
         Interrupt: ll Base address: 0xd000

If anyone else needs anything please let me know, I do not have wireless and my network is connected to a dsl router

---

### Post by Dundeviant on 2004-11-27
I too have the same problem as wongg62 and jure. The network adaptor ( Realtek 8139) seems to be defaulting to ipv6 rather than ipv4. Is there some way to change this ?

---

### Post by strawberry on 2004-11-28
Like in the headline, I'm not able to activate the 2nd NIC card anyway. 

I have a PCI RTK8029 to the LAN and the other one ISA SMC8416 to the WAN. At installation Ubuntu recognizes the PCI one but not the ISA. It also ignores the ISA SB sound card even that is a pnp device.
I uderstand that ubuntu has a new hw detect package called discover1 and it eliminates the former modconf module. 
I'm suspicious ubuntu (or debian sid itself) do not supply ISA devices at all.

I hope will get a solution (or confirmation) at this matter with your help.

---

### Post by selphish189 on 2004-12-12
Hi!
I have the same problem with my network adapter, the Device Manager reconizes the device (as have every other disto i have ever installed (slack, redhat, mandrake) sis 900 however it seems that IPv6 is the defalt setting.

---

### Post by selphish189 on 2004-12-13
so i have narrowed down the problem (aka not fixed but closer)
i think that  it has somthing to do with my ifconfig setup:
when i run ifconifg -a i get a list of devices, namely my eth0 and my ath0 as well as my loopback,  however on thing that i do not know what it is, is sit0.
the comand "sudo ifconifg sit0" gives me-
sit0      Link encap:IPv6-inIPv4
            NOARP MTU:1480 Metric:1
            RX packets:0  errors:0 dropped:0 overruns:0 frame:0
            TX packets:0  errors:0 dropped:0 overruns:0 carrier:0
             colisions:0 txqeuelen:0
             RX bytes:0 (0.0b)  TX bytes:0 (o.ob)

I am not sure what this all means, however i think it has somthign to do with the fact that my eth0 interface wants to find everything as IPv6
hope someone with more techncial know-how can find this helpful

---

### Post by rekurzion on 2004-12-13
Again, I am having the same problem.  

I have recently switched to Ubuntu with great success.  Many of the features and hardware that I could not get to work with RedHat . . . (I know) works like a charm in Ubuntu.  Until today I was having NO! problems at all.

I was attempting to try out my wireless card via the built setup for wireless internet (I did not install or download anything).  

I have AT&T DSL setup through a BritePort DSL Modem connected to a Linksys broadband router.  This setup has worked through all of the Linux distros which I have used.  Although, AT&T requires password and setup for PPPoE with routing there service, all of this which I have not been able to configure yet in Linux (I do not see a place to enter name and password for Ethernet connections), so I am resolved to do this through the setup on my Windows Patition.

While trying to setup the wireless link, i unplugged my ethernet cable.  And since then linux boot up has not been able to start up networking (and yes I have plugged the hard wire ethernet cable back into the system).  It can see the device from device manager but when I attempt to activate eth0 I get the same problem, check box is marked only for a little while the disapears.  On the same laptop the connections works with Windows.

If there is a solution to this please provide, it seems to be a growing and similar concern.

---

### Post by rekurzion on 2004-12-13
Well, I solved my problem that quickly, maybe this might help for others.

If you check your /etc/network/interfaces file and find something to effect of

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp
name Ethernet LAN card

Then you are good, however, my problem was that I had a lot of extra wireless setup in there when I was trying to get wireless to work.  After backing the original interfaces file then deleting everything that was not a working component of my system (ie. I only have the loopback and the one primary network interface working) I was able to reboot and have Ubuntu setup internet again.  My gues is that there are conflicts when more than one primary network interface is defined (maybe symbol table issues in the network interface).  

But of course, be sure to backup this file before making changes, so if you blow something up, you can always failsafe back in and return to the oringal file.

Worked for me :)

---

