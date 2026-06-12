---
title: "Ubuntu Server DHCP"
date: 2008-12-30
forum: New to Ubuntu
---

### Post by rbwh_wiki on 2008-12-30
Hi all,

I'm new to the server edition and I'm wondering if it is possible to de-activate the DHCP service when installting the server Edition?

The reason I ask is because, I need to make sure that the server is not going to function as DHCP and start boardcast to the existing network.

This has happened in the past and the IT people in our department got few servers messed up and was down.

Any suggestions is much appreciated

Thanks
Arda

---

### Post by namdung on 2008-12-30
Yes, just don't select DHCP option while installing.
Even if DHCP is installed, u can always choose to stop the DHCP services.

Freedom is what Linux is about.

---

### Post by cariboo on 2008-12-30
Unless you specifically installed the dhcp3-server package, the server doesn't act as a dhcp server. If you did install the dhcp server and want to remove it at the prompt type:

```
sudo apt-get purge dhcp3-server
```

If you want to set a static ip address you may want to remove dhcp3-client too.

Jim

---

### Post by rbwh_wiki on 2008-12-30
Thanks for the quick reply guys!

i have tried to install the CD on a VM machine but when it comes to the software oacge to install, it does not say anything about DHCP installation. does this mean that the DHCP is not going to be installed or DHCP is installed regardless?

If it is installed regardless, would it be a good idea to install it wihtout connecting the LAN cable to the network and then make sure that i remove the installation using the :

```
sudo apt-get purge dhcp3-server
```

Then assign static ip address. Will this be the best way to do it?

****How do I remove the DHCP client?

let me know if I'm missing something.

Thanks again much appreciated

---

### Post by albinootje on 2008-12-30
> **rbwh_wiki said:**
> Hi all,

I'm new to the server edition and I'm wondering if it is possible to de-activate the DHCP service when installting the server Edition?


Has that happened from an Ubuntu machine ?

The last few years that I've installed a dhcp-server on Debian or Ubuntu machines, the dhcp server would always fail to start because it needed a subnet declaration added in the default example /etc/dhcpd.conf

---

### Post by albinootje on 2008-12-30
> **rbwh_wiki said:**
> Thanks for the quick reply guys!

i have tried to install the CD on a VM machine but when it comes to the software oacge to install, it does not say anything about DHCP installation. does this mean that the DHCP is not going to be installed or DHCP is installed regardless?

If it is installed regardless, would it be a good idea to install it wihtout connecting the LAN cable to the network and then make sure that i remove the installation using the :

```
sudo apt-get purge dhcp3-server
```

Then assign static ip address. Will this be the best way to do it?

****How do I remove the DHCP client?

let me know if I'm missing something.

Thanks again much appreciated

VMware... but that's a way to have an annoying DHCP-server running over the LAN. 
I'm serious, I had problems with an ADSL-modem picking up an ip-address from the VMware dhcp-server on a machine in the LAN and bringing the internet-connection down..

Perhaps you're confusing the VMware dhcp-server with the dhcp-server from Ubuntu Server ?

Just for your information.

---

### Post by cariboo on 2008-12-30
To remove the dhcp client use the same basic command:

```
sudo apt-get purge dhcp3-client
```

Then edit /etc/network/interfaces:

```
sudo nano /etc/network/interfaces
```

to look something like this:

```
 cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
    address 192.168.1.200
    netmask 255.255.255.0
    broadcast 192.168.1.255
    gateway	192.168.1.1
```

Once you have fiished editing the file press Ctrl-o to save and Ctrl-x to exit, then restart networking:

```
sudo /etc/init.d networking restart
```

The above is just an example, your ip address and gateway will be different.

Jim

---

### Post by namdung on 2008-12-30
Which Ubuntu version? While installing Ubuntu Server (I've tried in Intrepid) the options to install DHCP server, LAMP, Mail Server, SSH Server etc is given and one has to manually select each one of them to install. The options are not selected by default.

Again u can easily remove DHCP server

```
sudo apt-get remove dhcp3-server
```

A client without a static IP will try to connect to a DHCP server for automatic IP generation. So give all clients a static IP to avoid inconvenience.

---

### Post by albinootje on 2008-12-30
> **rbwh_wiki said:**
>  ****How do I remove the DHCP client?


Removing the dhcp-client is really over the top imho.

If you really want to remove it, do it after your networking on that machine is working.

---

### Post by rbwh_wiki on 2008-12-30
Sorry i might have confused you.

When i meantioned about installating on VMware, it was just for testing purposes at home. I don't have a spare PC to install so i did it on VMware.

The actual installation will be done on a PC (no VMware).

******* Questions *********

1. If I assign static Ip on the newly installed server, will that disable the DHCP service to work? or do I still need to removed the DHCP manually, then assign the static IP.

2. Do I need to unplugged my network cable when installting to prevent the unwanted issue with the existing network because DHCP server is running?

3. If I remove the DHCP client, will the machine be able to connect to the network available?

sorry for the basic questions :redface:

Thank you

---

### Post by albinootje on 2008-12-30
> **rbwh_wiki said:**
> 
1. If I assign static Ip on the newly installed server, will that disable the DHCP service to work? or do I still need to removed the DHCP manually, then assign the static IP.

There's a big difference between the dhcp client software, and the dhcp server software.
The dhcp server software is the one that can cause you trouble over the network. The dhcp client software is never gonna be harmful over the network.
> 
2. Do I need to unplugged my network cable when installting to prevent the unwanted issue with the existing network because DHCP server is running?

Do you need to run a dhcp-server on your server ?
If not, then simpy don't select it during installation.
It will not be installed by default afair.
> 
3. If I remove the DHCP client, will the machine be able to connect to the network available?

Not via dhcp, only if you've edited /etc/network/interfaces for a static ip properly
> 
sorry for the basic questions :redface:

No problem :)

---

### Post by rbwh_wiki on 2008-12-30
I forgot to let you guys know that the server is installed so:

- I can install dekiwiki mindtouch on it
- I will have to setup the Ip to static.

That is all I need for the machine. So, do I still need to have DHCP client on it?

Thanks

---

### Post by albinootje on 2008-12-30
> **rbwh_wiki said:**
> I forgot to let you guys know that the server is installed so:

- I can install dekiwiki mindtouch on it
- I will have to setup the Ip to static.

That is all I need for the machine. So, do I still need to have DHCP client on it?

Thanks
If you've tested the static ip by rebooting it, then you can remove the dhcp client (and server ?) software on it.

---

