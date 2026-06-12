---
title: "[SOLVED] Wired Static IP Troubles"
date: 2008-07-17
forum: Networking &amp; Wireless
---

### Post by Bionic Apple on 2008-07-17
I prefer to have a static ip for numerous programs that require port forwarding, plus I like to keep my network unscrambled with many dynamic IPs.  Ubuntu is dynamic by default.  "No big deal", I thought.  I go to the network settings GUI tool and put in my static IP settings.  I did a quick test (Firefox) and it utterly failed.  So, I thought that perhaps the program was buggy.  I googled the problem and came to a few ways to edit *etc/network/interfaces* to get it to work.  I tried each way, but none worked.  Actually, I lied, as one way worked, but it made the Gnome Settings daemon go crazy and make my login a 4 minute ordeal.

Please, can someone help?!

---

### Post by cmb11 on 2008-07-17
My way to get around problems related to network interfaces is by installing a network manager called: "WICD", it works flawlessly and supports all kinds of networks...

---

### Post by Iowan on 2008-07-17
Post your **/etc/network/interfaces** file. Although not necessary when listing a file to copy/paste, I like **nano** as editor - the help screen across the bottom aids my failing memory.```
 sudo nano /etc/network/interfaces
```

---

### Post by Bionic Apple on 2008-07-17
```
auto lo
iface lo inet loopback

```

Just for reference, here are the ones that don't work:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.1.107
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1
```


      ```
### Edit /etc/network/interfaces (in this example setup I will use the IP address 192.168.178.50 for eth0):
       
       
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).
       
 # The loopback network interface
      auto lo
      iface lo inet loopback
       
# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
      mapping hotplug
      script grep
      map eth0

       

# The primary network interface
      auto eth0
      iface eth0 inet static
      address 192.168.1.107
      netmask 255.255.255.0
      network 192.168.1.0
      broadcast 192.168.1.255
      gateway 192.168.1.1

#optional
#dns-nameserver 102.168.178.1

### You can also edit /etc/resolv.conf to configure a dns-server to use:
      nameserver 192.168.178.1
```


Then, here's the one that messes with the Gnome Settings Daemon, but works:

```
auto eth0
iface eth0 inet static
address 192.168.1.107
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
```

---

### Post by Bionic Apple on 2008-07-18
Bump.

---

### Post by Bionic Apple on 2008-07-18
BUMP.  Also, please help me because I am trying to set up a webserver and would like to test it on LAN, but can't because I don't know what local IP it is on all the time.

---

