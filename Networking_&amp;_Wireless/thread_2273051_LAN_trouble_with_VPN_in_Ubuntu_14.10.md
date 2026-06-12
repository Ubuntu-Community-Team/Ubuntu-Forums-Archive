---
title: "LAN trouble with VPN in Ubuntu 14.10"
date: 2015-04-10
forum: Networking &amp; Wireless
---

### Post by tapasray on 2015-04-10
Wanting to route my internet traffic through VPN, I had installed gAdmin OpenVPN server and client, and a VPN access manager. As I was unable to configure them, I uninstalled all three. Since then none of the LANs for which the computer is configured, shows up when the Ethernet cable is plugged in. 

I would really appreciate help with restoring the LAN connections. Thanks in advance.

---

### Post by michi1983 on 2015-04-10
What does your ```
sudo ifconfig
``` say?

---

### Post by tapasray on 2015-04-10
Thanks a lot, @michi1983. Sorry, I was commuting.

br0       Link encap:Ethernet  HWaddr 54:42:49:ff:91:f9  
          inet addr:192.168.1.10  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::5642:49ff:feff:91f9/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:9795 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1564203 (1.5 MB)  TX bytes:1637 (1.6 KB)

eth0      Link encap:Ethernet  HWaddr 54:42:49:ff:91:f9  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:9799 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:1701789 (1.7 MB)  TX bytes:491 (491.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:10013 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10013 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1260365 (1.2 MB)  TX bytes:1260365 (1.2 MB)

wlan0     Link encap:Ethernet  HWaddr 64:27:37:b1:15:9e  
          inet addr:192.168.0.134  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::6627:37ff:feb1:159e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:70313 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26650 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:36683454 (36.6 MB)  TX bytes:3928638 (3.9 MB)

---

### Post by michi1983 on 2015-04-10
alright, it seems you have a working wifi connection.
so to get rid of the bridge br0 which seems to get installed after one of your vpn steps type this into your terminal
 ```

ip link set br0 down
brctl delbr br0

```
one line after the other.

now please post the output of 
```
cat /etc/network/interfaces
```

---

### Post by tapasray on 2015-04-10
@michi1983 -- br0 could not be deleted. Here's the output (tried twice) -- 

~$ ip link set br0 down
RTNETLINK answers: Operation not permitted
~$ brctl delbr br0
can't delete bridge br0: Operation not permitted
~$ ip link set br0 down
RTNETLINK answers: Operation not permitted
~$ brctl delbr br0
can't delete bridge br0: Operation not permitted

---

### Post by michi1983 on 2015-04-11
try the commands with sudo at front

---

### Post by tapasray on 2015-04-11
Thanks. This is what I have got so far --

:~$ sudo ip link set br0 down
[sudo] password for tapas: 
:~$ sudo ip link set br0 down
:~$ brctl delbr br0
can't delete bridge br0: Operation not permitted
:~$ ip link set br0 down
RTNETLINK answers: Operation not permitted
:~$ sudo brctl delbr br0
:~$ sudo ip link set br0 down
Cannot find device "br0"
:~$ cat /etc/network/interfaces
auto lo br0
iface lo inet loopback

iface br0 inet static
 address 192.168.1.10
 netmask 255.255.255.0
 gateway 192.168.1.1
 bridge_ports eth0

iface eth0 inet manual
 up ip link set $IFACE up promisc on
 down ip link set $IFACE down promisc off

---

### Post by michi1983 on 2015-04-12
Alright, first of all, please type this in your terminal:


```
[COLOR=#333333][FONT=Menlo]sudo apt-get purge --auto-remove gadmin-openvpn-client[/FONT][/COLOR]
``` and
```
[COLOR=#333333][FONT=Menlo]sudo apt-get purge --auto-remove gadmin-openvpn-server[/FONT][/COLOR]
```

then edit your /etc/network/interfaces file and change all the code in there to the following:

```

auto lo
iface lo inet loopback


auto eth0
iface eth0 inet dhcp

```

After that restart your network service with 
```
sudo /etc/init.d/networking restart

```

And then please post again the output of 
```
sudo ifconfig
```

If the br0 interface is still there, something (one of the software you used for the vpn) creates the bridge interface automatically.

---

### Post by tapasray on 2015-04-13
Thanks a lot, @michi1983. Coming back soon with the outputs.

Thanks a lot, @michi1983. Coming back soon with the outputs ...

tapas@tapas-VPCYB35AN:~$ sudo /etc/init.d/networking restart
[sudo] password for tapas: 
stop: Job failed while stopping
start: Job is already running: networking
tapas@tapas-VPCYB35AN:~$ sudo /etc/init.d/networking restart
stop: Job failed while stopping
start: Job is already running: networking
tapas@tapas-VPCYB35AN:~$ sudo ifconfig
br0       Link encap:Ethernet  HWaddr 54:42:49:ff:91:f9  
          inet addr:192.168.1.10  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::5642:49ff:feff:91f9/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:1507 (1.5 KB)

eth0      Link encap:Ethernet  HWaddr 54:42:49:ff:91:f9  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1975 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1975 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:213179 (213.1 KB)  TX bytes:213179 (213.1 KB)

wlan0     Link encap:Ethernet  HWaddr 64:27:37:b1:15:9e  
          inet addr:192.168.223.107  Bcast:192.168.223.255  Mask:255.255.255.0
          inet6 addr: fe80::6627:37ff:feb1:159e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:50 errors:0 dropped:0 overruns:0 frame:0
          TX packets:135 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11513 (11.5 KB)  TX bytes:28183 (28.1 KB)

---

### Post by michi1983 on 2015-04-13
What did the ```
sudo apt-get remove
``` commands return? did it uninstall further software of your vpn stuff?

Please try a ```
sudo ifdown br0 && sudo ifdown eth0 && sudo ifup eth0
```

---

### Post by tapasray on 2015-04-14
Hi! Sorry, I had missed the second page, in which your post appears. Here's the full output. 

tapas@tapas-VPCYB35AN:~$ sudo apt-get purge --auto-remove gadmin-openvpn-client
[sudo] password for tapas:
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
gadmin-openvpn-client* libosmesa6* linux-headers-3.16.0-29*
linux-headers-3.16.0-29-generic* linux-image-3.16.0-29-generic*
linux-image-extra-3.16.0-29-generic* python-pexpect* wine-gecko2.21*
wine-mono0.0.8*
0 upgraded, 0 newly installed, 9 to remove and 10 not upgraded.
After this operation, 303 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 358754 files and directories currently installed.)
Removing gadmin-openvpn-client (0.1.2-4) ...
Purging configuration files for gadmin-openvpn-client (0.1.2-4) ...
Removing libosmesa6:i386 (10.3.2-0ubuntu0.1) ...
Purging configuration files for libosmesa6:i386 (10.3.2-0ubuntu0.1) ...
Removing linux-headers-3.16.0-29-generic (3.16.0-29.39) ...
Removing linux-headers-3.16.0-29 (3.16.0-29.39) ...
Removing linux-image-extra-3.16.0-29-generic (3.16.0-29.39) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.16.0-29-generic /boot/vmlinuz-
3.16.0-29-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.16.0-29-generic /boot/vmlinuz-3.16.0-
29-generic
update-initramfs: Generating /boot/initrd.img-3.16.0-29-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.16.0-29-generic /boot/vmlinuz-3.16.0-29-
generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.16.0-29-generic /boot/vmlinuz-3.16.0-
29-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.16.0-29-generic /boot/vmlinuz-3.16.0-
29-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.16.0-34-generic
Found initrd image: /boot/initrd.img-3.16.0-34-generic
Found linux image: /boot/vmlinuz-3.16.0-33-generic
Found initrd image: /boot/initrd.img-3.16.0-33-generic
Found linux image: /boot/vmlinuz-3.16.0-31-generic
Found initrd image: /boot/initrd.img-3.16.0-31-generic
Found linux image: /boot/vmlinuz-3.16.0-30-generic
Found initrd image: /boot/initrd.img-3.16.0-30-generic
Found linux image: /boot/vmlinuz-3.16.0-29-generic
Found initrd image: /boot/initrd.img-3.16.0-29-generic
Found linux image: /boot/vmlinuz-3.13.0-44-generic
Found initrd image: /boot/initrd.img-3.13.0-44-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Recovery Environment (loader) on /dev/sda1
Found Windows 7 (loader) on /dev/sda2
done
Purging configuration files for linux-image-extra-3.16.0-29-generic (3.16.0-29.39) ...
Removing linux-image-3.16.0-29-generic (3.16.0-29.39) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.16.0-29-generic /boot/vmlinuz-3.16.0-
29-generic
update-initramfs: Deleting /boot/initrd.img-3.16.0-29-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.16.0-29-generic /boot/vmlinuz-3.16.0-
29-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.16.0-34-generic
Found initrd image: /boot/initrd.img-3.16.0-34-generic
Found linux image: /boot/vmlinuz-3.16.0-33-generic
Found initrd image: /boot/initrd.img-3.16.0-33-generic
Found linux image: /boot/vmlinuz-3.16.0-31-generic
Found initrd image: /boot/initrd.img-3.16.0-31-generic
Found linux image: /boot/vmlinuz-3.16.0-30-generic
Found initrd image: /boot/initrd.img-3.16.0-30-generic
Found linux image: /boot/vmlinuz-3.13.0-44-generic
Found initrd image: /boot/initrd.img-3.13.0-44-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Recovery Environment (loader) on /dev/sda1
Found Windows 7 (loader) on /dev/sda2
done
Purging configuration files for linux-image-3.16.0-29-generic (3.16.0-29.39) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.16.0-29-generic /boot/vmlinuz-3.16.0-
29-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.16.0-29-generic /boot/vmlinuz-3.16.0-
29-generic
Removing python-pexpect (3.2-1) ...
Removing wine-gecko2.21:i386 (2.21-0ubuntu1) ...
Removing wine-mono0.0.8 (0.0.8-0ubuntu1) ...
Processing triggers for menu (2.1.47ubuntu1) ...
Processing triggers for libc-bin (2.19-10ubuntu2.3) ...
tapas@tapas-VPCYB35AN:~$ sudo apt-get purge ^C
tapas@tapas-VPCYB35AN:~$ sudo apt-get purge --auto-remove gadmin-openvpn-client
[sudo] password for tapas:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package 'gadmin-openvpn-client' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 10 not upgraded.
tapas@tapas-VPCYB35AN:~$
Editing file from –
auto lo br0
iface lo inet loopback
iface br0 inet static
address 192.168.1.10
netmask 255.255.255.0
gateway 192.168.1.1
bridge_ports eth0
iface eth0 inet manual
up ip link set $IFACE up promisc on
down ip link set $IFACE down promisc off
~
~
~
~
~
~
~
~
~
~
~
To ----
auto lo
iface lo inet loopback
uto eth0
iface eth0 inet dhcp
tapas@tapas-VPCYB35AN:~$ sudo /etc/init.d/networking restart
[sudo] password for tapas:
stop: Job failed while stopping
start: Job is already running: networking
tapas@tapas-VPCYB35AN:~$ sudo /etc/init.d/networking restart
stop: Job failed while stopping
start: Job is already running: networking
tapas@tapas-VPCYB35AN:~$ sudo ifconfig
br0
 Link encap:Ethernet HWaddr 54:42:49:ff:91:f9
