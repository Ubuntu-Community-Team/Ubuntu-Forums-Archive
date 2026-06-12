---
title: "Setting Up Static IP For My Server"
date: 2014-04-27
forum: Networking &amp; Wireless
---

### Post by Asif_Ahmad on 2014-04-27
Hello,

I'm currently running a fresh install of Ubuntu 14.04 desktop, and trying to set up a static IP.  I've been online watching videos and forums trying to setup a static IP address with no avail.  I have a Belkin router with an IP of: 192.168.2.1 currently.  

My server is hard-wired (ethernet cable) to the router, and has an IP of 192.168.2.7 currently.  I looked at the following document:
[http://www.fileformat.info/tip/linux/dynamic2static.htm](http://www.fileformat.info/tip/linux/dynamic2static.htm)

but am confused what I'm doing incorrectly.  Here are the values I'm trying to input:

/etc/network/interfaces:

address 192.168.2.200     (outside of my min/max IP range in my router)
netmask 255.255.255.0
network 192.168.2.1        (which is the router address)
broadcast 192.168.2.100  (which I read is supposed to be the min IP range)
gateway 192.168.2.1       (also the router address)

Am I doing this incorrectly?  TIA!

--Asif

---

### Post by Iowan on 2014-04-27
Broadcast and network are not essential,  but when presented:
Broadcast is usually the highest address - 192.168.2.255.
Network is the bottom of the [s]range[/s] subnet - 92.168.2.0
Your file should look something like:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.2.200
netmask 255.255.255.0
network 192.168.2.0
broadcast 192.168.2.255
gateway 192.168.2.1
```
Wait... Is the address 192.168.2.200 or 192.168.2.7?

---

### Post by Asif_Ahmad on 2014-04-27
The current "real" IP is 192.168.2.7:
aahmad@ubuntu-desktop:/var/www$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:21:85:93:33:bc  
         ** inet addr:192.168.2.7**  Bcast:192.168.2.255  Mask:255.255.255.0


But I want to set it with a static IP of: 192.168.2.200 (since it needs to be outside the DHCP IP range).

Here is the range:
[IMG]http://img.photobucket.com/albums/v405/A4orce84/LAN___LAN_Settings_zpse9936b66.png[/IMG]


Finally, I tried your recommendations above, and it still did not work unfortunately.

Thanks,
Asif

---

### Post by SeijiSensei on 2014-04-27
> **Asif_Ahmad said:**
> Finally, I tried your recommendations above, and it still did not work unfortunately.

Well, the configuration Iowan gave you is correct, so something else must be awry.

First, let's make sure Linux sees the network card.  What does "lspci | grep -i ethernet" return?  Does it report your adapter like this:
```
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)
```

If the adapter is recognized, restart networking with "sudo service networking restart".  Now enter the command "ifconfig".  What do you see for the eth0 address?

Next see if you can ping your router with "ping 192.168.2.1"?  Does that work?  If so, try pinging Google's DNS server at 8.8.8.8.

---

### Post by chili555 on 2014-04-27
You have a decision to make; since this is a desktop install, you are undoubtedly running Network Manager. You can set the details perfectly well in NM: [http://www.liberiangeek.net/wp-content/uploads/2011/05/1029141aa483_8FD2/natty_windows_static_ip_7_thumb.png](http://www.liberiangeek.net/wp-content/uploads/2011/05/1029141aa483_8FD2/natty_windows_static_ip_7_thumb.png)

The traditional server method is without NM, obviously, since they are headless and therefor run no graphical environment. If you prefer to do that, remove NM altogether and set /etc/network/interfaces something like this:```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.2.200
netmask 255.255.255.0
gateway 192.168.2.1
dns-nameservers 8.8.8.8 192.168.2.1
```Reboot and check:```
ping -c3 192.168.2.1
ping -c3 www.google.com
```

---

### Post by Asif_Ahmad on 2014-04-28
> **SeijiSensei said:**
> Well, the configuration Iowan gave you is correct, so something else must be awry.

First, let's make sure Linux sees the network card.  What does "lspci | grep -i ethernet" return?  Does it report your adapter like this:
```
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)
```

If the adapter is recognized, restart networking with "sudo service networking restart".  Now enter the command "ifconfig".  What do you see for the eth0 address?

Next see if you can ping your router with "ping 192.168.2.1"?  Does that work?  If so, try pinging Google's DNS server at 8.8.8.8.

Here's the output of [COLOR=#000000]lspci | grep -i ethernet:
[/COLOR]
```
aahmad@ubuntu-desktop:~$ lspci | grep -i ethernet00:14.0 Bridge: NVIDIA Corporation MCP51 **Ethernet** Controller (rev a3)
aahmad@ubuntu-desktop:~$ 
```


At this point, my network is essentially down, and I'm no longer connected to anything.  When I try to ping anywhere I get a "Network is unreachable" error message in terminal.

---

### Post by Asif_Ahmad on 2014-04-28
> **chili555 said:**
> You have a decision to make; since this is a desktop install, you are undoubtedly running Network Manager. You can set the details perfectly well in NM: [http://www.liberiangeek.net/wp-content/uploads/2011/05/1029141aa483_8FD2/natty_windows_static_ip_7_thumb.png](http://www.liberiangeek.net/wp-content/uploads/2011/05/1029141aa483_8FD2/natty_windows_static_ip_7_thumb.png)

The traditional server method is without NM, obviously, since they are headless and therefor run no graphical environment. If you prefer to do that, remove NM altogether and set /etc/network/interfaces something like this:```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.2.200
netmask 255.255.255.0
gateway 192.168.2.1
dns-nameservers 8.8.8.8 192.168.2.1
```Reboot and check:```
ping -c3 192.168.2.1
ping -c3 www.google.com
```


So I've attempted to disable NM from the instructions here:
[https://help.ubuntu.com/community/NetworkManager#Disabling_NetworkManager](https://help.ubuntu.com/community/NetworkManager#Disabling_NetworkManager)

After doing so, I still do not appear to have a network unfortunately.  I'm not sure if I need to force something so it reads my network settings from the interface configs?

---

### Post by Iowan on 2014-04-28
Did the machine get the 192.168.2.200 address?
The rest might be the aftermath of going static.
 Please post results of **route -n**

> **chili555 said:**
> ... since this is a desktop install, you are undoubtedly running Network Manager. 
I saw the "server" part, but missed the "14.04 desktop" part...

---

### Post by Asif_Ahmad on 2014-04-28
> **Iowan said:**
> Did the machine get the 192.168.2.200 address?
The rest might be the aftermath of going static.
 Please post results of **route -n**

Kernel IP Routing Table
Destination
Gateway
Genmask
Flags Metric Ref
Use Iface

It appears the server is no longer on the network.

---

### Post by chili555 on 2014-04-28
Do you have an ethernet interface, ideally eth0?```
ifconfig
```Are there any clues here?```
sudo ifdown eth0 && sudo ifup -v eth0
```The -v for verbose flag should produce some output showing what's going on or not behind the scenes.

Do you get the requested address?```
ifconfig
```Can you ping?```
ping -c3 www.google.com
```

---

### Post by Asif_Ahmad on 2014-04-28
Only had time to run ifconfig so far, but there is no eth0 (ethernet interface) presently listed.

---

### Post by chili555 on 2014-04-28
> **Asif_Ahmad said:**
> Only had time to run ifconfig so far, but there is no eth0 (ethernet interface) presently listed.Then your problem is not setting up a static IP; it is getting a driver to associate with your ethernet device. Let's see:```
lspci -nn | grep -i ethernet
uname -r
```

---

### Post by SeijiSensei on 2014-04-28
> **chili555 said:**
> Then your problem is not setting up a static IP; it is getting a driver to associate with your ethernet device. Let's see:```
lspci -nn | grep -i ethernet
uname -r
```

He did the first of those already.
```
aahmad@ubuntu-desktop:~$ lspci | grep -i ethernet
00:14.0 Bridge: NVIDIA Corporation MCP51 Ethernet Controller (rev a3)
```

That should be supported by the "[forcedeth](http://cateee.net/lkddb/web-lkddb/FORCEDETH.html)" module.  It's in the current kernel: /lib/modules/3.13.0-24-generic/kernel/drivers/net/ethernet/nvidia/forcedeth.ko.  Let's see if it's loaded.  OP, what do you see when you run "lsmod | grep forcedeth"?  If that turns up empty, then the driver isn't being loaded for some reason.  Let's give it a try manually first.  What happens if you run
```
sudo modprobe forcedeth
```
That should install the driver.  Check with lsmod then see if you can start the network.  If so, you can tell the computer to load forcedeth at boot by following [these instructions](https://help.ubuntu.com/community/Loadable_Modules).

---

### Post by Asif_Ahmad on 2014-04-28
I'll give it a shot when I get home from work.  Just to note, everything was working previously (when NM was enabled) minus being a static IP.  But I'll give your suggestions a try in a few hours.

Thanks guys! =)

---

### Post by Asif_Ahmad on 2014-05-03
Hello Everyone,

I was finally able to take some time and run your commands [COLOR=#000000][B]SeijiSensei.  
[/B][/COLOR]
I ran the following: lsmod | grep forcedeth
forcedeth   67509    0

Also tried to do the sudo modprobe forcedeth command, and it still appears I don't have an eth0 connection any longer after executing ifconfig.

Any other ideas?

Thanks,
Asif

---

### Post by chili555 on 2014-05-03
After a fresh reboot, what does this tell us?```
dmesg | grep -e forcedeth -e 14.0
```

---

