---
title: "slow gigabit transfers via samba"
date: 2007-08-21
forum: Networking &amp; Wireless
---

### Post by legoman666 on 2007-08-21
First off let me state that my transfer speeds on the same computer with win xp are rediculously fast (260mb/s) between 2 gigabit enabled computers.

Now with Ubuntu feisty (which i install like 2 days ago, so I know nothing about linux), I'm getting about 90kb/s, which sometimes spikes to 200kb/s for a second or two. Do the math, my speeds over the network decreased by a factor of ~370. This is unacceptble. 

I still get the same speeds over http (320kb/s or so) in ubuntu.

my network card is a "RTL8111/8168B PCI Express Gigabit" 

with these slow speeds, im not able to stream movies from the other computers on the network (all gigabit, and yes the switch is gigabit obviously) in win xp, im able to stream a  hd-dvd or blu ray or other 20000kbps h264 content perfectly fine over the network. Now it took an hour to copy a gigabyte from a windows share.

any clues? if possible, could you be very specific with suggestions? Complete linux newbie here. So far I am liking it, but this is pathetic.

---

### Post by dmizer on 2007-08-21
what's the output of:
ifconfig

what is your setup?  are you using a 64bit kernel?  have you disabled ipv6?  have you tried any other file transfer protocol other than samba (ftp, nfs, scp)?

---

### Post by legoman666 on 2007-08-21
```
eth0      Link encap:Ethernet  HWaddr 00:50:8D:91:0B:FA  
          inet addr:192.168.1.11  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::250:8dff:fe91:bfa/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:879101 errors:0 dropped:0 overruns:0 frame:0
          TX packets:604891 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1247121387 (1.1 GiB)  TX bytes:49079569 (46.8 MiB)
          Interrupt:19 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:668 (668.0 b)  TX bytes:668 (668.0 b)

```

im using the 32bit kernel. No, I have not disabled ipv6 and do not know how.  And no, I have not tried any other transfer method yet, nor do I know how with linux. Still working on it.

---

### Post by =JoNaZ= on 2007-09-01
i have the exact same problem... bought a new motherboard.. gigabyte p32-ds3 i think its the same lan controller...   solution anyone?

---

### Post by chrisp21 on 2007-09-01
I haven't gotten into the world of gigabit yet, but when building a linux machine I always buy a pci ethernet adapter that I know works well with Linux and turn off the integrated motherboard adapter.  Some drivers just don't get the most of the hardware because the developer doesn't know much about the actual hardware - because there are no specs.  A majority of the integrated adapters tend to be more obscure hardware and don't work as well.  It sounds to me like this is the situation you're running into.

You may be able to find a better driver, but my guess is that you'll need to get a gigabit card that is designed for linux (there are quite a few).  If you're liking Linux (other than this issue) than it's probably worth it.

---

### Post by un_dave on 2007-09-22
I have a similar motherboard, p35-ds3p, and i'm experiencing exactly the same problem. 

I setup samba shares, so other networked windows/linux/xbox boxes could access the media on this machine, but interestingly i get performance issues with all but one. 

Connecting to my debian xbox, and transferring via ssh2, i get speeds of: 
1.3MB/s which is reasonable, yet if i connect via samba, i get only a few kb/s.

None of my other systems have any issues with there samba shares.

Although the chipset supports gigabit ethernet, my switches only support 100mbit.

ifconfig gives:
[FONT="Courier New"]
eth0      Link encap:Ethernet  HWaddr 00:1A:4D:4B:E1:6F  
          inet addr:10.1.1.103  Bcast:10.1.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:4dff:fe4b:e16f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3685 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3461 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3114339 (2.9 MiB)  TX bytes:892359 (871.4 KiB)
          Interrupt:17 Base address:0xe000 
[/FONT]

Anyone have any ideas?

---

### Post by reckless2k2 on 2007-09-22
what are the results when you run the following command

```
sudo ethtool eth0 | grep -i speed
```

it should say

```
Speed: 1000Mb/s
```


????

---

### Post by un_dave on 2007-09-22
```

dave@hades:~$ sudo ethtool eth0 | grep -i speed
Speed: 100Mb/s

```

That makes sense though, because i'm connected to a 100Mb/s switch, so it won't be running at 1000Mb/s.

Another interesting point, I just tried pulling data from a windows xp machine's share, and got a good transfer speed, and writing into a share on the same computer also gives a good speed. 

Does that help things? Or just confuse them?

---

### Post by reckless2k2 on 2007-09-23
> **un_dave said:**
> ```

dave@hades:~$ sudo ethtool eth0 | grep -i speed
Speed: 100Mb/s

```

That makes sense though, because i'm connected to a 100Mb/s switch, so it won't be running at 1000Mb/s.