inet addr:192.168.1.10 Bcast:192.168.1.255 Mask:255.255.255.0
inet6 addr: fe80::5642:49ff:feff:91f9/64 Scope:Link
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:0 (0.0 B) TX bytes:1507 (1.5 KB)
eth0
Link encap:Ethernet HWaddr 54:42:49:ff:91:f9
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
lo
wlan0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:65536 Metric:1
RX packets:1975 errors:0 dropped:0 overruns:0 frame:0
TX packets:1975 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:213179 (213.1 KB) TX bytes:213179 (213.1 KB)
Link encap:Ethernet HWaddr 64:27:37:b1:15:9e
inet addr:192.168.223.107 Bcast:192.168.223.255 Mask:255.255.255.0
inet6 addr: fe80::6627:37ff:feb1:159e/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:50 errors:0 dropped:0 overruns:0 frame:0
TX packets:135 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:11513 (11.5 KB) TX bytes:28183 (28.1 KB)

Now trying "sudo ifdown br0 && sudo ifdown eth0 && sudo ifup eth0" ...

tapas@tapas-VPCYB35AN:~$ sudo ifdown br0 && sudo ifdown eth0 && sudo ifup eth0
[sudo] password for tapas: 
RTNETLINK answers: No such process
ifdown: interface eth0 not configured
tapas@tapas-VPCYB35AN:~$ sudo ifdown br0 && sudo ifdown eth0 && sudo ifup eth0
ifdown: interface br0 not configured
tapas@tapas-VPCYB35AN:~$

