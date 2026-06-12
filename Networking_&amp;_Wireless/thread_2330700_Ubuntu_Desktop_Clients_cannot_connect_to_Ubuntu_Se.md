---
title: "Ubuntu Desktop Clients cannot connect to Ubuntu Server Share via Samba"
date: 2016-07-13
forum: Networking &amp; Wireless
---

### Post by cackles on 2016-07-13
I have been stuck with a problem for days now and I have no idea where I am going wrong. I cannot get my Ubuntu clients to connect to my Ubuntu server.

I am running my machines on VMWare but I am sure that is not the problem, but for arguments sake and to rule it out I will explain my setup and why I think it is not VMWare. All of my machines are on the same net and can see each other. VMWare tools are fully deployed and working 100%.

I've lost count how many machines I have setup, I really should just snapshot, but here is the current layout:

Host:

Master (Windows 10)

Clients:

Ubuntu (Ubuntu 64 Desktop)
DroidKiller (As above)
Mother (Win 7 client)

I get 2 different results when I run smbtree:

```
cackles@ubuntu:~$ smbtree
Enter cackles's password: 
WORKGROUP
	\\UBUNTU         		ubuntu server (Samba, Ubuntu)
		\\UBUNTU\Microsoft_XPS_Document_Writer:2	Microsoft XPS Document Writer
		\\UBUNTU\Fax:3          	Fax
		\\UBUNTU\Microsoft_Print_to_PDF:4	Microsoft Print to PDF
		\\UBUNTU\EPSON81939C:1  	EPSON81939C
		\\UBUNTU\IPC$           	IPC Service (ubuntu server (Samba, Ubuntu))
		\\UBUNTU\print$         	Printer Drivers
	\\SLAVE2THEBOX   		ishare
	\\MOTHER         		
	\\MASTER         		
	\\EPSON81939C    		
	\\DROIDKILLER    		DroidKiller server (Samba, Ubuntu)

```

```
cackles@DroidKiller:~$ smbtree
Enter cackles's password: 
WORKGROUP
	\\SLAVE2THEBOX   		ishare
	\\MOTHER         		
	\\MASTER         		
	\\EPSON81939C    		
	\\DROIDKILLER    		DroidKiller server (Samba, Ubuntu)

```

I have done so many configurations and tried so many tutorials I think my nose is about to bleed.

Edit: I should add both my Window's host and client can connect to the samba shares.

Edit-Edit:

Just ran sudo apt-get install cifs-utils winbind

and now get:

```
cackles@DroidKiller:~$ smbtree
Enter cackles's password: 
WORKGROUP
	\\UBUNTU         		ubuntu server (Samba, Ubuntu)
	\\SLAVE2THEBOX   		ishare
	\\MOTHER         		
	\\MASTER         		
	\\EPSON81939C    		
	\\DROIDKILLER    		DroidKiller server (Samba, Ubuntu)
		\\DROIDKILLER\Microsoft_XPS_Document_Writer:2	Microsoft XPS Document Writer
		\\DROIDKILLER\Fax:3          	Fax
		\\DROIDKILLER\Microsoft_Print_to_PDF:4	Microsoft Print to PDF
		\\DROIDKILLER\EPSON81939C:1  	EPSON81939C
		\\DROIDKILLER\IPC$           	IPC Service (DroidKiller server (Samba, Ubuntu))
		\\DROIDKILLER\print$         	Printer Drivers

```

---

### Post by TheFu on 2016-07-14
For Unix-to-Unix file sharing, NFS is the better choice. Seriously. IMHO.  NFS is faster.  NFS provides the expected Unix permissions.  You can run both CIFS and NFS on the same storage.
[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo) has the long version with lots and lots of other things included that aren't needed for simple, small, home, setups.  There's a link near the top for a minimal setup too. Assuming all the userids and groupids that will use NFS storage already are the same on all systems, this is a 3-5 minute effort to setup NFS - 30 min if you don't know what you are doing.

If you are security paranoid, NFSv4 will use Kerberos system to system authentication.

---

