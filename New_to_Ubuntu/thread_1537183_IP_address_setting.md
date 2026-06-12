---
title: "IP address setting"
date: 2010-07-23
forum: New to Ubuntu
---

### Post by fluteofliar on 2010-07-23
Hi,all of you
i am using ubuntu10.04 ultimate edition2.6
i want to change my ip address (idnt know how to check wheather it sstatic or dynamic)
these are the following entires i found in  /etc/network/interfaces
iauto lo
iface lo inet loopback
plz tell me if you can?

---

### Post by Nerflander on 2010-07-23
go in terminal.
typ:

sudo -i
cd /etc/network/
nano interfaces


now you get a interface file displayed and your able to configure
=================================================
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp               <---- add this line for dhcp settings (auto ip) "
=================================================
or for static :
=================================================
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
#iface eth0 inet dhcp             <---- comment that line
 iface eth0 inet static
    address   192.168.xx.xx
    netmask   255.255.255.0
    network   192.168.xx.0
    broadcast 192.168.xx.255
    gateway   192.168.xx.xx
=================================================

hope you get it:)


edit : Dont forget to save the file by pressing ctrl+ O and close the file with ctrl + x
and then when your done use the command:
/etc/init.d/networking restart

---

### Post by Stefanie on 2010-07-23
You can use the network manager, much easier. Right click on the wireless/wired connection icon, edit connections, select the connection and then click edit. You can change the settings under the IPv4 tab, then select manual instead of dhcp. Now you can enter the static IP address, netmask and gateway. I would not touch /etc/network/interfaces .

---

### Post by Rubi1200 on 2010-07-23
> **Nerflander said:**
> go in terminal.
typ:

sudo -i
cd /etc/network/
nano interfaces

Why do you need a root shell for this? In my opinion, it is completely unnecessary.

The same thing could also be accomplished with 

"sudo gedit (or nano) /etc/network/interfaces"

Much easier, much less likely to cause problems by having a root shell open don't you think?

---