---

### Post by michi1983 on 2015-04-14
I can't see where you did:```
sudo apt-get purge --auto-remove gadmin-openvpn-server
```

---

### Post by tapasray on 2015-04-14
tapas@tapas-VPCYB35AN:~$ sudo ifdown br0 && sudo ifdown eth0 && sudo ifup eth0
[sudo] password for tapas: 
RTNETLINK answers: No such process
ifdown: interface eth0 not configured
tapas@tapas-VPCYB35AN:~$ sudo ifdown br0 && sudo ifdown eth0 && sudo ifup eth0
ifdown: interface br0 not configured
tapas@tapas-VPCYB35AN:~$

> **michi1983 said:**
> I can't see where you did:```
sudo apt-get purge --auto-remove gadmin-openvpn-server
```

Ok, let me go through the steps again and post the output.

... but it's there right at the top ... attaching a pdf in which I had saved it --

If you can't open the file or can't find what you are looking for, please let me know and I'll do those steps again.

Oh no, the remove server command is not there in the file, too. Sorry. Let me repeat it.

tapas@tapas-VPCYB35AN:~$ sudo apt-get purge --auto-remove gadmin-openvpn-server
[sudo] password for tapas: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  gadmin-openvpn-server*
0 upgraded, 0 newly installed, 1 to remove and 10 not upgraded.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 329082 files and directories currently installed.)
Removing gadmin-openvpn-server (0.1.5-3.1) ...
Purging configuration files for gadmin-openvpn-server (0.1.5-3.1) ...
dpkg: warning: while removing gadmin-openvpn-server, directory '/etc/gadmin-openvpn' not empty so not removed
Processing triggers for menu (2.1.47ubuntu1) ...
tapas@tapas-VPCYB35AN:~$

---

### Post by michi1983 on 2015-04-14
Alright, now to be sure, please restart your computer and after that, please post again the output of ```
ifconfig
```

---

### Post by tapasray on 2015-04-14
Hi! I have to be away for a couple of hours. Thanks for everything. Will be back.

Ok, o/p of "ifconfig" --

tapas@tapas-VPCYB35AN:~$ ifconfig
br0       Link encap:Ethernet  HWaddr 54:42:49:ff:91:f9  
          inet addr:192.168.1.10  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::5642:49ff:feff:91f9/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:1092 (1.0 KB)

eth0      Link encap:Ethernet  HWaddr 54:42:49:ff:91:f9  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1766 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1766 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:182547 (182.5 KB)  TX bytes:182547 (182.5 KB)

wlan0     Link encap:Ethernet  HWaddr 64:27:37:b1:15:9e  
          inet addr:192.168.0.134  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::6627:37ff:feb1:159e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:883 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1025 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:462473 (462.4 KB)  TX bytes:174422 (174.4 KB)

---

### Post by michi1983 on 2015-04-14
okay, so the sh** br0 is still here ;)

please post the output of ```
cat /etc/network/interfaces
```

---

### Post by tapasray on 2015-04-14
Ok, o/p of "ifconfig" --

tapas@tapas-VPCYB35AN:~$ ifconfig
br0       Link encap:Ethernet  HWaddr 54:42:49:ff:91:f9  
          inet addr:192.168.1.10  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::5642:49ff:feff:91f9/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:1092 (1.0 KB)

eth0      Link encap:Ethernet  HWaddr 54:42:49:ff:91:f9  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1766 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1766 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:182547 (182.5 KB)  TX bytes:182547 (182.5 KB)

wlan0     Link encap:Ethernet  HWaddr 64:27:37:b1:15:9e  
          inet addr:192.168.0.134  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::6627:37ff:feb1:159e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:883 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1025 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:462473 (462.4 KB)  TX bytes:174422 (174.4 KB)

---

### Post by michi1983 on 2015-04-14
Okay, now please do a ```
sudo apt-get remove --purge bridge-utils
```

Then please remove everything in your /etc/network/interfaces file and replace it with
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

```