### Post by cackles on 2016-07-14
> **TheFu said:**
> For Unix-to-Unix file sharing, NFS is the better choice. Seriously. IMHO.  NFS is faster.  NFS provides the expected Unix permissions.  You can run both CIFS and NFS on the same storage.
[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo) has the long version with lots and lots of other things included that aren't needed for simple, small, home, setups.  There's a link near the top for a minimal setup too. Assuming all the userids and groupids that will use NFS storage already are the same on all systems, this is a 3-5 minute effort to setup NFS - 30 min if you don't know what you are doing.

If you are security paranoid, NFSv4 will use Kerberos system to system authentication.

Thanks, I will give that a look at when I get up.

I was just looking to use the same setup as I have though. I have the Samba passwords setup, but not ruling anything out just now.

Edit:
Read the introduction on it, now I probably won't be sleeping anytime soon :)

---

### Post by TheFu on 2016-07-14
Completely understand - options.  NFS does rock. It is still morning here, so I won't be sleeping anytime soon either. ;)

For system to system communications, ensure that name resolution is working for all the boxes. Doesn't matter if that is /etc/hosts or zeroconf or running a DNS server. All the systems need to know the **same name** for each other. That is step 1.

Maybe this will help, if you stay with CIFS servers.
[https://help.ubuntu.com/community/How%20to%20Create%20a%20Network%20Share%20Via%20Samba%20Via%20CLI%20(Command-line%20interface/Linux%20Terminal)%20-%20Uncomplicated,%20Simple%20and%20Brief%20Way](https://help.ubuntu.com/community/How%20to%20Create%20a%20Network%20Share%20Via%20Samba%20Via%20CLI%20(Command-line%20interface/Linux%20Terminal)%20-%20Uncomplicated,%20Simple%20and%20Brief%20Way)!

If it doesn't, please run **testparm** and post the output. This is for the servers.  

For Linux to Windows (Win-hosted shares), check for any added security that Win10 added which isn't supported by samba yet.  I've had to turn down some security previously with new versions of Windows when the Linux connector (RDP) didn't support it yet.  There was an issue with Win10 clients connecting to samba servers  - vaguely recall it from last fall.  I don't have Win10 and never plan to touch it, ever, so can't check this.  My Win7 client accesses samba shares fine. 

But for Ubuntu-to-Ubuntu file sharing, NFS is the way on a LAN.  Over the internet, you can use sshfs.

---

### Post by cackles on 2016-07-15
> **TheFu said:**
> Completely understand - options.  NFS does rock. It is still morning here, so I won't be sleeping anytime soon either. ;)

For system to system communications, ensure that name resolution is working for all the boxes. Doesn't matter if that is /etc/hosts or zeroconf or running a DNS server. All the systems need to know the **same name** for each other. That is step 1.

Maybe this will help, if you stay with CIFS servers.
[https://help.ubuntu.com/community/How%20to%20Create%20a%20Network%20Share%20Via%20Samba%20Via%20CLI%20(Command-line%20interface/Linux%20Terminal)%20-%20Uncomplicated,%20Simple%20and%20Brief%20Way](https://help.ubuntu.com/community/How%20to%20Create%20a%20Network%20Share%20Via%20Samba%20Via%20CLI%20(Command-line%20interface/Linux%20Terminal)%20-%20Uncomplicated,%20Simple%20and%20Brief%20Way)!

If it doesn't, please run **testparm** and post the output. This is for the servers.  

For Linux to Windows (Win-hosted shares), check for any added security that Win10 added which isn't supported by samba yet.  I've had to turn down some security previously with new versions of Windows when the Linux connector (RDP) didn't support it yet.  There was an issue with Win10 clients connecting to samba servers  - vaguely recall it from last fall.  I don't have Win10 and never plan to touch it, ever, so can't check this.  My Win7 client accesses samba shares fine. 

But for Ubuntu-to-Ubuntu file sharing, NFS is the way on a LAN.  Over the internet, you can use sshfs.

This link pretty much shows how I set my server up.
[https://ubuntuforums.org/showthread.php?t=2268558](https://ubuntuforums.org/showthread.php?t=2268558)

I used the server IP, which I shouldn't have needed to, after reading 16.04 problems regarding the same issue. It only allowed me to connect once though. After I rebooted the client it takes forever to connect again. Transfer speed and access once connected is fast.

Now it is really starting to bug me.

I have 7 x Windows clients in the house using Win7, 8.1 and Win10 that can all connect easily to the shares, just the Ubuntu clients don't seem to want to.

I will install an earlier version of Ubuntu later and see if that works, I should have a couple ready to go somewhere, just need to find the virtual disks.

My router/DNS is 192.168.0.1 

All my hosts are the same, with the exception of their relative names

127.0.0.1       localhost
127.0.1.1       UbuntuTwelve

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

Interfaces has the standard 3 lines, 2 of which being code.

---

### Post by TheFu on 2016-07-15
Sounds like you have a name resolution issue.  127.0.1.1/127.0.0.1 doesn't help any system discover the other machines on the network.  You need to setup something that handles that for IP networking.  Unix doesn't scream "here I am" like Windows does on the network. That method from hte 1980s just doesn't scale or route.

There are 3 options.
1) setup /etc/hosts on every machine (including Windows) that knows all the static IPs for the systems on your network. Yes, you want them to have static IPs if they run any service. No DHCP, though ....
2) setup a DNS server ... either on the router (openwrt/tomato/pfsense all can do this) that lets all the clients and server find each other OR on any of the systems on the network. Just be certain that you tell all the machines to use this internal DNS. If you do go this way, it would be smart to setup DHCP reservations on the router too, especially for laptops and other portable devices. [http://blog.jdpfu.com/2011/07/18/use-your-router-to-centralize-your-network-device-management](http://blog.jdpfu.com/2011/07/18/use-your-router-to-centralize-your-network-device-management) tries to explain.
3) Setup Bonjour/zeroconf .... if you do this, all the machines will be access using the .local TLD.   Try to **ping ubuntutwelve.local** - does it work? [https://help.ubuntu.com/community/HowToZeroconf](https://help.ubuntu.com/community/HowToZeroconf)

BTW, hostnames and domainsnames are NOT case sensitive.  It is best to make them all lowercase so that a bug with a stupid programmer/script doesn't break things.   For example, UbuntuTwelve -->  ubuntutwelve .  In theory, it shouldn't matter, but ... 25 yrs of doing this stuff says to change it.

Wow, that was long for something that is part of basic network setup and necessary for all networks.

When you are done, every machine should be able to ping every other machine on the network by name, period. If not, start over and fix this.  Unix systems use IP networking - old school style. Recently, some distros have added things trying to make this system IP to IP location stuff easier. I always disable it due to issues that I've had over the years.  To much easier to setup an /etc/hosts file and share all but the top 2 lines across all my systems.  1 little command does that for my Unix network - don't have any idea how to accomplish the same thing in Windows ... bet they just use a central DNS because any other way would be too hard.

---

### Post by cackles on 2016-07-15
> **TheFu said:**
> Sounds like you have a name resolution issue.  127.0.1.1/127.0.0.1 doesn't help any system discover the other machines on the network.  You need to setup something that handles that for IP networking.  Unix doesn't scream "here I am" like Windows does on the network. That method from hte 1980s just doesn't scale or route.

There are 3 options.
1) setup /etc/hosts on every machine (including Windows) that knows all the static IPs for the systems on your network. Yes, you want them to have static IPs if they run any service. No DHCP, though ....
2) setup a DNS server ... either on the router (openwrt/tomato/pfsense all can do this) that lets all the clients and server find each other OR on any of the systems on the network. Just be certain that you tell all the machines to use this internal DNS. If you do go this way, it would be smart to setup DHCP reservations on the router too, especially for laptops and other portable devices. [http://blog.jdpfu.com/2011/07/18/use-your-router-to-centralize-your-network-device-management](http://blog.jdpfu.com/2011/07/18/use-your-router-to-centralize-your-network-device-management) tries to explain.
3) Setup Bonjour/zeroconf .... if you do this, all the machines will be access using the .local TLD.   Try to **ping ubuntutwelve.local** - does it work? [https://help.ubuntu.com/community/HowToZeroconf](https://help.ubuntu.com/community/HowToZeroconf)

BTW, hostnames and domainsnames are NOT case sensitive.  It is best to make them all lowercase so that a bug with a stupid programmer/script doesn't break things.   For example, UbuntuTwelve -->  ubuntutwelve .  In theory, it shouldn't matter, but ... 25 yrs of doing this stuff says to change it.

Wow, that was long for something that is part of basic network setup and necessary for all networks.

When you are done, every machine should be able to ping every other machine on the network by name, period. If not, start over and fix this.  Unix systems use IP networking - old school style. Recently, some distros have added things trying to make this system IP to IP location stuff easier. I always disable it due to issues that I've had over the years.  To much easier to setup an /etc/hosts file and share all but the top 2 lines across all my systems.  1 little command does that for my Unix network - don't have any idea how to accomplish the same thing in Windows ... bet they just use a central DNS because any other way would be too hard.

Thanks for all your help, especially the last 3 -because you will laugh at this ... maybe :/

I am only testing the connectivity to make sure it works on my current setup.

One plan is to put something like an RPi3 between my modem and the HP 1920 PoE+ L3 switch. IP cameras will be getting added that as well.

The Pi will be running something like IPCop and will be the DNS etc. I just forgot to buy 2 x USB GB adapters.

Another, my current favourite, is to install IPCop on my server -which is also my main computer. In that case I would use the Microsoft loopback adapter as the network connection for all machines. Modem > onboard Gigabit adapter > my 4 port gigabit pcie card > L3 switch using port bonding or Modem > onboard Gigabit adapter > my 4 port gigabit pcie card > 1-room1 router/2-room2 router /3-room3 router /4-room4 router.

So either way the physical setup will change.

---

### Post by TheFu on 2016-07-16
A little advice on equipment:

Rpi make terrible routers. GigE over USB with a Rpi isn't gonna happen. It isn't designed for that speed.  My LUG has been doing tests on stuff like this.  Rpi are not designed for throughput, even the v3. A little over 12MB/s, that's all.  That means a Rpi isn't even good for backup server duty.  The wifi only gets 40Mb/sec.  Sure, the CPU is 50% faster than the v2, but not much else has changed that I can see.

Depending on where you are in the world, the $145-ish PCengines APU2 (can't be sold to consumers inside the EU for some reason) might be a good alternative (6W of power) or an Ubiquiti router-lite ($60). This little machine will easily last 10 yrs and keeping it patched/maintained with any of the x86 Linux/BSD router/firewall distros quarterly is easy.  Just replaced an Alix here after a decade use - need to get ready for GigE WAN connections which the Alix just can't touch. 
Stay away from consumer routers for the WAN connection - they can never be maintained for the life of the HW thanks to lacking firmware updates after 2-3 yrs, pre-inserted back doors. After market firmwares don't get updated nearly enough. dd-wrt stable is 8 yrs old, for example! For wifi, use ubiquiti stuff. It is sooooooooo much better than the others and cheap, but if you already have some wifi-APs and/or routers and need to reuse it, just keep it away from the WAN connection.  I'm using a tp-link device (has back doors and flaky dd-wrt support) that has been repurposed as a wifi AP and placed in the center of the house. The WAN port cannot be used on it.  If I hadn't spent $150 on it 4 yrs ago, before I saw the light, it would be a Ubiquiti mounted from the attic/ceiling and I'd have 2x better wifi coverage for the entire house.  In a prior job, I did over 1200 wifi deployments NOT using Ubiquiti.  I've only done a few with ubiquiti and their stuff is amazing and cheap.  I don't use wifi much - just for a chromecast and house guests. My stuff is on a different LAN.  Also love the PoE aspect of Ubiquiti - was a little apprehensive the first time, now I think it is magic and see all sorts of other ways to use it, if needed.  Setup a $60 Ubiquiti AP  in my house before deploying it at a client location. Even in a less than optimal location, it covered the entire house, garage, upstairs, downstairs, and half of the yard. This wasn't even the LR version. The signal was great even in the far corners.

I would never mix the WAN router with any other purpose. Security. If a NIC is shared, there are attack vectors.  If things fail on that machine, it could be bad.  For inside the network, I've played with virtual routers (I do lots of virtual machines here), cheap consumer routers. At work, we used Juniper and Cisco stuff - not really that impressed for the value of those devices. Plus they are power hogs - at least ours were.  My DNS/DHCP server is actually inside a tiny VM running pfsense. It is not a router or a firewall. I use pf on the WAN firewall. Something about BSD's network stack gives me comfort.  Plus backup/restore of pfsense is bonehead simple - they have a button AND it works, perfectly.  I could see where using Linux for that would be just as great.  I should mention that my network was hacked in 2002 through BIND (DNS), so I'm especially careful about making that available outside. I don't do that anymore - $20/yr to a DNS provider solves the public DNS aspect for my public IPs.

Looked at IPCop 5+ yrs ago. Also looked at smoothwall and a few other linux firewall distros, but at the time, it was for a client in a fairly hostile environment and they really needed some QoS that worked to manage 60+ users with just 1Mbps fibre connection. Back then, Linux QoS wasn't that great.  They had a small campus with 5 Ubiquiti outdoor APs that worked really well. That client converted me to Ubiquiti stuff.  Anyway, discussions with some security experts I trust pointed me to pfsense/opensense over any Linux-based solution.

Sorry - didn't mean to write this much. I've just been disappointed and think a workable, 10 yr solution isn't that hard anymore for people with a little tech knowledge who can use a screwdriver.

Or not. We all have different experiences and need to follow our own path.

---

### Post by cackles on 2016-07-16
Fire away, the more info the better, actually thanks for taking the time to explain it :)

I just cut down from 3 physical machines to 1, I was hoping to keep it that way.

I was going to go rack-mount and instead bought an Obsidian 950D and water-cooling. I went a bit OTT because of that.

[UserBenchmarks: Game 101%, Desk 125%, Work 112%](http://www.userbenchmark.com/UserRun/1120429)
CPU: [Intel Core i7-5820K](http://cpu.userbenchmark.com/Intel-Core-i7-5820K/Rating/2579) - **95.4%**
GPU: [Nvidia GTX 970](http://gpu.userbenchmark.com/Nvidia-GTX-970/Rating/2577) - **85.5%**
SSD: [Samsung 950 NVMe PCIe M.2 512GB](http://ssd.userbenchmark.com/SpeedTest/38554/NVMe-Samsung-SSD-950) - **273%**
SSD: [SanDisk X110 mSATA 256GB](http://ssd.userbenchmark.com/SpeedTest/10872/SanDisk-SD6SF1M256G1022) - **89.5%**
HDD: [WD Green 3TB (2011)](http://hdd.userbenchmark.com/WD-Green-3TB-2011/Rating/1415) - **69%**
HDD: [Seagate Desktop HDD 4TB (2013)](http://hdd.userbenchmark.com/Seagate-Desktop-HDD-4TB-2013/Rating/1598) - **91.1%**
RAM: [Unknown 8x8GB](http://ram.userbenchmark.com/SpeedTest/90352/Unknown-8x8GB) - **115.6%**
MBD: [MSI X99S SLI PLUS (MS-7885)](http://www.userbenchmark.com/System/MSI-X99S-SLI-PLUS-MS-7885/7724)

Plus my net connection is over 200Mb and will increase next year. Seems no matter what the advice is to have another device as the firewall.

OK, so ... I will forget the Pi3 and take an old Core2Duo, put my 2 port PCI-E network card into that and install pfsense into it. At the same time install the 4-port NIC and pfsense on my server and run that virtually to do the DHCP and DNS.

Does that sound about right? I got the iso and usb installs for pfsense.

I do have one possible problem with that setup. I have a Google router on another network. It downloads to HQ every night and I was hoping to keep it away from my personal network, like even physically. The reason being when my 60 odd Android machines cycle it will flood them with crap (which might be funny ... but) it isn't something I want to do.

On top of that I am wondering if pfsense would like a device 'doing its own thing'.

Well I guess I will find out during the week.

---

### Post by TheFu on 2016-07-16
I don't really track hardware that closely. Since I don't game, it doesn't matter after a certain point provided the systems have vt-x, vt-d, sufficient CPU and enough RAM for the tasks required, I'm good.  Only 1 of my systems has over 8G of RAM and it is using, right now, .... 
```
$ free -mh
             total       used       free     shared    buffers     cached
Mem:           15G       9.9G       5.8G       3.5M       130M       1.2G
-/+ buffers/cache:       8.6G       7.1G
Swap:          11G         0B        11G

``` and running 6 VMs.   Looks like I don't need any swap. Time to clean that up.  Of course, the Windows VM uses most of the CPU. It is a hog.

WAN Edge Routers are special devices. They really, really, need to be separate hardware, IMHO. There are others with different opinions, of course.  I've seen routers pwn'd a bunch. There's a botnet using consumer routers, APs and webcams/nanny-cams now.

C2D is fine, but those CPUs suck a bunch of watts. A new, energy efficient device that can handle 550-900Mbps would be nice, right?  Plus it is tiny - like a normal home router, silent and passively cooled. And over the life of the device, the power savings will more than pay for it ... for my location, it will take about 2.5-3 yrs for the power savings to pay the $150 purchase costs.  I dumped my last C2D about 2 yrs ago due to Perf/W/$ considerations. Used them for years as VM workhorses back when I ran infrastructure for 2 other companies.  I always want to have 2 systems capable of running all the VMs needed here, redundancy.  Moving VMs back and forth between them isn't a big deal anymore and sometimes there are failures with cheap HW like I purchase. At home, I use the google HW philosophy after decades doing the telecom redundancy inside the HW philosophy (which costs 3x more) and often doesn't really provide sufficient redundancy.

pfSense is an impressive routing solution. You pick which ports are for what purpose.  That can mean 3 WAN and 1 LAN ports, if that is your need OR 1 WAN and 3 LAN ports.  Be certain to use Intel PRO/1000 NICs. Realtek requires 20x more CPU than the intel NICs do and Intel is much better supported by BSD.

I used dd to shovel a pfSense image onto an SDHC card and that has been running for the last month in the APU2 box.  The image comes with 3+ partitions already there ... Thing A/B for the OS, so that OS upgrades are risk-free.  There's always a prior copy of the OS available, so if things go badly, we can always boot the older OS.  I understand that using an SSD would make the throughput 30% faster than my SDHC storage - according to a friend with GigE service and the same HW.   Anyway, the router distro is just that - a router distro - so it can handle routing as needed - almost anything you can imagine, just limited by HW and HW support.  Playing with pf in a VM is good practice, plus you can backup all or selected settings as desired and restore those on other pf systems. 

pf is highly flexible. You pick which ethernet port is used for what you need it to be used as. That can be multiple WAN, multiple LAN, plenty of VLANs, and nearly unlimited subnetting, if you want that.  I tend to keep things simple and split my subnets on physical layers.  $20 GigE switches are cheap and work just as well as $120+ managed switches, except I can't remotely manage the switch. OTOH, I've never needed to manage these switches - that's what the router is for.

Ok - we are so far off-topic is isn't funny.  I'm gonna unsubscribe.

---

### Post by cackles on 2016-07-16
Thanks for the help :)

It isn't exactly off topic because it is a hurdle I need to over come anyway to solve my initial problem ... best excuse I can come up with, lol.

If you are interested these are the two cards I have, might set up a hardware discussion about them ;)

[https://www.amazon.co.uk/gp/product/B00AWP9MGG/ref=oh_aui_search_detailpage?ie=UTF8&psc=1](https://www.amazon.co.uk/gp/product/B00AWP9MGG/ref=oh_aui_search_detailpage?ie=UTF8&psc=1)
[https://www.amazon.co.uk/gp/product/B000FVQZ9E/ref=oh_aui_search_detailpage?ie=UTF8&psc=1](https://www.amazon.co.uk/gp/product/B000FVQZ9E/ref=oh_aui_search_detailpage?ie=UTF8&psc=1)

Again, thanks for your time (and no, you don't need to reply to the 2 NIC's I posted).

---

### Post by TheFu on 2016-07-16
I wouldn't buy either.  There is something about Intel PRO/1000 NICs that just makes life easy and systems perform well.  There are lots of different intel GigE models, but basically they all use the e1000 driver under Linux.  For pfsense, HW support is limited, so I wouldn't touch non-Intel NICs.  It just isn't worth the fight to me.  If you do, be certain to check the bsd compatibility AND look for throughput and CPU numbers. They are not all the same.

---