Another interesting point, I just tried pulling data from a windows xp machine's share, and got a good transfer speed, and writing into a share on the same computer also gives a good speed. 

Does that help things? Or just confuse them?

if you are connected to a 100Mb/s switch then you will not get gigabit speeds. i still think the nic should read gigabit speed though and the transfer would be limited by the switch only.

---

### Post by un_dave on 2007-09-23
I would have thought that the auto sensing on the network connection works out the speed of the line dependent on the speed supported at either end. 

Anyway, regardless of whether  it's my 'nic supported speed' or 'current link speed', we're still seeing stupidly slow speeds. On my 100mbit network, i'm seeing 10s of kbytes a second, no where near the 1 - 5 mbytes per second that i should really be getting. 

I've tested the network using ftp, and ssh, and have no trouble achieving these speeds with those protocols, so i'm stumped as to what could be wrong with samba. 

I've disabled ipv6, and my smb.conf looks like this:

```
# Samba config file created using SWAT
# from 127.0.0.1 (127.0.0.1)
# Date: 2007/09/23 12:18:53

[global]
	workgroup = MSHOME
	server string = %h server (Samba, Ubuntu)
	security = SHARE
	obey pam restrictions = Yes
	passdb backend = tdbsam
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .
	log level = 2                      # Default is 0
	log file = /var/log/samba/log.%m
	read raw = No
	write raw = No
	max xmit = 65535
	deadtime = 15
	socket options = TCP_NODELAY IPTOS_LOWDELAY
	load printers = No
	dns proxy = No
	ldap ssl = no
	panic action = /usr/share/samba/panic-action %d
	invalid users = root
	#oplocks = No

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	browseable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

[downloads]
	comment = deluge downloads
	path = /home/dave/Desktop/downloads
	guest ok = Yes

[drop]
	comment = hade's drop box
	path = /data/drop
	read only = No
	guest ok = Yes
```

---

### Post by un_dave on 2007-09-23
Ok, so some further testing. 

Using Nautilus 2.18.1 in gnome, i open two windows.
one is the drop box on debian xbox (prometheus) 
\\prometheus\drop 

the other is my desktop, ubuntu (hades). 
\\hades\drop

Using these windows i drag and drop a movie file from one window to another. 
prometheus -> hades FAST
hades -> prometheus SLOW

I then transfered the same file using smbclient, the same directions. The results then are:
prometheus -> hades FAST
hades -> prometheus FAST

So how is using smbclient any different to copying in Nautilus? I was expecting the same speed issues?

Keep in mind here that by FAST, i'm talking mb/s, and SLOW, i mean kb/s.

---

### Post by un_dave on 2007-09-24
Ok, so after spending way to much time reading up on this, it seems to be that lots of people are having the same issue, yet there is no firm solution. Lots of people are just resorting to putting in a PCI network card. :(

One useful thread i found was this:
[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/84782](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/84782)

Which suggests installing the drivers from here:
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=5&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=5&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false)

As mentioned, I have a P35-DS3P mb, which has the Realtek 8111B-GR nic.

When i get home tonight, i'll try out installing that driver, and let you all know how I go. 

On a slightly 'noob' side note, i've never done this before, so i'm just going off the readme file in the driver package. Is this the correct way to go about it? Anyone have anything to add to the process?

It goes like this:

> 
<Linux device driver for Realtek Ethernet controllers>

	This is the Linux device driver released for RealTek RTL8168B/8111B 
	and RTL8168C/8111C, Gigabit Ethernet controllers with PCI-Express 
	interface.

<Requirements>

	- kernel source tree (supported Linux kernel 2.6.x)
	- compiler/binutils for kernel compilation

<Quick install with proper kernel settings>

	Unpack the tarball :
		# tar vjxf r8168-8.aaa.bb.tar.bz2

	Change to the directory:
		# cd r8168-8.aaa.bb

	If you are running the target kernel, then you should be able to do :

		# make clean modules	(as root or with sudo)
		# make install
		# depmod -a
		# insmod ./src/r8168.ko

	You can check whether the driver is loaded by using following commands.

		# lsmod | grep r8168
		# ifconfig -a

	If there is a device name, ethX, shown on the monitor, the linux 
	driver is loaded. Then, you can use the following command to activate 
	the ethX.

		# ifconfig ethX up

		,where X=0,1,2,...

