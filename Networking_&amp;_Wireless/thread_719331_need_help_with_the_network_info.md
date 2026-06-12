---
title: "need help with the network info"
date: 2008-03-09
forum: Networking &amp; Wireless
---

### Post by jwxie on 2008-03-09
hello guys
i am setting up a server edition 6.06 LTS

it's command line interface cuz it's only 128 RAM i believed
and i really want to learn more command line and for server command line interface is much superior than grpahical

here is my problem

i want to make sure to configure the following infor correctly
according to this website
[http://ubuntuserversysadmin.blogspot.com/](http://ubuntuserversysadmin.blogspot.com/)
> # The primary network interface
auto eth0
iface eth0 inet static
address 192.168.0.100
netmask 255.255.255.0
network 192.168.0.0
broadcast 192.168.0.255
gateway 192.168.0.1
# dns-* options are implemented by the resolvconf package, if installed
dns-nameservers 192.168.0.1

how do i check each of them, or identify them using any command that you guys would know?
i am always having trouble with identifying some of them

please tell me the best way to deal with this
i am not dummie but i am willing to learn (i am still a high school kid, really engage in learning them right)

thank you

---

### Post by wormser on 2008-03-09
I am unshure if you need to do that.  You can use DHCP to get your network info assigned to you automatically.  Here are some basic commands for networking.

This will list your network information
```
ifconfig
```

This will assign you an IP address from DHCP
```
dhclient
```

You should learn some [basic commands]("http://www.itd.umich.edu/itcsdocs/r1159/").  

Here is a quick run down of what that guide is saying.

*This command opens the interfaces file to edit in a program called vi.  If I was you, I would use nano instead.  It is easier to use than vi.  So just replace vi with nano in the following command.*

vi /etc/network/interfaces


Now make the file look like this to this press the Insert key to enter edit mode:

*Copy this into the file now.*

> # This file describes the network interfaces available on your system
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
# dns-* options are implemented by the resolvconf package, if installed
dns-nameservers 192.168.0.1

---

### Post by jwxie on 2008-03-09
great help my dear friend, you are nice 
i will take a serious look at the basic command link and the infor you provides to me

oh yes, but soon i will mirgate my server to my school instead at my home
but it's great to learn some more basic commands

thank you

---

