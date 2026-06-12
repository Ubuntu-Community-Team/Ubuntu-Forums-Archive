---
title: "Ubuntu 8.10/DSL modem: cannot go online!"
date: 2009-02-11
forum: New to Ubuntu
---

### Post by amko on 2009-02-11
Hey, thanks for reading - Ubuntu rocks!

Just upgraded to Ubuntu 8.10 after a good Ubuntu 7.10 experience, but still a n00b

Anyway, here I go with my problem: cannot connect to the Net, using DSL modem.

--Hardware:

- 2.66GHz Dual-Core Intel Pentium 4 CPU, Intel GGc Motherboard, 1 GB RAM, 40 GB Disk size (single-disk)

- OS : Linux Ubuntu 8.10 (currently installed within Windows XP SP2 - really looking to 'make the switch', soon as I resolve this!)

Issue:

I connect to my ADSL modem via Ethernet. While I can go online in WinXP, I am unable to go online in Ubuntu 8.10.

I 'became root', ran 'pppoeconf' in a terminal window and followed the sequence. Apart from entering my current provider-assigned user name/password when prompted, made no other changes in any settings.

What I've tried so far on my own:

1. Switched back to WinXP, and visited Ubuntuforums.org.

Google search returned a post from Ubuntu 8.10 user, advising that this issue had been resolved as follows: log in as 'root', then in 'Places>Computer>Filesystem>etc>network>interface' , change a word in the last line in the 'interface' file - from ' manual' to 'dhcp'. Switched back to Ubuntu, logging in as 'root', replicated this process and saved the file, then opened Firefox - no dice.


2. Tried running 'pon dsl-provider' - here is the output from the terminal:

amko@ubuntu:~$ sudo pppoeconf
Plugin rp-pppoe.so loaded.
amko@ubuntu:~$ pon dsl-provider
Error: only members of the 'dip' group can use this command.
amko@ubuntu:~$

- I do not understand why I should be receiving this error. Anyway. Logged in as 'root', created a Group called 'dip' (System>Administration>Users and Groups) and assigned my user account ('amko') to the 'dip' group, logged back in as 'amko' user, and...still no dice.

- Then tried running 'plog', here is the output from the terminal:

amko@ubuntu:~$ plog
Feb 10 06:25:00 ubuntu pppd[7357]: Connection terminated.
Feb 10 06:25:30 ubuntu pppd[7357]: PPP session is 55720
Feb 10 06:25:30 ubuntu pppd[7357]: Using interface ppp0
Feb 10 06:25:30 ubuntu pppd[7357]: Connect: ppp0 <--> eth0
Feb 10 06:25:32 ubuntu pppd[7357]: Remote message: Authentication failure
Feb 10 06:25:32 ubuntu pppd[7357]: PAP authentication failed
Feb 10 06:25:32 ubuntu pppd[7357]: Connection terminated.
amko@ubuntu:~$

- Needless to add, unable to get online...


- Then went to 'System>Preferences>Network Configuration', in the 'Network Connections' dialog, saw 'DSL', 'Wired' and 'Point-to-Point Protocol' tabs, in 'DSL', saw current DSL service provider name displayed, selected it, then clicked on 'Edit', the 'DSL' tab dialog was displayed, re-typed my user ID/PPP/password. Then clicked on the 'Wired' tab, on clicking this, saw that the 'MAC' field was blank. Is this a problem - do I need to add the address?

Now requesting your advice, thanks. Will write up the process in detail once resolved and re-post for mutual benefit.

(What's that? Why am I not approaching my DSL provider for help? Um, I did try calling Support. When I said Linux there was an eerie silence followed by 'our technical dept. will call you'. I'm still waiting...)


Thank you kindly for your time and support.

Aaaand...hey, Ubuntu rocks!
amko

---

### Post by yeats on 2009-02-11
So you have an external router that is already configured to accept the PPPoE connection, right?  If so, what typically happens is that the router is the DCHP server, in which case you should be able to connect via eth0 (your default ethernet jack) to your router.  All the PPP configuration would only be necessary if your computer was accepting the router connection directly.  Or maybe I'm misunderstanding the situation . . .

If you will, open a terminal and run this command:

```
sudo gedit /etc/network/interfaces
```

and paste the contents here.  Another command you can try in the terminal is 

```
sudo dhclient eth0
```

which has your computer search for a DHCP connection on your network.  If it doesn't work, please post the output here.

