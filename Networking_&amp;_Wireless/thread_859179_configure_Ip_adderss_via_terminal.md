---
title: "configure Ip adderss via terminal"
date: 2008-07-14
forum: Networking &amp; Wireless
---

### Post by e24ohm on 2008-07-14
Forum,
How do i configure a Static IP address via the terminal?

How do i configure a dynamic IP address via the terminal?

thank you,
E

---

### Post by pytheas22 on 2008-07-14
For static, use ifconfig, e.g.
```

sudo ifconfig eth0 192.168.1.2
```

An addressed assigned like this will only last till you reboot the computer.  If you want to assign the address permanently, you have to edit /etc/network/interfaces.

To get an address dynamically via dhcp:
```

sudo dhclient eth0
```

---

### Post by e24ohm on 2008-07-14
> **pytheas22 said:**
> For static, use ifconfig, e.g.
```

sudo ifconfig eth0 192.168.1.2
```

An addressed assigned like this will only last till you reboot the computer.  If you want to assign the address permanently, you have to edit /etc/network/interfaces.

To get an address dynamically via dhcp:
```

sudo dhclient eth0
```
what does sudo do? I am new to linux, and i'm not sure what sudo does, and would like to know.

Thank you,

---

### Post by z.s.tar.gz on 2008-07-14
'sudo' is similar to running something as administrator in windows.
Exept in linux, it is called running it as *root*

---

### Post by pytheas22 on 2008-07-14
Yes, as z.s. says, sudo just means "run as root" (the root account is what Windows calls the administrator account), so "sudo ifconfig [some arguments...]" means "run ifconfig [arguments] as root."  You have to do this because ordinary users on Ubuntu don't have privileges to modify system settings like IP addresses.

You should know that most Linux distributions don't use sudo, although they still have root accounts and a user-privilege system and all that.  The difference is that in other distributions, in order to run a command as root, you have to "become root" first by using the "su" (super user) command.  So if you wanted to change an IP on Fedora, for example:
```

su
[you get asked for your password and then become root permanently, until you type 'exit']
ifconfig eth0 192.168.1.1
exit
[now you're back to a regular user]
```

This is good to know if you're trying to follow instructions for a different distribution.

On Ubuntu, if you want to become root permanently, type:
```

sudo -s
```

Also, since you're new to Ubuntu, you may want to know that you can configure static IP addresses and all that with a graphical interface by using the utility at System>Administration>Network.  I would have mentioned that before, but I assumed you needed to use the command line for some reason--maybe you just didn't realize that you can do it all through a graphical interface.

---

### Post by Dudewhoa on 2008-07-18
> **e24ohm said:**
> what does sudo do? I am new to linux, and i'm not sure what sudo does, and would like to know.

Thank you,

I think If you log in as the Root user then you won't need SUDO. But Z and Pytheas had explained everything.

I'm a noob too and I was just looking how to configure the IP address in Ubuntu, and I would like to give you guys thanks for this thread.

---