Then do a ```
sudo /etc/init.d/networking restart
```

And then post again the output of ```
sudo ifconfig
```

And PLEASE use (code) brackets! It makes it much easier to read what the console output is ;)
You can see here how that works:
[http://ubuntuforums.org/misc.php?do=bbcode](http://ubuntuforums.org/misc.php?do=bbcode)

---

### Post by tapasray on 2015-04-14
My net just went down, so posting this from my tablet. Placed the codes within angle brackets - can't find square brackets on the tab.

&#65279;<tapas@tapas-VPCYB35AN:~$ sudo apt-get remove --purge bridge-utils>
[sudo] password for tapas: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  bridge-utils*
0 upgraded, 0 newly installed, 1 to remove and 10 not upgraded.
After this operation, 146 kB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 329081 files and directories currently installed.)
Removing bridge-utils (1.5-7ubuntu1) ...
Purging configuration files for bridge-utils (1.5-7ubuntu1) ...
Processing triggers for man-db (2.7.0.2-2) ...
 
<tapas@tapas-VPCYB35AN:~$ sudo gedit /etc/network/interfaces>
[sudo] password for tapas: 

(gedit:8035): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

(gedit:8035): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files
tapas@tapas-VPCYB35AN:~$ sudo /etc/init.d/networking restart
stop: Job failed while stopping
start: Job is already running: networking