<Set the network related information>
	1. Set manually
		a. Set the IP address of your machine.

			# ifconfig ethX "the IP address of your machine" 

		b. Set the IP address of DNS.

		   Insert the following configuration in /etc/resolv.conf.
		
			nameserver "the IP address of DNS"

		c. Set the IP address of gateway.

			# route add default gw "the IP address of gateway"

	2. Set by doing configurations in /etc/sysconfig/network-scripts
	   /ifcfg-ethX for Redhat and Fedora, or /etc/sysconfig/network
	   /ifcfg-ethX for SuSE. There are two examples to set network 
	   configurations.

		a. Fix IP address:
			DEVICE=eth0
			BOOTPROTO=static
			ONBOOT=yes
			TYPE=ethernet
			NETMASK=255.255.255.0
			IPADDR=192.168.1.1
			GATEWAY=192.168.1.254
			BROADCAST=192.168.1.255

		b. DHCP:
			DEVICE=eth0
			BOOTPROTO=dhcp
			ONBOOT=yes	

<Modify the MAC address>
	There are two ways to modify the MAC address of the NIC.
	1. Use ifconfig:

		# ifconfig ethX hw ether YY:YY:YY:YY:YY:YY

	   ,where X is the device number assigned by Linux kernel, and
		  YY:YY:YY:YY:YY:YY is the MAC address assigned by the user.

	2. Use ip:

		# ip link set ethX address YY:YY:YY:YY:YY:YY

	   ,where X is the device number assigned by Linux kernel, and
		  YY:YY:YY:YY:YY:YY is the MAC address assigned by the user.

<Force Link Status>

	1. Force the link status when insert the driver.

	   If the user is in the path ~/r8168, the link status can be forced 
	   to one of the 5 modes as following command.

		# insmod ./src/r8168.ko speed=SPEED_MODE duplex=DUPLEX_MODE autoneg=NWAY_OPTION

		,where
			SPEED_MODE	= 1000	for 1000Mbps
					= 100	for 100Mbps
					= 10	for 10Mbps
			DUPLEX_MODE	= 0	for half-duplex
					= 1	for full-duplex
			NWAY_OPTION	= 0	for auto-negotiation off (true force)
					= 1	for auto-negotiation on (nway force)
		For example:

			# insmod ./src/r8168.ko speed=100 duplex=0 autoneg=1

		will force PHY to operate in 100Mpbs Half-duplex(nway force).

	2. Force the link status by using ethtool.
		a. Insert the driver first.
		b. Make sure that ethtool exists in /sbin.
		c. Force the link status as the following command.

			# ethtool -s ethX speed SPEED_MODE duplex DUPLEX_MODE autoneg NWAY_OPTION

			,where
				SPEED_MODE	= 1000	for 1000Mbps
						= 100	for 100Mbps
						= 10	for 10Mbps
				DUPLEX_MODE	= half	for half-duplex
						= full	for full-duplex
				NWAY_OPTION	= off	for auto-negotiation off (true force)
						= on	for auto-negotiation on (nway force)

		For example:
		
			# ethtool -s eth0 speed 100 duplex full autoneg on

		will force PHY to operate in 100Mpbs Full-duplex(nway force).


Cheers!

---

### Post by netztier on 2007-09-24
> **legoman666 said:**
> First off let me state that my transfer speeds on the same computer with win xp are rediculously fast (260mb/s) between 2 gigabit enabled computers.

my network card is a "RTL8111/8168B PCI Express Gigabit" 


Possibly one more victim of this issue here: [http://ubuntuforums.org/showthread.php?t=550804](http://ubuntuforums.org/showthread.php?t=550804)
[COLOR="Gray"][SIZE="1"]To me personally, this adds one more shovel of dirt to the increasingly large heap in front of which a sign says: don't buy Realtek. Yes I know - sometimes you just don't have a choice.[/SIZE][/COLOR]

Now.. before plunging into the depths of Samba debugging with buffer sizes and TCP_NODELAY and all the likes, always measure **raw TCP throughput** with **iPerf**. It's in the universe repositories and available for different platforms (Win32 included) here: [http://dast.nlanr.net/Projects/Iperf/](http://dast.nlanr.net/Projects/Iperf/)

Be sure to swap roles of "server" (the iPerf instance that *receives* the traffic) and "client" (the instance of iPerf that *sends* the traffic) for each client/server pair you test on.

You should reach figures like ~95Mbit/s on 100Mbps Full Duplex,  ~22Mbps on 54Mbps WLAN, and 300Mbps or better on Gigabit. If you play with the **-w <window size>** and the **-P <no of parallel threads>** command line parameters, you may even be able to actually touch the 1000Mbit/s barrier - given the end systems are up to it.

It it performs well, you know that you don't have any duplex or link speed issues - and you can start debugging the upper layers and protocols, such as HTTP, NFS or CIFS (Samba). If it doesn't, the problem has to be at the lower layers - then it's time to dig into Ethernet parameters, link speed autosensing, duplex autonegotiation, ethernet flow control (aka "pause frames") choice of NIC driver,  etc.

best regards

Marc


Just for the sake of comparison: my old P-III 500MHz running Ubuntu 7.04 (with an Intel NIC in a 32bit PCI slot) fileserver does 600-700Mbps with iPerf. It is able to jump the 50MByte/s barrier when serving from cache via NFS. Samba however trundles along at 15MByte/s reads and 16MByte/s writes.

---

### Post by un_dave on 2007-09-26
Ok, it looks like my problem is solved!

I installed the new driver from [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=5&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=5&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false)

Followed the readme instructions to build and install.

Unfortunately now i had two drivers installed, and it will always defaulted to the old, buggy one. r8169.

To tell the new driver to load first, 
Edit /etc/initramfs-tools/modules and add two lines:
r8168
r8169

Then run:
sudo update-initramfs -u

And now when you reboot, your network adapter should now be using the r8168 driver. 

You could of course, blacklist the r8169 module, but no amount of my coaxing could get this to work, and i had to resort to the above. 

Speed issues now seem to be completely sorted. 

:)

