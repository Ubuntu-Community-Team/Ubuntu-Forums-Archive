---
title: "Ubuntu boots with wrong default gateway device"
date: 2006-08-11
forum: Networking &amp; Wireless
---

### Post by daou on 2006-08-11
I have two network cards, eth0 for internet and eth1 for LAN.
The problem is Ubuntu always loads eth1 as my "Default Gateway Device" and I have to change it to eth0 to access the internet. How can I force Ubuntu to use eth0 instead because simply selecting it in the network configuration dialogue doesn't seem to help?

---

### Post by ciscosurfer on 2006-08-11
There are a few things you can try.  Do a quick search for your problem on the forums and you'll notice many people have your same problem.  One [post in particular]("http://www.ubuntuforums.org/showthread.php?t=233123") (read entire thread) tells you to change some setting in your /etc/network/interfaces file; to switch it from dhcp to static (they are using routers, as I assume you are as well).  Backup your interfaces file first before doing anything so you can revert to it if things go fishy :grin:```
sudo cp -f /etc/network/interfaces /etc/network/interfaces.backup
```Then mess with the file to see if you can get it working the way you want.  Another post suggests simply switching your cables around (eth0 to eth1 and vice versa and reconfiguring)...different approaches are working for different people.

---

### Post by daou on 2006-08-13
Thanks for the links. Unfortunately the solutions didn't work for me. But I was able to get it working by making a startup script file that runs some route commands.
Also, if the gateway field in the properties of the LAN ethernet device is unnecessary, meaning the LAN works without it, then removing it takes it out of the Default Gateway Device dropdown box. So that's a possible solution.

If anyone is interested, here is the shell script:

```
#!/bin/bash

if [ `netstat -nr | grep UG | grep eth0 | wc -c` -lt 1 ] ; then
	`echo "<your-root-passwd>" | sudo -S route add default gw <your-internet-gateway-ip-address>`
else
	echo "Default gateway device already set to eth0"
fi
if [ `netstat -nr | grep UG | grep eth1 | wc -c` -lt 1 ] ; then
	echo "eth1 was not a default gateway device"
else
	`echo "<your-root-passwd>" | sudo -S route del default gw <your-LAN-gateway-ip-address>`
fi
```

The script loads at startup. First it checks if eth0 is set as default gateway device. If not, it runs the "sudo route add" command to set it. Then it checks if eth1 is set as a default gateway device. If it is, the "route del" removes it.
It needs the root password and the gateway ip's and possibly the eth0 and eth1 changed to work. The script is however a security hole because it leaves the root password in plaintext view. Changing the owner to root and revoking read rights from others would hide the root password from others. But unfortunately shell scripts need read rights in order to be executable and I couldn't come up with a better way to automatically load the script without prompting for a root password, short of making a binary file.

---

### Post by AlexMorin on 2007-01-30
> **daou said:**
> ...Also, if the gateway field in the properties of the LAN ethernet device is unnecessary, meaning the LAN works without it, then **removing it takes it out of the Default Gateway Device dropdown box**. So that's a possible solution.
That worked fine for me!
I have a Edubuntu server with two NICs, running LTSP for 25 terminals. The LAN NIC kept popping up in the Default Gateway drop-down menu. So I did away with the DG line in its config, and voilà!
There was no need for it anyway


Thanks!

---