<tapas@tapas-VPCYB35AN:~$ sudo ifconfig>
br0       Link encap:Ethernet  HWaddr 54:42:49:ff:91:f9  
          inet addr:192.168.1.10  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::5642:49ff:feff:91f9/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:1092 (1.0 KB)

eth0      Link encap:Ethernet  HWaddr 54:42:49:ff:91:f9  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:5692 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5692 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:740791 (740.7 KB)  TX bytes:740791 (740.7 KB)

wlan0     Link encap:Ethernet  HWaddr 64:27:37:b1:15:9e  
          inet addr:192.168.0.134  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::6627:37ff:feb1:159e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:28677 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25585 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:22014502 (22.0 MB)  TX bytes:3541887 (3.5 MB)

tapas@tapas-VPCYB35AN:~$

I have placed the codes within square brackets as you wanted.

[tapas@tapas-VPCYB35AN:~$ sudo apt-get remove --purge bridge-utils]
[sudo] password for tapas: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  bridge-utils*
0 upgraded, 0 newly installed, 1 to remove and 10 not upgraded.
After this operation, 146 kB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 329081 files and directories currently installed.)
Removing bridge-utils (1.5-7ubuntu1) ...
Purging configuration files for bridge-utils (1.5-7ubuntu1) ...
Processing triggers for man-db (2.7.0.2-2) ...

[tapas@tapas-VPCYB35AN:~$ sudo gedit /etc/network/interfaces]
[sudo] password for tapas: 

(gedit:8035): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

(gedit:8035): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

[tapas@tapas-VPCYB35AN:~$ sudo /etc/init.d/networking restart]
stop: Job failed while stopping
start: Job is already running: networking

[tapas@tapas-VPCYB35AN:~$ sudo ifconfig]
br0       Link encap:Ethernet  HWaddr 54:42:49:ff:91:f9  
          inet addr:192.168.1.10  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::5642:49ff:feff:91f9/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:1092 (1.0 KB)

eth0      Link encap:Ethernet  HWaddr 54:42:49:ff:91:f9  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:5692 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5692 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:740791 (740.7 KB)  TX bytes:740791 (740.7 KB)