Oh, and it's worth mentioning that there is not a need to log in as root to do anything on Ubuntu.  Prefacing commands with "sudo" will allow you to be root in a particular instance.

---

### Post by superprash2003 on 2009-02-11
if you still have problems post output of ifconfig from the terminal..are you able to access [http://192.168.1.1](http://192.168.1.1) ??

---

### Post by amko on 2009-02-12
@ chrissharp 123:

First, thanks much - appreciate it.
OK, you said:

-- Run:
sudo gedit /etc/network/interfaces

and paste the output.

Here it is:

auto lo
iface lo inet loopback


auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider

auto eth0
iface eth0 inet dhcp

-- Next, you said:

 Run:
sudo dhclient eth0

and paste the output.

OK, here it is:

amko@ubuntu:~$ sudo dhclient eth0
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:16:76:7f:ae:36
Sending on   LPF/eth0/00:16:76:7f:ae:36
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 18
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
amko@ubuntu:~$ 

(end)

@superprash2003

Thanks for your input, appreciate it.
--------------------------------

You said: if you still have problems post output of ifconfig from the terminal..

OK, here it is:

amko@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:76:7f:ae:36  
          inet6 addr: fe80::216:76ff:fe7f:ae36/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:23707 errors:0 dropped:0 overruns:0 frame:0
          TX packets:178 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1432741 (1.4 MB)  TX bytes:25051 (25.0 KB)
          Interrupt:21 Base address:0x1000 

eth0:avahi Link encap:Ethernet  HWaddr 00:16:76:7f:ae:36  
          inet addr:169.254.6.70  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:21 Base address:0x1000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:26 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1828 (1.8 KB)  TX bytes:1828 (1.8 KB)

amko@ubuntu:~$ 


-- Next, you asked:

Are you able to access [http://192.168.1.1](http://192.168.1.1) ??

No.

-------------------------------------------------

Hope this helps, thanks. Over to you, folks...thanks again.

Ubuntu rocks!
amko

---

### Post by superprash2003 on 2009-02-12
your eth0 isnt getting.. try getting one via dhcp from your router by typing **sudo dhclient eth0** is 192.168.1.1 your router ip address?

---

### Post by amko on 2009-02-12
@superprash2003

You said: your eth0 isnt getting.. try getting one via dhcp from your router by typing sudo dhclient eth0

ok thanks. and here is the output of the above:

amko@ubuntu:~$ sudo dhclient eth0
[sudo] password for amko: 
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:16:76:7f:ae:36
Sending on   LPF/eth0/00:16:76:7f:ae:36
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
amko@ubuntu:~$ 

(end)

-- and yes, i do believe [http://192.168.1.1](http://192.168.1.1) is my modem address...

What does this mean, please. And what am I missing?

Ubuntu rocks!

---

### Post by trdofMSoft on 2009-02-12
Could you post the results of ipconfig /all in xp?

---

### Post by yeats on 2009-02-14
Yes - trdofMSoft is right - this will let us know the IP range of your network.

From your responses, it sounds like you're just pasting in commands without knowing exactly what they do (which is generally fine to do on the forums, by the way).  Forgive me if I'm wrong here :-). To give you some context:

```
sudo gedit /etc/network/interfaces
```

The /etc/network/interfaces file shows how your network interfaces are defined for your computer to see.  The lines

```

auto eth0
iface eth0 inet dhcp
```

are telling your computer to automatically bring up eth0 (which is the name of your primary Ethernet connection), and to use DHCP to configure the IP address.  Incidentally, this may be in conflict with this line in the PPPoE section, which also seems to want to bring up eth0:

```
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
```

but I don't know that that's the problem.

```
ifconfig
```

(or "_i_nter_f_ace _config_uration) is a command that lets you know how your networking interfaces are configured at any given time.  This is the same as "i_p_config" Windows.  When your network it connected the way it should be you should see something like this for eth0:

```

eth0      Link encap:Ethernet  HWaddr 00:11:11:18:d2:2b
          **inet addr:192.168.1.123  Bcast:192.168.1.255  Mask:255.255.255.0**
          inet6 addr: fe80::211:11ff:fe18:d22b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:23502 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20566 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:23715821 (22.6 MB)  TX bytes:2695055 (2.5 MB)

```

That second line that I highlighted in bold is the one we're looking for.  If there is no IP listed, you're not on the network.

Finally,

```
sudo dhclient eth0
```

This is running the program "dhclient" which automatically searches for an IP address from your DHCP server.  Something in your configuration is not allowing that to happen, hence the "No DHCPOFFERS received" line.

I would look into undoing the ppp configuration.  Did you follow instructions to do this in the first place?  I haven't needed to set up my network that way before, so I just don't know.

---

### Post by amko on 2009-02-14
@trdofMSoft:

You said: Could you post the results of ipconfig /all in xp? 
-- Thanks for looking in and for your input.

Funny thing is, I cannot locate the command prompt in this installation of Windows XP - for some reason when I click on 'Start', I cannot see 'Run' listed. I tried Start>Programs>Accessories> too, but no dice. Please let me know how to get to it and I will run 'ipconfig /all'/paste the output.

@chrissharp123:

Thanks much for taking time to put together the detailed and helpful response. (And yes, you're right, I'm just pasting in the output as directed without context!) 

OK, you said: 'I would look into undoing the ppp configuration. Did you follow instructions to do this in the first place?'
-- No, I have not. Did someone really suggest I 'undo the ppp configuration' here before? :) Oh, they did? Where? :(

And speaking of reviewing the thread: chrissharp123, the output pasted when superprash2003 suggested I run 'ipconfig' does seem to  contain an IP address - I have re-pasted a part of the output below (please see the bold line): 

eth0:avahi Link encap:Ethernet HWaddr 00:16:76:7f:ae:36
**inet addr:169.254.6.70 Bcast:169.254.255.255 Mask:255.255.0.0**
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
Interrupt:21 Base address:0x1000

Does this help?

---

### Post by superprash2003 on 2009-02-14
i think it would be better if you setup static ip [http://www.prash-babu.com/2008/11/how-to-setup-static-ip-address-in-linux.html](http://www.prash-babu.com/2008/11/how-to-setup-static-ip-address-in-linux.html) .. and then try accessing [http://192.168.1.1](http://192.168.1.1)

---

### Post by yeats on 2009-02-14
> 
OK, you said: 'I would look into undoing the ppp configuration. Did you follow instructions to do this in the first place?'
-- No, I have not. Did someone really suggest I 'undo the ppp configuration' here before? Oh, they did? Where? 

I don't see that someone has suggested that here, no.  What I was trying to ask was how you went about installing/configuring your ppp configuration in the first place, so you could try to uninstall/unconfigure it.  I don't think your eth0 interface is going to work with those conflicting lines in /etc/network/interfaces.

---

### Post by tsali on 2009-02-14
I don't think you are using a router.

It look like you are connected directly to the ADSL modem via ethernet.

You are suffering from authentication failure.

Who is your ISP?

---

### Post by amko on 2009-02-15
@superprash2003

Thanks, checked out the info on your site re: changing from 'dhcp' to static IP, noted.  



@chrissharp123:

You said: What I was trying to ask was how you went about installing/configuring your ppp configuration in the first place, so you could try to uninstall/unconfigure it. I don't think your eth0 interface is going to work with those conflicting lines in /etc/network/interfaces.

- You know, I do not recall installing/configuring ppp in the 'XP-only' era...discovered 'ppp configuration' only when I installed Ubuntu v 8.10, blissfully unaware about it prior. (*Not* that I'm yearning for those days.)

Ok, so I tried running 'pppoeconf' and again followed the process - then tried running 'pon dsl-provider', but couldn't. Here is the output:

amko@ubuntu:~$ sudo pppoeconf
[sudo] password for amko: 
Plugin rp-pppoe.so loaded.
amko@ubuntu:~$ pon dsl-provider
Error: only members of the 'dip' group can use this command.
amko@ubuntu:~$ 


Still no closer to understanding 'dip' group. As those among you might recall, before starting this thread, I tried creating a new group called 'dip', and assigning 'amko' (me) to it.  (chrissharp123 - before you ask, I have no idea what I'm doing :)) 

@tsali

Thanks for writing in. 

You said: 'I don't think you are using a router'.

- I believe this PC connects to a Motorola 4-port  ADSL cable modem/router combo via Ethernet - said device provided by the ISP (their details below as requested).

You said: 'You are suffering from authentication failure'.

- Now you mention it, I do recall seeing this exact phrase in one of the outputs returned against one of the commands - sorry, cannot recall exactly which one.

Is this an ISP-related issue, then?  ISP Tech Support did say something like 'Linux is not a supported OS but we'll need to confirm'...as I said before, 'someone should be getting back to me', which I'll be sure to let you know about when (if?) it does happen.

The Internet provider is You Tele ([http://www.youtele.com/](http://www.youtele.com/)), btw. 

To sum up, options at this stage (please pitch in):

- run 'ipconf /all' in XP and post the output (how? see my earlier post re: this)

- change to static IP, as superprash2003 suggests

- undo/re-do the ppp config (how exactly?), as chrissharp2003 advises

- follow up with the ISP re: Linux compatibility

- ...?


Thanks all!

---

### Post by trdofMSoft on 2009-02-15
you can start the command prompt by clicking cmd.exe found in the \windows\system32 folder.

Since we know xp works, this will take all the guess work out of these network settings.

In the majority of cases, the pppoe settings are in the router, which make them unnecessary in the computer.

If the output of ipconfig /all is 192.168.1.x, start your web browser and type 192.168.1.1 in as an address. Log into the router.  If you see your isp account user name and password set in the router, the router is handling pppoe, and you will need to remove the "dsl" connection that you set up in ubuntu.  From there we will be working with the "wired" connection.
But I'll wait to hear back from you.

Dale

*(Another way to get some clues is to call back the isp, and have them walk you through setting up xp manually. Write down what choices they tell you to make in the "wizard", this will tell you what settings you will need in ubuntu.  What your ISP meant when they said Linux is not supported is that THEY don't offer tech support on configuring Linux. I hope those replies will one day be a distant memory.)*

---

### Post by trdofMSoft on 2009-02-15
While you are in xp, go into device manager and note the name of your ethernet hardware.  When you boot back into ubuntu, go to system administration, and select hardware testing.  When you get to the ethernet test, compare the hardware that ubuntu detected with the results from device manager.  they should be the same

---

### Post by amko on 2009-02-16
@ trdofMSoft:

Thanks much for your time and patience (and follow-up).

Ok, I ran ipconfig /all and am enclosing a screenshot of the output - hope it came thru ok/you're able to see it. Else please let me know, I'll type out/post the output). 

I noticed straight off that for 'You Tele ppp adapter YouTele', dhcp is 'not enabled'. Do I need to (if yes, how do I) enable it? 

I'll try the Ubuntu hardware test in a bit and update you.

Thanks again, later.

---

### Post by amko on 2009-02-16
@trdofMSoft:

Ok, so I logged back into Ubuntu and ran the Hardware Testing wizard.  The Ethernet hardware is indeed recognized as the same hardware as that listed by 'Device Manager' in XP. That's good to know :) 

Dale, looking at the screenshot I attached before, I note that the output of 'ipconfig /all' does not mention '192.168.1.x' - and that visiting 'http://192.168.1.1' in my browser currently returns a blank screen. 

Until your next then, thanks.

Cheers,
amko

---

### Post by trdofMSoft on 2009-02-16
Unfortunately, I can't read the screen on the jpg, it is too low res.  Once I have your output of ipconfig, I will be able to tell you if you need to enable dhcp.

---

### Post by amko on 2009-02-16
@ trdofMSoft:

Sorry for that screenshot, my bad. Here's the output of ipconfig /all: 

Microsoft Windows XP [version 5.1.2600]
(c) Copyright 1985-2001 Microsoft Corp.

C:\Documents and Settings\Administrator\Desktop>ipconfig /all

Windows IP configuration:
	Host name:......................: HOME
	Primary DNS suffix..............: 
	Node type.......................: unknown
	IP Routing Enabled..............: No
	WINS Proxy Enabled..............: No

Ethernet adapter Local Area Connection

        Connection-specific DNS suffix .:
	Description.....................: Realtek RTL8139 Family PCI Fast Ethernet NIC
	Physical address................: 00-16-76-7F-AE-36
	Dhcp enabled....................: Yes
	Autoconfiguration enabled.......: Yes
	Autoconfiguration IP address....: 169.254.226.190 
	Subnet mask:....................: 255.255.0.0
	Default gateway.................: 169.254.226.190

PPP adapter YouTele 
	
        Connection-specific DNS suffix..:
	Description.....................: WAN (PPP/SLIP)Interface
	Physical Address................: 00-53-45-00-00-00
	Dhcp enabled....................: No
	IP address......................: 219.91.208.225
	Subnet mask.....................: 255.255.255.255
	Default Gateway.................: 219.91.208.225
	DNS Servers.....................: 208.67.222.222
					  208.67.220.220
	NetBIOS over TCP/IP.............: Disabled

C:\Documents and Settings\Administrator\Desktop>169.254.226.190

(end)

Hope this helps and thanks again,

amko

---

### Post by trdofMSoft on 2009-02-16
PPP adapter YouTele

Connection-specific DNS suffix..:
Description.....................: WAN (PPP/SLIP)Interface
Physical Address................: 00-53-45-00-00-00
Dhcp enabled....................: No
[B]IP address......................: 219.91.208.225
Subnet mask.....................: 255.255.255.255
Default Gateway.................: 219.91.208.225
DNS Servers.....................: 208.67.222.222
208.67.220.220[/B]
NetBIOS over TCP/IP.............: Disabled

Above tells us that you have a static ip address because dhcp is not enabled.  The settings in bold print are the settings that you will use with ubuntu. go to system -> administration -> network.  select unlock and enter your password.

Now here's where my knowlege begins to fade as I have never used pppoe in ubuntu.  either highlight wired or the "dsl" entry. select properties. Make these changes in one or the other..(unless someone else knows and chimes in.) run sudo pppoeconf again. if it doesn't work, try it with the other. you might have to experiment a bit.

---

### Post by amko on 2009-02-22
Hi trdofMSoft, superprash2003, chrissharp123, tsali, others. 

As yet unf. *not* online. But then I'm sure it's just me. Checking in with a status update:

Basically, following the advice received thus far, I tried changing 'interface' from dhcp to static, and tried reconfiguring PPPoE. Without progress. Details for your consideration:

-- I modified the 'interfaces' file (/etc/network/interfaces). The file now reads as:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 219.91.208.225
netmask 255.255.255.255
gateway 219.91.208.225

(Btw, the ip adresses above are from the output of 'ipconfig /all' in xp, posted here earlier.)

-- After making changes to 'interface' as above, I saved the file/closed it. Then tried to run 'sudo /etc/init.d/networking restart'. Here is the output:

root@ubuntu:~# sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          
grep: /etc/resolv.conf: No such file or directory
grep: /etc/resolv.conf: No such file or directory
                                                                         [ OK ]
root@ubuntu:~# 

I then tried visiting [http://192.168.100.1/](http://192.168.100.1/). Following changes above, was able to see the home page of the cable modem - showing cable modem status as 'operational'.  I clicked on a link marked 'Configure' and in the page served, I notice that there is a checkbox next to "Enable DHCP server." I'm wondering, is this setting in any way conflicting with my attempt to configure eth0 over to the 'static ip address'?

-- Anyway, after running 'sudo /etc/init.d/networking restart' as above, I ran 'sudo pppoeconf'. Then tried accessing the Web using Firefox - no dice. 

After this, ran 'plog' and 'ifconfig ppp0': here are the outputs:

(plog)
root@ubuntu:~# plog

(ifconfig)
root@ubuntu:~# ifconfig ppp0
ppp0: error fetching interface information: Device not found

Ok, other than changing the 'interfaces' file as above, have tried configuring eth0 using the GUI method - in the 'Network Connection' dialog box (System>Preferences>Network Configuration), changed 'DHCP' to 'manual' and added IP addresses (from 'ipconfig /all' output in xp) to both 'Wired' and 'DSL' tabs. No dice. 

Obviously missing something, but have no idea what that might be. TIA for any suggestions/support, appreciate it.

Ubuntu rocks!

cheers,
amko

---

### Post by amko on 2009-02-27
OK, now online. Yes! 

A Linux guru (who would rather remain anonymous) just analyzed the output of various terminals posted here/your helpful advice and advised that I 

- modify the 'wired' tab in 'Network Tools' (System>Preferences>Network Configuration>Wired), also
 
- undo all recent changes to the 'interfaces' file (delete static IP config lines added, change back to 'dhcp' from 'manual, etc.')

- assigned permissions to save the file with the new (i.e., original) code - which wasn't happening using the GUI to configure 'Wired'. As previously mentioned, this is a bug already reported in Launchpad by a fellow user.

Thanks much to all here - and case closed!

Ubuntu rocks! (and will even more, no doubt,  once the bug is fixed...)

Cheers,
amko

---

