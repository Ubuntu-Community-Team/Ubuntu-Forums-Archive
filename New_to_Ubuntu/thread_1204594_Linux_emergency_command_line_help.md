---
title: "Linux emergency command line help?"
date: 2009-07-04
forum: New to Ubuntu
---

### Post by wyrmtamer on 2009-07-04
i deleted the etc/networks/interfaces on ubuntu 8.04 file by accident and cant log in now. is there some way i can retrive the file in the failsafe terminal? detailed instructions would be nice. thanks

---

### Post by ad_267 on 2009-07-04
I'm not sure if this file is usually different between different computers but mine just looks like this:
```
auto lo
iface lo inet loopback
```

If you boot into recovery mode you can run "nano /etc/network/interfaces" and enter those lines, then use Ctrl+O to save the file.

---

### Post by x33a on 2009-07-04
you could also try running
```
sudo pppoeconf
```

it should create the file for you.

---

### Post by wyrmtamer on 2009-07-05
.

---

### Post by wyrmtamer on 2009-07-05
when i try to save it it says not a directory

---

### Post by ibutho on 2009-07-05
Do you have an Ubuntu live cd (or any other live cd)? If you have, boot the live cd, mount your Ubuntu root partition (the partition where Ubuntu is installed) and then create a new /etc/network/interfaces file. Mine has the following
```

auto lo
iface lo inet loopback

```
You may need to have admin privileges using sudo to create the file if you are using an Ubuntu live cd. For other distros, you may need to switch to root using su.

---

### Post by Sky Pixie on 2009-07-05
> **wyrmtamer said:**
> when i try to save it it says not a directory

When saving the file?  How are you accessing the session?

/etc/networks is a text file in Hardy.  The correct path is /etc/network/interfaces

I have not used a failsafe terminal, but try the following from the failsafe terminal if you have access.

Change to the /etc directory:
```
cd /etc
```

List all files and directories:
```
ls
```

Is the directory "network" listed?  Notice the name is "network" not "networks."

If so, change to the network directory:
```
cd network
```

List all files and directories:
```
ls
```

Is interfaces listed?  If not, create it.

Either way, open a blank interfaces text file using nano while in the /etc/network directory:
```
sudo nano interfaces
```

Enter the following text for DHCP assigned information:
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
Be certain there is a blank line at the bottom of the file.

Save the file with Ctrl X.

Reboot.
```
sudo reboot
```

---

