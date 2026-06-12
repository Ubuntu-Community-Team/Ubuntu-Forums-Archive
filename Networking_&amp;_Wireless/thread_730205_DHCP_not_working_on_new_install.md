---
title: "DHCP not working on new install"
date: 2008-03-20
forum: Networking &amp; Wireless
---

### Post by MDMS on 2008-03-20
Hey I hope you guys can help me.  Here is an overview of what I've got:

IBM380Z Laptop (rather old), the PC Card slot contains a card with USB 2.0 ports, a USB 2.0 to Ethernet adapter.  I've installed Xubuntu 7.1 from the 'alternate' cdrom (the regular install CD didn't work for me -- hung on disk partitioning).  The install when smoothly except the Ethernet couldn't be configured.

(NOTE: Before proceeding, I should add that this same laptop with the configuration as above had Windows ME OS running on it and DHCP was working fine!)

Anyhow, the _problem_ is that I can get any Ethernet functionality at all; not even ping works.  And, since I'm not networked, I'm typing this on my Windows XP computer!

To help myself, I've tried the instructions at: [https://help.ubuntu.com/7.10/internet/C/troubleshooting.html](https://help.ubuntu.com/7.10/internet/C/troubleshooting.html) ....

I typed:  sudo lshw -C network...
the good news is that the Ethernet interface seems to be recognized through the PC Card / USB2.0 interface.  To summarize, the ethernet interface is an ASIX chip AX88178 and its full duplex 1000Mb/sec capable.  The logical name is eth0 and the MAC address is also displayed.

NOTE: This is a _wired_ ethernet configuration that I'm trying to get working.  In case it matters, my home router is a D-Link DI-707 and I've got 3 other Windows computers connected to it right now, all being served by DHCP.

When I type ifconfig, I notice that my inet addr is set to 192.168.1.7 (I was hacking), my Bcast is 192.168.1.255 and Mask is 255.255.255.0....  Only the eth0 and lo interfaces are present.

Note that I also have an irda0 ethernet interface which I shut down but its inet addr is set to 192.168.0.199 (this is from my initial installation dialog when installing from CDROM).

I also think my route is messed up.  When I type route I get:
192.168.1.0 (destination) * (gateway) 255.255.255.0 (genmask).... eth0

More facts about my network:
The Gateway should be 192.168.0.1 (the address of my router).  Note that I tried to change the route above but I always get an error and the route table is not changed.
My router is assigning addresses in the range 100 to 198  (eg. 192.168.0.175).
I can't ping my router.
The command: sudo dhclient eth0 ....  never succeeds.
Rebooting the laptop doesn't help either (so far).

I did disable ipv6 by editing /etc/modprobe.d/aliases and changed a line to 'alias net-pf-10 off' and rebooted just in case this would help but it didn't.

I've been hacking a bit to try and get ethernet to work but only with the ifconfig and route commands.

So, there you have it.  Please ask me for any information that I might have missed.

---

### Post by Eiríkr on 2008-03-20
It sounds like your eth0 interface is not configured for DHCP, but is instead set up for a static connection.  This could be why none of your network stuff is getting automatically assigned (IP address, route, etc).

So here's an idea -- we're going to rework your [font=courier]/etc/network/interfaces[/font] file.  We'll first make a backup copy:
```
sudo cp /etc/network/interfaces /etc/network/interfaces.BAK
```

Now we'll edit the file:
```
sudo gedit /etc/network/interfaces
```

Leave your lo lines as-is.  Find the lines relating to your eth0 interface, and edit / replace them to look like this:
```
auto eth0
iface eth0 inet dhcp
```
Save and exit gedit.

Now restart your network:
```
sudo /etc/init.d/networking restart
```

Post any error messages from the restart and the output from [font=courier]ifconfig[/font] here, and we'll go from there.

HTH,

Eiríkr

---

### Post by MDMS on 2008-03-20
OK.  I did what you've suggested.

After restarting my network, DHCP still fails (No DHCPOFFERS received....... sleeping).

The output if ifconfig is as follows:
(Its a good thing the two monitors are close together, I've got to transcribe everything..)

eth0  Link encap:Ethernet  HWaddr ........
         UP BROADCAST RUNNING MULTICAST MTU: 1500 Metric: 1
.................
.............

eth0:avah Link encap:Ethernet  HWaddr <as above>
                 inet addr:169.254.5.234  Bcast:169.254.255.255  Mask: 255.255.255.0
                 UP BROADCAST RUNNING MULTICAST MTU: 1500  Metric: 1

lo           Link encap:Local Loopback
              inet addr:127.0.0.1 Mask: 255.0.0.0
              UP LOOPBACK RUNNING MTU: 16436  Metric: 1
.....................
...............

(The status for errors, dropped, overruns, frame, carrier, collisions were all 0.)

('I don't think I made a transcription error for the output of ifconfig, hope you don't mind the .....'s.)

---

### Post by Eiríkr on 2008-03-20
The "No DHCPOFFERS received" bit tells us that either a) your DHCP server (likely your router?) isn't working correctly (unlikely, but a possibility), or b) your machine isn't connecting through to the DHCP server at all.  This could be due to a hardware problem, like a bad cable or loose connection, but then again you said this same physical setup works fine on Windows, which makes me think it's due to a software problem, such as a driver issue.  Driver issues are out of my league, unfortunately, so we must ask someone else to pitch in.  

Any takers?

Cheers,

Eiríkr

---

### Post by MDMS on 2008-03-20
OK.  Thanks for your input.  At least my /etc/network/interfaces file got clean up.

---

### Post by MDMS on 2008-03-25
Hi everyone.

Well, its been almost one week and I've just been watching my original post slide down the newsgroup list and become stale...  I've also been searching the forum for others with the same Ethernet/DHCP problem and trying out the suggested solutions, no luck, and; it seems that most of them still don't have working ethernet as well.  No new takers?!?!?

For me, nothing has changed, I just can't get DHCP or even a static IP to work.  ALSO, it seems that a lot of ubuntu people are having trouble with Ethernet connections while for others it 'just works'....  It would be interesting to know the percentage of users with working Ethernet connections versus not working and categorizing the problem hardware, but of course such information would be difficult to collect.

Just to verify that my old hardware's ethernet connection still works with at least one OS, I will probably try and install Windows ME on the laptop again; I just want to see ethernet working with absolutely no hardware changes (eithernet did work with Windows ME before).  I can't create a dual-boot system because the hard drive is just too small to make it useful in such a configuration (only 4 GB hard drive and 168 MB RAM).

Other questions:
--> Assuming it _is_ a driver problem I have, what output of which commands should I try and capture?  How do I actually get a developer's attention and get help?  Is this the correct forum?  Is there paid support and would it help me get ethernet working?
--> Should I try an older version of Xubuntu where I might have a better chance of getting ethernet to work?
--> Should I wait for a newer release of Xubuntu to become available?
--> Should I just use my old laptop as a doorstop and forget about it?

Thanks!

---

### Post by Eiríkr on 2008-03-26
Have a look at [post=4585373]this post[/post] and the related thread -- someone else had exactly your issue, with a simple (but counter-intuitive) fix.  I suspect the problem is related to Ubuntu's poor choice of the Network Manager app, which is implicated in *many* posts on this board in connection with various network problems.  Anyway, try what arnaud13 did, and maybe also / instead consider replacing Network Manager with WICD, which comes highly recommended by other forum posters, and is available for download from [its Sourceforge page]("http://wicd.sourceforge.net/").  

Cheers,

Eiríkr

---

