---
title: "Networking not working after router reset"
date: 2011-02-17
forum: New to Ubuntu
---

### Post by Gooseheaded on 2011-02-17
Hello everyone.

I have an old desktop that I converted into a LAMP server just a few days ago.
Everything was going just fine: I followed this guide ([http://rickvause.com/2009/11/getting-a-development-webserver-set-up-at-home-with-xubuntu/](http://rickvause.com/2009/11/getting-a-development-webserver-set-up-at-home-with-xubuntu/)) and got everything working properly and well.

Just a couple of hours ago, however, I had to reset my router in order for some re-settings to take place, and now the desktop cannot connect to the internet.

The router shows that the computer is connected (detects the cable connection), and vice-versa: but there is absolutely no networking.  When I go to my router's "management page", and go to "device list", I  see the desktop as "inactive," despite having a LED on the physical  router displaying connection.

Anyhow, when I try to restart networking by using *sudo /etc/init.d/networking restart*, I get the following error message:

* Reconfiguring network interfaces...
/etc/network/interfaces:4: misplaced option
ifdown: coulnd't read interfaces file "/etc/network/interfaces"
/etc/network/interfaces:4: misplaced option
ifup: coulnd't read interfaces file "/etc/network/interfaces"

My /ect/network/interfaces is as follows:

auto lo
iface lo inet loopback
auto eth0
ifate eth0 inet static
address 192.168.1.107
netmask 255.255.255.0
gateway 192.1.168.254

Now, I know that the netmask and gateway are correct because it was functional before the router reset.

Also, */etc/resolv.conf* is completely empty. I have a feeling this has something to do with it.

1) What is the problem?
2) Why/When does this problem happen?
3) How can I fix it?

I've only been messing around with linux/xubuntu for one week, and I'm not, by any means, experienced. I'm JUST NOW starting to get the hang of it, but still... treat me nicely, don't assume that I know much, :)

Thanks for reading! Will reply as soon as possible.

---

### Post by PunkLV on 2011-02-17
> **ifa_t_e** eth0 inet dhcp
This might be the problem.
By the way, why do you assign via dhcp AND a static address without declaring so?
Use either
```
iface eth0 inet dhcp
```
or
```
iface eth0 inet static
address 192.168.1.107
netmask 255.255.255.0
gateway 192.1.168.254
```

And as the last option, I'd suggest checking the IPs router assigns via DHCP. In case by "reset" you mean "Factory Default Reset"

---

### Post by Gooseheaded on 2011-02-17
> **PunkLV said:**
> This might be the problem.
By the way, why do you assign via dhcp AND a static address without declaring so?
Use either
```
iface eth0 inet dhcp
```or
```
iface eth0 inet static
address 192.168.1.107
netmask 255.255.255.0
gateway 192.1.168.254
```And as the last option, I'd suggest checking the IPs router assigns via DHCP. In case by "reset" you mean "Factory Default Reset"


Sorry, I just meant, "Reboot", instead of Factory Reset.

And, wow, that was a silly, silly mistake by me. The website is now working properly, thank you very much!

Another problem shows up, however, when I try to restart networking:

* Reconfiguring network interfaces...
SIOCADDRT: No such process
Failed to bring up eth0.

After Googling a bit, it seems that network *shouldn't* work when I get that problem: but it is working, and I can't restart networking.

Should I be worried about this? Or should I leave the server as it is, since it is working properly?

Thanks a bunch, again! That was a quick and effective reply, :D

---

### Post by PunkLV on 2011-02-17
> address 192.**168**.1.107
netmask 255.255.255.0
gateway 192.**1**.168.254
Change to:
```
address 192.168.1.107
netmask 255.255.255.0
gateway 192.168.1.254
```
Did not notice that at first glance.

---

### Post by Gooseheaded on 2011-02-17
> **PunkLV said:**
> Change to:
```
address 192.168.1.107
netmask 255.255.255.0
gateway 192.168.1.254
```


...is there a "slap self" function I can use?
Or, perhaps, "sudo facepalm" ?

(Thank you. That was very silly, hahahah!)

---

### Post by PunkLV on 2011-02-17
Yea, these things happen. Greatest frustration I've handled was when I had to configure 3 PCs (2 Linux 1 XP) which were connected:

```
----Linux----XP---Printer
  |
Linux
```

---

### Post by Gooseheaded on 2011-02-17
The server responds to ping, and the website works fine;
but when I try to install mumble through *apt-get mumble-server*, I get an error message saying, 

W: Failed to fetch [http://mx.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/binary-i386/Packages.gz](http://mx.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/binary-i386/Packages.gz)  Something wicked happened resolving 'mx.archive.ubuntu.com:http' (-5 - No address associated with hostname)

Google says it's something about my /etc/hosts file.
What should it look like? my hostname is gooseheaded-desktop.

```
127.0.0.1       gooseheaded-desktop     localhost.localdomain   localhost
::1     gooseheaded-desktop     localhost6.localdomain6 localhost6
::1     gooseheaded-desktop     localhost6.localdomain6 localhost6
127.0.1.1       gooseheaded-desktop

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```Thanks, again.

---

### Post by Gooseheaded on 2011-02-17
What can I do to fix this, or work around it? Thanks!

---

### Post by PunkLV on 2011-02-17
I'd suggest following [http://mumble.sourceforge.net/Main_Page](http://mumble.sourceforge.net/Main_Page)

---

### Post by Gooseheaded on 2011-02-18
I can't use apt-get at all. I can't even install updates for the system/programs.

As in, it's not only Mumble.

---

