---
title: "DHCP broken 18.04.  Static IP just fine.  Just can't get DHCP as a client."
date: 2020-10-19
forum: Networking &amp; Wireless
---

### Post by jimmys1 on 2020-10-19
Pretty much the title says it all. 

1. If I try to connect to my router with DHCP, it won't work.  This is true for both Ether cable OR Wifi.
2. My router works fine.  All other devices I own works fine with the router for DHCP. 
3. My laptop (where the problem is) the adapter/wifi works fine **IF** I boot from a memory chip (clean OS).  It's just in 18.04
4. At one time the DHCP worked in this 18.04 install, but I did "something" along the way and now it doesn't. 
5. Setting any connection on Static works just fine. 
6. I can't get on (of course) at any public hotspot.

I'm not a newbie or an expert.   Just experienced.   It's a weird problem.   Need help.  It's very annoying.  :P
Any pointers?

---

### Post by CelticWarrior on 2020-10-20
Welcome.

Please describe that "something".

---

### Post by HermanAB on 2020-10-20
Check the network routing with *tcpdump *in one terminal:
[I]$ sudo apt install tcpdump
$ sudo tcpdump -nlX host ip.address.of.router  and port 67[/I]

Then run *dhclient *from another terminal window:
[I]$ ip link show
$ dhclient nameofethernetdevice[/I]

Look at the error messages and google them for enlightenment.

---

### Post by Tadaen_Sylvermane on 2020-10-20
Did you do your static ip with netplan or the gui? The proper netplan for a desktop to use the gui is critical.

```
cat /etc/netplan/01-netcfg.yaml
network:
 version: 2
 renderer: NetworkManager
```

That file could be named whatever you named it.

If it looks like this then you are getting your dhcp, just don't know it because it isn't reporting to the gui. Replace interface name with yours of course.

```
network:
 version: 2
 renderer: networkd
 ethernets:
  enp?s0:
   dhcp4: true
```

---

### Post by jimmys1 on 2020-10-20
> **Tadaen_Sylvermane said:**
> Did you do your static ip with netplan or the gui? The proper netplan for a desktop to use the gui is critical.

```
cat /etc/netplan/01-netcfg.yaml
network:
 version: 2
 renderer: NetworkManager
```

That file could be named whatever you named it.

If it looks like this then you are getting your dhcp, just don't know it because it isn't reporting to the gui. Replace interface name with yours of course.

```
network:
 version: 2
 renderer: networkd
 ethernets:
  enp?s0:
   dhcp4: true
```


Okay I'm pasting the output of /etc/netplan/01-network-manager-all.yaml

```


# Let NetworkManager manage all devices on this system
network:
  version: 2
  renderer: NetworkManager

```

It looks like your first chunk of code.  So you think I should backup that file and replace the text with the second block of code? 

I'm very very confused on this one.  It's had me scratching my head for months.   I've only gone through the gui to set things up.  It just stopped getting DHCP addresses. ??  I'm on the static ip setting right now.  Works fine on static.

Also I'm going to paste my /etc/network/interfaces file

```

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

```

---

### Post by Tadaen_Sylvermane on 2020-10-20
/etc/network/interfaces shouldn't be needed. Netplan doesn't use it. Maybe check for single space indentation on your netplan file. Yaml is insistent on indentation with spaces.

---

### Post by jimmys1 on 2020-10-20
Okay thanks for the info on /etc/network/interfaces

Okay the yaml is now single spaced.   Still not working for dhcp.   Strange!

This is so odd.  Everything except this 18.04 is working with it. :P

---

### Post by jimmys1 on 2020-10-21
Is there anything else that could cause DHCP not to work?  My *.yaml file seems to be good.

---

### Post by HermanAB on 2020-10-22
Well, the Windows way of poking around in the dark until you trip over something, doesn't work well in Linux.  It is better to run a test and look at the error messages.

First, see what is the name of your ethernet device:
*$ sudo ip link show*

Then ask nicely for a DHCP address and see what happens:
*$ sudo dhclient ipdevicename*

Alternatively, if you are very lazy, simply run *dhclient *with *no *device names and then it will try all of them:
*$ sudo dhclient*

Read the the error messages and google them.

---

### Post by webaake on 2020-10-22
I do 18.04 too and I've come across some problems with DHCP and networking in general. The problems depends on the mix in 18.04 of old and new routines for networking.

1. Originally 18.04 didn't use Netplan.
2. Originally 18.04 didn't use systemd for DHCP.

You don't need Netplan for networking. /etc/network/interfaces can work just fine, or even better.
And systemd's DHCP slowed my name searches way down, so I ditched it.

To disable Netplan go to Step 5 here: [https://www.civo.com/learn/remove-netplan-from-ubuntu-bionic-beaver-18-04](https://www.civo.com/learn/remove-netplan-from-ubuntu-bionic-beaver-18-04)

To disable systemd's DHCP service [https://www.naut.ca/blog/2018/12/12/disabling-systemd-networking/](https://www.naut.ca/blog/2018/12/12/disabling-systemd-networking/)

---

### Post by slickymaster on 2020-10-22
*Thread moved to **Networking & Wireless**.*

---