---

### Post by kelvinchow on 2007-09-29
> **legoman666 said:**
> ```
eth0      Link encap:Ethernet  HWaddr 00:50:8D:91:0B:FA  
          inet addr:192.168.1.11  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::250:8dff:fe91:bfa/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:879101 errors:0 dropped:0 overruns:0 frame:0
          TX packets:604891 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1247121387 (1.1 GiB)  TX bytes:49079569 (46.8 MiB)
          Interrupt:19 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:668 (668.0 b)  TX bytes:668 (668.0 b)

```

im using the 32bit kernel. No, I have not disabled ipv6 and do not know how.  And no, I have not tried any other transfer method yet, nor do I know how with linux. Still working on it.

Your MTU of eth0 is 1500 only , adjust MTU up to 9000 , that will be fine

---

### Post by netztier on 2007-09-29
> **kelvinchow said:**
> Your MTU of eth0 is 1500 only , adjust MTU up to 9000 , that will be fine

This is only advisable if all NICs participating in that nework support Jumbo Frames and also the (wired) switch does. All systems on that subnet should be running the PathMTU Discovery feature, and the router giving access to the Internet from such an MTU 9000 enabled network must be able to respond with an ICMP message type 3 code 4 ("Fragmentation needed, but DF bit set") .

Combining MTU 9000 with a LAN that has a MTU 1500 wireless segment bridged to it (as it commonly happens with broadband wireless routers) will lead to connectivity problems.

Be wary with fiddling with the MTU... 

best regards 

Marc

---

### Post by njparton on 2007-10-29
How do you "fiddle with the MTU"? 

I have 3 gigabit enabled PC's, 2 are running jumbo frames (9014) and I'm trying to set this up on my ubuntu PC but I can't find out how?

I'd like to test this if possible :)

---

### Post by netztier on 2007-10-29
> **njparton said:**
> How do you "fiddle with the MTU"? 

I have 3 gigabit enabled PC's, 2 are running jumbo frames (9014) and I'm trying to set this up on my ubuntu PC but I can't find out how?

I'd like to test this if possible :)

```
iface eth0 inet static
 address <ip>
 netmask <netmask>
 gateway <gateway>
** mtu 1500**
auto eth0

```

Just set **mtu 9000** there. I suggest using 9000 - this will be the maximum size for an IP packet tat'll be packed into a 9014byte ethernet frame (9018bytes if it's a 802.1q trunk). 

To work properly, the ethernet chipset on your NIC and also the ASICs in your gigabit switch have to support Jumbo Frames. Some switches do by default, others only after activating it via the (probably web based) management interface. A normal store-and-forward (cut-through versions have become rare) switch must calculate each packet's CRC32 checksum before forwarding it to the destination port. It needs to be cofigured to also do this for a >9000 byte frame. Else it might discard the frame as "oversized".

best regards

Marc

---

### Post by njparton on 2007-10-30
Great, thanks.

I have a netgear GS105 prosafe switch that supports jumbo frames.  It works very well between windows transfers. Samba transfers are currently 70-80% as quick. Hopefully this will help.

I'm not sure my onboard NIC supports jumbo frames, but the Intel Pro/1000 PT that I have on order does :)

---

### Post by ed_209a on 2007-11-03
> **un_dave said:**
> Ok, it looks like my problem is solved!

I installed the new driver from [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=5&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=5&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false)

Followed the readme instructions to build and install.


I am having a similar problem with a Gigabyte GA-P35 MB. 

I see several files available, which one do I need? I am running 7.10. I am guessing I don't need the Slackware, BSD, SCO or Solaris files. One is named Packet driver. Is that what I need?

---

### Post by un_dave on 2007-11-06
I'm pretty sure the one I used was:
"Linux driver for kernel 2.6.x (Support x86 and x64)"

I've upgraded now to 7.10 too, and it still seems to be working fine. Although, after the update, it'd dumped the module/driver, and I had to reinstall it. 

Let me know how you go.

---

