---
title: "dhcp - static ip help?"
date: 2008-02-01
forum: Networking &amp; Wireless
---

### Post by fondoo on 2008-02-01
hi,

i just installed ubuntu server 7.10 and i'm new to linux. i want to learn not from the gui, but the command line. i'm trying to configure my ubuntu server from a dhcp to a static ip. i've used 

sudo vi /etc/network/interfaces

and edit iface eth0 inet dhcp(static)

i couldnt figure out how to save the file, so i hit ctrl-alt-del

then i went back to the command line

sudo nano /etc/network/interfaces

made the changes dhcpto static and saved the file

then i tried restarting the network services

sudo /etc/init.d/networking restart

and i get 

*Reconfiguring network interfaces...
/etc/network/interfaces:2: misplaced option
ifdown: couldnt read interface file "/etc/network/interfaces"
/etc/network/interfaces:2: misplaced option
ifup: couldnt read interface file "/etc/network/interfaces"

[fail]

i hae a feeling i have duplicate files. can anyone help? thanks in advance.

---

### Post by dannyboy79 on 2008-02-01
what do you mean by a dhcp static ip? are you saying that your router will always hand out a certain ip based on the MAC address of the NIC card in your ubuntu machine? if that's the case than your interfaces file (the line pertaining to dhcp or static) should merely be this

iface eth0 inet dhcp

or if you do want a static ip, then put only static. you can read about it in the man pages. 
man interfaces

---

### Post by dboot on 2008-02-01
If you want to use dhcp, /etc/network/interfaces should look something like:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp
```

If you want to use a static IP, /etc/network/interfaces should look something like:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.0.100
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.1
```

Some quick points when using vi:

vi /etc/network/interfaces -> opens the file
h, j, k, and l -> navigate the file in command mode
i -> go into insert mode (for each key to represent the letter on it instead of a command) when you want to type
make sure the file looks like either of the above
ESC key -> exit insert mode and go back into command mode 
:wq -> write to the file and quit

---

### Post by superbo8218 on 2008-02-01
edit /etc/network/interfaces with pico or nano:

sudo /etc/network/interfaces

it should be somethig like:

auto eth*
iface eth* inet static
address ***.***.***.***
netmask ***.***.***.***

the first line "auto eth*" is for the interface to be started at boot.

you can save the file in pico/nano with Ctrl+O or while exiting with Ctrl+X

you can reboot or restart the network with:

sudo /etc/init.d/networking restart


hope this helps

---