wlan0     Link encap:Ethernet  HWaddr 64:27:37:b1:15:9e  
          inet addr:192.168.0.134  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::6627:37ff:feb1:159e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:28677 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25585 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:22014502 (22.0 MB)  TX bytes:3541887 (3.5 MB)

---

### Post by michi1983 on 2015-04-14
Oh man :D 
In my description it tells you how to put the code within the brackets correctly. You can see the difference when I post code and when you do?
(code)here is some code (/code)
You just replace the round brackets with these []

So did you edit the /etc/network/interfaces file? Because you just posted an error but not the content of it.

---

### Post by tapasray on 2015-04-14
Ok, think I got it (the formatting thing). 

I think you are referring to the error after ```
 gedit /etc/network/interfaces 
```. Since i hadn't [sudo], I could not save the edited file. Once I used [sudo] I could. So the content of /etc/network/interfaces is now 

```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

```

I'm not sure what else to post for this.

"hadn't used [sudo] ..."

---

### Post by michi1983 on 2015-04-15
okay now reboot your computer again and post the output of
```
sudo ifconfig
``` again

---

### Post by tapasray on 2015-04-15
Hi! It's freezing up during reboot at various points. Sometimes just black screen, so I have to power off. Sometimes stuck in GRUB. Sometimes waiting for "full network configurations" and then loading "without full network configurations." After this sort of load, the wifi icon at the top doesn't show for 10/20 seconds. 

Here's the [ifconfig] o/p --

```

tapas@tapas-VPCYB35AN:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 54:42:49:ff:91:f9  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:736 errors:0 dropped:0 overruns:0 frame:0
          TX packets:736 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:58160 (58.1 KB)  TX bytes:58160 (58.1 KB)

```

---

### Post by michi1983 on 2015-04-15
Alright, so the bridge is finally gone.
Now please edit the file again that it looks like this:
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto wlan0
iface wlan inet dhcp

```

Then restart your computer again.

Post again the output of ```
sudo ifconfig
```

We are getting closer ;)

---

### Post by tapasray on 2015-04-15
Thanks! Right away ...

Here --

```

tapas@tapas-VPCYB35AN:~$ sudo gedit /etc/network/interfaces
[sudo] password for tapas: 

(gedit:4401): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

(gedit:4401): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files
tapas@tapas-VPCYB35AN:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 54:42:49:ff:91:f9  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth0:avahi Link encap:Ethernet  HWaddr 54:42:49:ff:91:f9  
          inet addr:169.254.11.243  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:7685 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7685 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:807323 (807.3 KB)  TX bytes:807323 (807.3 KB)

wlan0     Link encap:Ethernet  HWaddr 64:27:37:b1:15:9e  
          inet addr:192.168.0.134  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::6627:37ff:feb1:159e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:25151 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25162 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:24028531 (24.0 MB)  TX bytes:4015336 (4.0 MB)

```

---

### Post by michi1983 on 2015-04-15
Oh man, something is still messing up here :/
At least your eth0 tries to get an IP address from somewhere but it seems that no DHCP server is answering.

I am not sure if I have asked already but to what is your computer connected? A wifi-router/modem? If yes, can you please post some screenshots on your LAN settings from the router.
You are 100% sure that you have a working cable connected from the router/modem to your computer?

---

### Post by tapasray on 2015-04-15
Hi. I do have a working cable connection. Right now, since ethernet is not working, I'm on wifi: ADSL cable --> Modem/router --> WiFi --> Computer.

Attaching a screen shot of the cable connection's IP4 settings.

PS: The 'VPN Connections' entry is still there in the network (scroll-down) menu.

---

### Post by michi1983 on 2015-04-15
Wait! Your attached screenshot is from which device? From your Ubuntu machine?

---

### Post by tapasray on 2015-04-15
Yes. the laptop running Ubuntu.

---

### Post by michi1983 on 2015-04-15
Jesus :D Why is it on manual? You are interfering with the /etc/network/interfaces file if you set that to manual. Because we set the /etc/network/interfaces file to DHCP. 
We first wanna try if everything runs fine when set to DHCP. So please change that from "manual" to "automatic/dhcp" and lets see if you get an IP from your router.

---

### Post by tapasray on 2015-04-15
ok ...

... here's the DHCP connection. I have both set up, because I have used ethernet both ways.

---

### Post by michi1983 on 2015-04-15
Okay, and now again ```
sudo ifconfig
``` please

---

### Post by tapasray on 2015-04-15
```

