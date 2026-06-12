---
title: "I need to activatemy eth0"
date: 2005-11-09
forum: Networking &amp; Wireless
---

### Post by pminetti on 2005-11-09
Hi
every time I shutdown my computer my eth0 goes deactivate
so when I restart I have no conection, I need to activate and then make "pon".
Please how can I solve this problem?

---

### Post by varunus on 2005-11-09
How did you set up your eth0? Did you use a terminal?

I think if you set it up in System->Administration->Networking it should come up every time you boot.  I did this with my atheros wireless card.

Make sure you're not skipping the "configuring network interfaces" step in bootup, this is the one that brings up network connections.

If you used the control panel to do it, what settings did you use?

---

### Post by pminetti on 2005-11-09
let me explain
when I boot my computer, always stop for a seconds when it is in network configuration, because my computer it's no in a network, I dicided to deactivete eth0. Next time I reboot it didn't stop on network configuration like I want, but... no more conection to internet, even my apache not work (127.0.0.1 it's not working) so I go to System->Administration->Networking and say activate eth0, but now every time I need to say activate to eth0
More extrage is that now take moretime to came up the network windows.
It's no much what I can configure, only say to use DHCP

is there a comand line to configure my eth0?
thanks

---

### Post by pminetti on 2005-11-09
well i find that if i do ifconfig lo up then mi loopback works, apache too
i think that i have broke some network configuartion file, but I don't know where it is.

---

### Post by varunus on 2005-11-10
The file that does the network configuration in boot is "/etc/init.d/networking".  It just runs the ifconfig up things, and uses the data in /etc/network/interfaces to do this.  Did you edit either of these files?  What is the content of /etc/network/interfaces?  Do you not see the "configuring network interfaces" now when you boot anymore?

---

### Post by pminetti on 2005-11-10
Hi varunus
this is the content  of /etc/network/interfaces

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

iface eth0 inet dhcp
name Tarjeta de red Ethernet





auto dsl-provider
iface dsl-provider inet ppp
provider dsl-provider

# added by pppoeconf
auto eth0

    pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf


And thas all
yes  I saw the configuring network interfaces, but before all this problem it take's some second in this part of the boot, and now inmidiatly say [ ok ],  because no configuration of the eth0,lo, and pppoe
thanks for your coperation

---

### Post by pminetti on 2005-11-10
JEJE!! Thanks Varunus
after I post you my  /etc/network/interfaces i said "hey something is wrong here"
now all it's OK
thank, because I don't know where is the right file to look for until you said

thanks

---

### Post by varunus on 2005-11-11
Glad you got it working.  Usually, manually editing that file shouldn't be necessary...ah well, glad it works.  :)

---

