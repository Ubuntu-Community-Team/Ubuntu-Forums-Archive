---
title: "no internet with new Dual boot setup [/NEWB]"
date: 2008-02-17
forum: Networking &amp; Wireless
---

### Post by bnuk013 on 2008-02-17
After eight years with the old dell I finally kicked it to the curb and built a new system.  pretty standard budget Intel system, I got a one of the lower end core 2 models, with a micro-ATX board.

for a while i have been wanting to make the transition away from the proprietary OSs and programs and this was the perfect chance to get started.

getting the dual boot set up was not bad. I have on 30GB for XP x64, 30GB for ubuntu 7.10 and the balance as a storage drive for media etc. accessable by both OSs.

Here is the problem, Ubuntu does not connect to the internet.  I have a Touchstone cable modem directly connected to the comp via ethernet.  I am using a Realtek onboard LAN card on the Gigabyte MB.  If you dig into gigabytes site it says the LAN card is a Realtek 8111/8169 LAN.  Do I need a driver for the LAN card?  I DLed one but I have ZERO experience with linux so i wasn't able to install it.  i checked and according to ubuntu I don't need any restricted drivers.

I attached a screen shot of the 2 network setup windows.

Let me know if there is some guide for idiots i can look through instead of wasting your time, I just really like the idea of ubuntu and want it to work out.

---

### Post by bnuk013 on 2008-02-18
come on, anyone?

---

### Post by tangibleorange on 2008-02-18
OK could you post the output of the following command:

```
ifconfig
```

and also the contents of your /etc/network/interfaces:

```
sudo gedit /etc/network/interfaces
```

---

### Post by bnuk013 on 2008-02-18
will do.

---

### Post by bnuk013 on 2008-02-18
Ok, I ran the ifconfig command and here is what came back:

> j@TheBox:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1D:7D:A4:BD:AA
          inet6 addr: fe80::21d:7dff:fea4:bdaa/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:4294967284 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 Base address:0x6000
eth0:avah Link encap:Ethernet  HWaddr 00:1D:7D:A4:BD:AA
          inet addr:169.254.9.74  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:17 Base address:0x6000
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1184 (1.1 KB)  TX bytes:1184 (1.1 KB)


and here is the contents of the interface file:

> auto lo
iface lo inet loopback

Thanks

---

### Post by tangibleorange on 2008-02-19
OK so at least Ubuntu can detect the ethernet card. I am now going to propose connecting from the command line. Try the following commands in order:

First, kill NetworkManager:

```
sudo killall NetworkManager
sudo killall NetworkEventsDispatcher
```

Then, configure the interface:

```
sudo ifconfig eth0 down
sudo ifconfig eth0 192.168.1.8 netmask 255.255.255.0 broadcast 192.168.1.255
``` 
replacing 192.168.1 with the subnet of your network (if you're not sure, just leave it as it is).

Now connect to the internet:

```
sudo ifconfig eth0 up
sudo route add default gw 192.168.1.1
```

Hopefully this will enable you to connect. It wil then be reset when you reboot, but we can sort that later!

---

### Post by bnuk013 on 2008-02-20
No dice.  went through those commands and still nothing.  do I need to tell it the same IP address as XP so the modem knows it the same computer or something?

here is what ifconfig brings up now:

```
eth0      Link encap:Ethernet  HWaddr 00:1D:7D:A4:BD:AA  
          inet addr:192.168.1.8  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:7dff:fea4:bdaa/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:4294967247 overruns:0 frame:0
          TX packets:0 errors:0 dropped:33 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:208 errors:0 dropped:0 overruns:0 frame:0
          TX packets:208 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15424 (15.0 KB)  TX bytes:15424 (15.0 KB)
```

---

### Post by spudratic on 2008-02-20
try this it worked for me.boot into windows go to the device manager find the network interface card (nic)right click properties on one of the tabs advanced I think there is an option to keep the card enabled after shut down enable it then reboot into ubuntu .hope this helps

---

### Post by tangibleorange on 2008-02-21
Well I have never seen this before. All the packets are being dropped by the card:

```
RX packets:0 errors:0 dropped:4294967247 overruns:0 frame:0
```

So the card is connected and receiving packets, but just decides not to use them. My only other idea is to try [WICD]("http://wicd.sourceforge.net") network manager. Follow the instructions for installation there. Synaptic will also prompt you to remove network manager.

---

### Post by bnuk013 on 2008-02-21
Damn. I really thought this would be easier than this.  I may try some more stuff and maybe 8.04 when it comes out but I guess I'll be sticking with windows for now.

I tried that WICD but the installer is download based , they have a stand-alone install but it didn't work and the only instructions are for the self downloading version.  (I'm sorry but what the ****.  its a network connection utility, do you think some of the people using it might not have a network connection?!)

