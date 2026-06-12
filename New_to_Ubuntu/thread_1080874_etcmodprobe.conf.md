---
title: "/etc/modprobe.conf"
date: 2009-02-25
forum: New to Ubuntu
---

### Post by shurkes on 2009-02-25
hello
i am new with linux and in the forum.
recently i bought net book and installed ubuntu.
right now i am not able to connect wireless. the wireless card is from realek. i asked them to send me the driver for this card and they sent it with explainations.
 they wrote that i have to edit "/etc/modprobe.conf" in order to install.
i don't have this file in my machine.
what shall i do?
thanks

---

### Post by unutbu on 2009-02-25
Any file in /etc/modprobe.d will be read and interpreted like /etc/modprobe.conf.
So you could for example create a file in /etc/modprobe.d called realtek and put the commands in there. You will need administrator privileges to create a file in /etc/modprobe.conf. You do this by opening a terminal (Applications>Accessories>Terminal) and typing
```

gksu gedit /etc/modprobe.d/realtek
```

---

### Post by sgosnell on 2009-02-25
Or just type gksudo gedit /etc/modprobe.d/conf.  If the file doesn't exist, it will be created.  /etc/modprobe.conf is not the proper filename.

---

### Post by shurkes on 2009-02-26
[U][B]hi and thanks for the responses.
i'd copied the text file that i received withe the driver package and its below.
when i am checking if the built in driver is installed, i see:" r8169        33156   0"
i think that i have it.
when i try to uninstall, it tells me operation not permitted. i tried to make a modprobe.conf and still can't uninstall.

does anyone can help?[/B][/U]

[LEFT]<Linux device driver for Realtek Ethernet controllers>

	This is the Linux device driver released for RealTek RTL8101E, RTL8102E(L) and RTL8103E(L), the Fast Ethernet controller with PCI-Express interface.

<Requirements>

	- kernel source tree (supported Linux kernel 2.6.x and 2.4.x)
	- For linux kernel 2.4.x, this driver supports linux kernel 2.4.20 and latter.
	- compiler/binutils for kernel compilation

<Quick install with proper kernel settings>
	Check whether the built-in driver, r8169.ko (or r8169.o for kernel 2.4.x), is installed. 
		# lsmod | grep r8169

	If it is installed, please remove it.
		# rmmod r8169
	note: If the built-in driver cannot removed by rmmod, please edit /etc/modprobe.conf and comment 'alias eth0 r8169'. Then, remmove it again or reboot your computer.

	Unpack the tarball :
		# tar vjxf r8101-1.aaa.bb.tar.bz2

	Change to the directory:
		# cd r8101-1.aaa.bb

	If you are running the target kernel, then you should be able to do :

		# make clean modules	(as root or with sudo)
		# make install
		# depmod -a
		# insmod ./src/r8101.ko	(or r8101.o for kernel 2.4.x)

	You can check whether the driver is loaded by using following commands.

		# lsmod | grep r8101
		# ifconfig -a

	If there is a device name, ethX, shown on the monitor, the linux 
	driver is loaded. Then, you can use the following command to activate 
	the ethX.

		# ifconfig ethX

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

		a. Fixed IP address:
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

	   If the user is in the path ~/r8101, the link status can be forced 
	   to one of the 4 modes as following command.

		# insmod ./src/r8101.ko speed=SPEED_MODE duplex=DUPLEX_MODE autoneg=NWAY_OPTION

		,where
			SPEED_MODE	= 100	for 100Mbps
					= 10	for 10Mbps
			DUPLEX_MODE	= 0	for half-duplex
					= 1	for full-duplex
			NWAY_OPTION	= 0	for auto-negotiation off (true force)
					= 1	for auto-negotiation on (nway force)
		For example:

			# insmod ./src/r8101.ko speed=100 duplex=0 autoneg=1

		will force PHY to operate in 100Mpbs Half-duplex(nway force).

	2. Force the link status by using ethtool.
		a. Insert the driver first.
		b. Make sure that ethtool exists in /sbin.
		c. Force the link status as the following command.

			# ethtool -s ethX speed SPEED_MODE duplex DUPLEX_MODE autoneg NWAY_OPTION

			,where
				SPEED_MODE	= 100	for 100Mbps
						= 10	for 10Mbps
				DUPLEX_MODE	= half	for half-duplex
						= full	for full-duplex
				NWAY_OPTION	= off	for auto-negotiation off (true force)
						= on	for auto-negotiation on (nway force)

		For example:
		
			# ethtool -s eth0 speed 100 duplex full autoneg on

		will force PHY to operate in 100Mpbs Full-duplex(nway force).

<Jumbo Frame>
	RTL8101E, RTL8102E and RTL8103E do not support Jumbo Frame.

[/LEFT]

---

### Post by unutbu on 2009-02-26
Often when the computer complains that a command is not permitted, it means you need to prefix the command with sudo (for text-based commands) or gksu (for graphical apps). So try
```

sudo rmmod r8169
```

or ```


sudo modprobe -r r8169
```

In general, try each command without sudo since it is good to use root powers as sparingly as possible. Soon you will learn which commands require sudo.

---

### Post by shurkes on 2009-02-27
thanks
i am getting an empty line, nothing in fact.

---

### Post by unutbu on 2009-02-27
An empty line as response is fine. It means the r8169 module was successfully removed from the kernel. You can continue with the rest of the instructions. :)

---

### Post by shurkes on 2009-02-27
but when i am doing:
lsmod | grep r8169

it tells me aggain:
r8169       33156   0


doesnt it mean that it is still there?

---

### Post by unutbu on 2009-02-27
Hm. In that case, perhaps try blacklisting the module so the kernel does not load it a boot time:
```

gksu gedit /etc/modprobe.d/blacklist
```

Add a line at the bottom which says
```

blacklist r8169
```

Save the file, reboot, and test that r8169 is not loaded:
```

lsmod | grep r8169
```

---

