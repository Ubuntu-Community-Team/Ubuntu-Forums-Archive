---
title: "Share files via ethernet Ubuntu &amp; XP"
date: 2009-07-11
forum: New to Ubuntu
---

### Post by kamitsukai on 2009-07-11
How do I setup file sharing between Ubuntu and XP? via Ethernet

---

### Post by d_liebscher on 2009-07-11
Hi,

to access a Windows sharing, you need the package libsmbclient, which should be installed by standard installation. Then you  just have to go to smb://name-of-windows-computer (for example with nautilus). 

To share files for Windows you have to set up a Samba Server. 
You'll find a nice guidance here: [https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba) so I needn't write all these things here again.

Daniel

---

### Post by kamitsukai on 2009-07-11
> **d_liebscher said:**
> Hi,

to access a Windows sharing, you need the package libsmbclient, which should be installed by standard installation. Then you  just have to go to smb://name-of-windows-computer (for example with nautilus). 

To share files for Windows you have to set up a Samba Server. 
You'll find a nice guidance here: [https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba) so I needn't write all these things here again.

Daniel

well when i connect both via the ethernet cable it says that they cannot connect so surely they have to connect before I can do the above???

---

### Post by d_liebscher on 2009-07-11
Hi,

if i understood correctly, you connected both pc's direct, without any switch or an router:

**_just in this case:_**
the can't connect, because they have no IP Address and you must set the address manually

Win: hm, depend on version: normally right click on Network -> Properties -> right click on lan adapter properties -> TCP/IP v4 -> Properties ->
IP Address: 192.168.1.1
Subnetmask: 255.255.255.0
--> OK

Linux: (somewhere  there is a grafical tool to edit IP Address)
change ip to IP Address: 192.168.1.2
 
backup config:
```
sudo cp /etc/network/interfaces /etc/network/interfaces.bak
```edit config:
```
edit /etc/network/interfaces
```there is a line for yout Networkcard which look like:

```
iface eth0 inet dhcp
```you change into:

```
iface eth0 inet static
        address 192.168.1.2
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
```restart networkconfiguration:

```
sudo /etc/init.d/network restart
```if you want to connect to an router (connect to internet via router) which have a DHCP in it (which is the nomal case): you have to turn back the configuration

win: 
selcet automatic IP and automatic DHCP
linux: 
```
sudo cp /etc/network/interfaces.bak /etc/network/interfaces
sudo /etc/init.d/network restart
```(it could be useful to backup the static configuration for later)



Daniel


PS: 

if I misunderstood you, please describe what you mean with
 > so surely they have to connect before I can do the above because my English is not as good as it should be, sorry

---

### Post by nhasian on 2009-07-11
if you are connecting both computers directly without a switch or hub, then you need a special cable called a crossover cable.  If both pcs are connecting to a switch/hub then you can just use plain ethernet cables.

once both pcs are connected to the same network, ubuntu will be able to see the xp shares automatically from places->network in your menu.
to share a folder in ubuntu just right click on it and select sharing.

---

### Post by d_liebscher on 2009-07-11
ok, it seems I give myself a hard time :roll:
well, I think I spend to much time with server consoles^^

---

### Post by LewRockwell on 2009-07-11
> **d_liebscher said:**
> ok, it seems I give myself a hard time :roll:
well, I think I spend to much time with server consoles^^

I think you did a fine job

.

---

### Post by d_liebscher on 2009-07-11
Thanks.

---

### Post by thedalmeny on 2009-07-14
Whats your MSN kamit? Need a word with ya

Add me if ya can - [email]andrewdalmeny@hotmail.com[/email]

---

### Post by d_liebscher on 2009-07-14
Sorry, i don't use msn, just Jabber, ICQ and Skype. I'll send you my contact data via Message.

Daniel

---