and the wake/enabled after shutdown option is already enabled.

---

### Post by tangibleorange on 2008-02-22
> **bnuk013 said:**
> Damn. I really thought this would be easier than this.  I may try some more stuff and maybe 8.04 when it comes out but I guess I'll be sticking with windows for now.

I tried that WICD but the installer is download based , they have a stand-alone install but it didn't work and the only instructions are for the self downloading version.  (I'm sorry but what the ****.  its a network connection utility, do you think some of the people using it might not have a network connection?!)

and the wake/enabled after shutdown option is already enabled.

Did you download the .deb file on another computer and then transfer it to the ubuntu machine? I think that's what you're meant to do, but I only really suggested it as a last resort - I don't think it will work. I'm afraid I'm all out of ideas - my wireless connections have caused me a lot of problems but not my wired ones...

---

### Post by bnuk013 on 2008-02-22
If were to get the drivers and connect to the modem via USB would that have a better chance of working? Is there any reason I shouldn't do this?

---

### Post by tangibleorange on 2008-02-22
Well anything is worth a try! I've had no experience with a USB modem but providing you have the right drivers I see no reason why it wouldn't work...

---

### Post by ahos on 2008-02-22
You must be sure that the IP address of your NIC is in the same LAN address of your modem. Usually the modem work as DHCP server as default setup. If this is the case, your NIC must be set with DHCP Client on. 

In the network settings Connections > Propertiesl, you can see if the NIC is set for DHCP IP or manual IP.

Be sure that the NIC has the correct default gateway. It must be the modem IP address.

AHOS

---

### Post by bnuk013 on 2008-02-23
yeah I've tried putting the exact same addresses that XP uses and it didn't help.  Now just now I tried to access the modem settings through firefix via the IP (works in XP) and I got nothing. So it seems that there is no connection there at all.  I downloaded the drivers for the onboard LAN card but I have no idea how to install it.

So does the pound sign just mean what follows is code?  below is what the readme file says. (its long...)  I have now idea what I am supposed to do with this.
```
<Linux device driver for Realtek Ethernet controllers>

	This is the Linux device driver released for RealTek RTL8168B/8111B 
	and RTL8168C/8111C, Gigabit Ethernet controllers with PCI-Express 
	interface.

<Requirements>

	- Kernel source tree (supported Linux kernel 2.6.x and 2.4.x)
	- For linux kernel 2.4.x, this driver supports 2.4.20 and latter.
	- Compiler/binutils for kernel compilation

<Quick install with proper kernel settings>

	Unpack the tarball :
		# tar vjxf r8168-8.aaa.bb.tar.bz2

	Change to the directory:
		# cd r8168-8.aaa.bb

	If you are running the target kernel, then you should be able to do :

		# make clean modules	(as root or with sudo)
		# make install
		# depmod -a
		# insmod ./src/r8168.ko (or r8168.o in linux kernel 2.4.x)

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



```

---

### Post by tangibleorange on 2008-02-23
> **bnuk013 said:**
> yeah I've tried putting the exact same addresses that XP uses and it didn't help.  Now just now I tried to access the modem settings through firefix via the IP (works in XP) and I got nothing. So it seems that there is no connection there at all.  I downloaded the drivers for the onboard LAN card but I have no idea how to install it.

The file you posted gives you the commands to run to install it. Try them (this assumes you downloaded them to your home directory):

```
tar vjxf r8168-8.aaa.bb.tar.bz2
cd r8168-8.aaa.bb
sudo make clean modules
make install
depmod -a
insmod ./src/r8168.ko
```

This should load the driver's kernel module. You can then try connecting again using the commands I posted earlier for manual configuration.

---

### Post by bnuk013 on 2008-02-23
what is vjxf? do I actually type that or is that a filler for something else?  so I need the expanded folder in the root directory?

---

### Post by tangibleorange on 2008-02-23
No no "vjxf" is just a collection of options which are being applied to the "tar" command, which will unzip the file. I'm not sure what the options mean but I'm pretty sure you could find out easily on the internet...

The file will then be unzipped to the directory in which the tar file was located (I'm assuming desktop)

---

### Post by tr333 on 2008-02-24
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/141343](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/141343) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				If this helps, I managed to get my ethernet working with the r8169 driver by adding the option "pci=nomsi" to the boot options for my system.

---

### Post by bnuk013 on 2008-03-23
tried just about everyhting you guys said and nothing works.  However I just tried the the 8.04 beta LiveCD and it does connect so I guess the problem has been fixed.  woot.

---