tapas@tapas-VPCYB35AN:~$ sudo ifconfig
[sudo] password for tapas: 
eth0      Link encap:Ethernet  HWaddr 54:42:49:ff:91:f9  
          inet addr:192.168.0.169  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::5642:49ff:feff:91f9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:602 errors:0 dropped:0 overruns:0 frame:0
          TX packets:352 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:92899 (92.8 KB)  TX bytes:36623 (36.6 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:142 errors:0 dropped:0 overruns:0 frame:0
          TX packets:142 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:28681 (28.6 KB)  TX bytes:28681 (28.6 KB)

wlan0     Link encap:Ethernet  HWaddr 64:27:37:b1:15:9e  
          inet addr:192.168.0.134  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::6627:37ff:feb1:159e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:495 errors:0 dropped:0 overruns:0 frame:0
          TX packets:755 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:307509 (307.5 KB)  TX bytes:108185 (108.1 KB)


```

---

### Post by michi1983 on 2015-04-15
There you go, your eth0 is getting an IP address.

Please some last tests. Post the output of
```
ping 192.168.0.1
```
```
ping 8.8.8.8
```
```
ping www.google.com
```

---

### Post by tapasray on 2015-04-15
```

       RX bytes:307509 (307.5 KB)  TX bytes:108185 (108.1 KB)

tapas@tapas-VPCYB35AN:~$ ping 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
64 bytes from 192.168.0.1: icmp_seq=1 ttl=64 time=0.412 ms
64 bytes from 192.168.0.1: icmp_seq=2 ttl=64 time=0.443 ms
64 bytes from 192.168.0.1: icmp_seq=3 ttl=64 time=0.528 ms
64 bytes from 192.168.0.1: icmp_seq=4 ttl=64 time=0.560 ms
64 bytes from 192.168.0.1: icmp_seq=5 ttl=64 time=0.409 ms
64 bytes from 192.168.0.1: icmp_seq=6 ttl=64 time=0.372 ms
64 bytes from 192.168.0.1: icmp_seq=7 ttl=64 time=0.593 ms
64 bytes from 192.168.0.1: icmp_seq=8 ttl=64 time=0.391 ms
64 bytes from 192.168.0.1: icmp_seq=9 ttl=64 time=0.353 ms
64 bytes from 192.168.0.1: icmp_seq=10 ttl=64 time=0.398 ms
64 bytes from 192.168.0.1: icmp_seq=11 ttl=64 time=0.430 ms
64 bytes from 192.168.0.1: icmp_seq=12 ttl=64 time=0.591 ms
64 bytes from 192.168.0.1: icmp_seq=13 ttl=64 time=0.558 ms
64 bytes from 192.168.0.1: icmp_seq=14 ttl=64 time=0.482 ms
...

```

```

tapas@tapas-VPCYB35AN:~$ ping 8.8.8.8
connect: Network is unreachable
tapas@tapas-VPCYB35AN:~$ 

```


```

tapas@tapas-VPCYB35AN:~$ ping www.google.com
connect: Network is unreachable
tapas@tapas-VPCYB35AN:~$ 

```

---

### Post by michi1983 on 2015-04-15
Okay, this tells that your DNS settings are wrong which your router provides you.
What router do you have? And can you please post screenshots of your router settings here. NOT from your machine, from your router.

And please switch off your wifi to test the eth0. this could be a problem otherwise.

---

### Post by tapasray on 2015-04-15
That's what I was doing - meaning, I was disconnecting WiFi while testing the DHCP connection with the modem. I have just rebooted the machine and now the 'Disconnect' option for the wifi connection is disabled - it appears in faded letters! Which means I can't disconnect from WiFi at all!

---

### Post by michi1983 on 2015-04-15
When you open a terminal and type ```
sudo ifdown wlan0
``` your wifi interface should get switched off totally.
If you need it again, just type ```
sudo ifup wlan0
```

---

### Post by tapasray on 2015-04-15
It's D-Link B-330. Trying to get the router settings through wifi.

---

### Post by michi1983 on 2015-04-15
Don't you get to the webinterface (192.168.0.1) when you are only connected with wire?

---

### Post by tapasray on 2015-04-15
I have shut down the system. Will turn it back on in a minute.

I didn't get a chance to try 192.168.0.1 through wire, as I could not disconnect wifi. The 'disconnect' option got diabled after the lasr reboot!

Ok. Turned the system back on. Booting was problematic, and network has completely vanished. Went to System settings > Network, got "network services not compatible with this version"!

---

### Post by michi1983 on 2015-04-15
Hm, your system seem to be really messed up to be honest. 
This is just no normal behaviour.
Do you have any important data on your machine? Could you backup it?
I think it makes more sense to do a clean install of a fresh 14.10 installation.

Edit: last thing we could try is completely delete the network-manager inclusive gui and handle everything with the /etc/network/interfaces file
```
sudo apt-get purge network-manager
``` would be the command.
Then ```
sudo ifdown eth0 && sudo ifup eth0
```
```
sudo dhclient eth0
```

---

### Post by tapasray on 2015-04-15
Hi! Here's the modem -- 

```


WAN
Connection Type : Static IP
Cable Status : Connected
Network Status : Connected
Connection Up Time : 0 Day 0 Hour 54 Min 18 Sec
MAC Address : xxxxxxxxxxxxxx
IP Address : 172.18.141.199
Subnet Mask : 255.255.255.128
Default Gateway : 172.18.141.129
Primary DNS Server : 172.16.0.1
Secondary DNS Server : 10.10.0.1
LAN
MAC Address : xxxxxxxxxxxxxx
IP Address : 192.168.0.1
Subnet Mask : 255.255.255.0
DHCP Server : Enabled
WIRELESS LAN
Wireless Radio : Enabled
MAC Address : xxxxxxxxxxxxxx
802.11 Mode : Mixed 802.11n, 802.11g and 802.11b
Channel Width : 20/40MHz
Channel : 1
Network Name (SSID) : wishnet

Wi-Fi Protected Setup : Enabled/Configured
Security : WPA/WPA2-PSK
Guest Zone Wireless Radio : Disabled
Guest Zone Network Name (SSID) : dlink-guest

Guest Zone Security : Disabled
WIRELESS LAN2
Wireless Radio : Enabled
MAC Address : xxxxxxxxxxxxxx
802.11 Mode : Mixed 802.11ac, 802.11n and 802.11a
Channel Width : 20/40/80MHz
Channel : 40
Network Name (SSID) : wishnet5gh

Wi-Fi Protected Setup : Enabled/Configured
Security : WPA/WPA2-PSK
Guest Zone Wireless Radio : Disabled
Guest Zone Network Name (SSID) : dlink-media-guest

Guest Zone Security : Disabled
LAN COMPUTERS
MAC Address 	IP Address		Name(if any)	

```

---

### Post by michi1983 on 2015-04-15
What does ```
cat /etc/resolv.conf
``` and
```
route -n
``` say?

---

### Post by tapasray on 2015-04-15
Hi! I have to leave for a couple of hours. 

Wondering if I should try to reinstall Ubuntu as booting itself has become so troublesome now. I'll be in a soup if it crashes. Do let me know what you think. I'll check when I get back.

Thanks a ton!

---

### Post by michi1983 on 2015-04-15
Yeah to be honest, there seems to be more messed up than just the networking stuff. I would suggest (if you can backup your important data) that you start from scratch and reinstall Ubuntu again.
Sorry that I couldn't help you figuring out the problem :/

---

### Post by tapasray on 2015-04-15
Come on! Why should you be sorry?? You took a LOT of trouble and fixed the main things, but what can you do if there are other things messed up? I have Win as dual-boot, so will back up data via Win and then do a clean reinstall of 14.10. Many, many thanks again for your help and patience! I really, really appreciate it.

---

