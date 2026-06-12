---
title: "No internet"
date: 2009-03-26
forum: New to Ubuntu
---

### Post by jakupl on 2009-03-26
Hi. I installed Kubuntu 8.10 but the internet is not working. I have Ubuntu 8.04 and Windows xp on the same hd. and the internet works on both of them.

I live in a dormitory where we all have seperate IP's so I need to specify the ip, the subnet, gateway and DNS, and I have done so in Kubuntu but it still does not work. Any suggestions?

---

### Post by superprash2003 on 2009-03-26
in your terminal type the following commands and post its output

1)ifconfig
2)cat /etc/network/interfaces
3)ping 74.125.67.100

---

### Post by jakupl on 2009-03-26
> **superprash2003 said:**
> in your terminal type the following commands and post its output

1)ifconfig
2)cat /etc/network/interfaces
3)ping 74.125.67.100

Thank you. Here are the outputs:

```
jakup@bobby:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:17:31:c8:ba:44
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:33 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2220 (2.2 KB)  TX bytes:1710 (1.7 KB)
          Interrupt:20 Base address:0xb800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:28 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1568 (1.5 KB)  TX bytes:1568 (1.5 KB)
```

```
jakup@bobby:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

```
```
jakup@bobby:~$ ping 74.125.67.100
connect: Network is unreachable 
```

EDIT: sorry I'm so slow. I have to reboot twice every time something needs to be done.

---

### Post by jakupl on 2009-03-27
A premature and painful bump

---

### Post by superprash2003 on 2009-03-28
try specifying the ip in the /etc/network/interfaces file and then restart networking by typing sudo /etc/init.d/networking restart

for reference : [http://www.prash-babu.com/2008/11/how-to-setup-static-ip-address-in-linux.html](http://www.prash-babu.com/2008/11/how-to-setup-static-ip-address-in-linux.html)

---

### Post by jakupl on 2009-03-29
> **superprash2003 said:**
> try specifying the ip in the /etc/network/interfaces file and then restart networking by typing sudo /etc/init.d/networking restart

for reference : [http://www.prash-babu.com/2008/11/how-to-setup-static-ip-address-in-linux.html](http://www.prash-babu.com/2008/11/how-to-setup-static-ip-address-in-linux.html)

This did not work. This is what the terminal gave me.

```
jakup@bobby:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                   [ OK ]
jakup@bobby:~$ sudo ifdown eth0
ifdown: interface eth0 not configured
jakup@bobby:~$ sudo ifup eth0
grep: /etc/resolv.conf: No such file or directory
```

Then I tried the restart command again - for fun.

```
jakup@bobby:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...grep: /etc/resolv.conf: No such file or directory
```

If it helps, then this is how the /etc/init.d/networking file was configured before I touched it.


```
auto lo
iface lo inet loopback
```

although the referance you gave me suggests that is should look like this.
```

iface eth0 inet dhcp
```

---

### Post by hyper_ch on 2009-03-29
what's the output of
```

cat /etc/resolv.conf

```?

---

### Post by jakupl on 2009-03-29
> **hyper_ch said:**
> what's the output of
```

cat /etc/resolv.conf

```?

jakup@bobby:~$ cat /etc/resolv.conf
cat: /etc/resolv.conf: No such file or directory

---

### Post by hyper_ch on 2009-03-29
so we have no dns server set....

create that file and make an entry just like

```

nameserver IP

```

---

### Post by jakupl on 2009-03-29
> **hyper_ch said:**
> so we have no dns server set....

create that file and make an entry just like

```

nameserver IP

```

Thanks, now something happened, in KDE, the internet sign is now green instead of gray, but still no internet. Having the internet sign green, I tried redoing what superprash2003 told me.

```
jakup@bobby:~$ sudo /etc/init.d/networking restart
[sudo] password for jakup:
 * Reconfiguring network interfaces...                                   [ OK ]
jakup@bobby:~$ sudo ifdown eth0
ifdown: interface eth0 not configured
jakup@bobby:~$ sudo ifup eth0
 * if-up.d/mountnfs[eth0]: **waiting for interface lo before doing NFS mounts**
```

Is this any help?

---

### Post by hyper_ch on 2009-03-29
well, I assume you did replace "IP" with a real IP - usually the one of your router?

and the issue you get there it seems you try to mount some partitions over thenetwork? You may want to turn that of for the time being.

---

### Post by jakupl on 2009-03-29
> **hyper_ch said:**
> well, I assume you did replace "IP" with a real IP - usually the one of your router?

and the issue you get there it seems you try to mount some partitions over thenetwork? You may want to turn that of for the time being.

Well yes.

```
jakup@bobby:~$ cat /media/disk-1/etc/resolv.conf
nameserver 172.16.16.26
```

About the partitions over the network... I don't know what is happening there. I have not configured anything in kubuntu since after the install. I am not trying to mount anything over the network, but I do have a seperate /home...

---

### Post by hyper_ch on 2009-03-30
have a look at the content of that file.

---

### Post by oOarthurOo on 2009-03-30
> **jakupl said:**
> EDIT: sorry I'm so slow. I have to reboot twice every time something needs to be done.

That's interesting. Certainly not normal. I wonder if the network problems are related.

EDIT. Oh, I get it. You reboot once to get in and test it. Reboot again to report on the results. Duh.

Sorry.

---

### Post by |Porsche on 2009-03-30
Try adding this to your /etc/networks/interfaces file.
> auto eth1
#iface eth1 inet dhcp



Then do a ```
/etc/init.d/networking restart
```

---

### Post by hyper_ch on 2009-03-30
I use this for configuration of a static ip address for a ethernet card:

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
allow-hotplug eth0
iface eth0 inet static
address 10.0.0.5
netmask 255.255.255.0
network 10.0.0.0
broadcast 10.0.0.255
gateway 10.0.0.1

```

Just use eth0 or eth1 (depending what your adapter is called) and change the values to your network.

---

### Post by linux_tech on 2009-03-30
Try specifying an ip address next to nameserver

---

### Post by jakupl on 2009-03-30
> **hyper_ch said:**
> have a look at the content of that file.

what file? 
```

jakup@bobby:~$ cat /media/disk-1/etc/resolv.conf
nameserver 172.16.16.26
```
??

> **oOarthurOo said:**
> That's interesting. Certainly not normal. I wonder if the network problems are related.

EDIT. Oh, I get it. You reboot once to get in and test it. Reboot again to report on the results. Duh.

Sorry.

LOL

> **|Porsche said:**
> Try adding this to your /etc/networks/interfaces file.


Then do a ```
/etc/init.d/networking restart
```

Tried it. Nothing happens.

> **hyper_ch said:**
> I use this for configuration of a static ip address for a ethernet card:

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
allow-hotplug eth0
iface eth0 inet static
address 10.0.0.5
netmask 255.255.255.0
network 10.0.0.0
broadcast 10.0.0.255
gateway 10.0.0.1

```

Just use eth0 or eth1 (depending what your adapter is called) and change the values to your network.

I tried using that. This is how I did mine.

```
jakup@bobby~$: cat /media/disk-1/etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
allow-hotplug eth1
iface eth1 inet static
address 172.16.16.26
netmask 255.255.255.0
gateway 217.16.16.1
jakup@bobby:~$
```

It did nothing.


> **linux_tech said:**
> Try specifying an ip address next to nameserver

I have done that.

It might also help you to know that, no matter what, when I hold my mouse over the internet sign, it always sais:
Device: eth0
State: unmanaged
It doesn't matter if it is configured to eth1 or not.

---

### Post by jakupl on 2009-03-31
bump

---

### Post by superprash2003 on 2009-04-01
your output seems like you have made a typo.. your ip is 172.x.x.x but gateway is 217.x.x.x .. do you have a router? what is its ip address?

---

### Post by jakupl on 2009-04-01
> **superprash2003 said:**
> your output seems like you have made a typo.. your ip is 172.x.x.x but gateway is 217.x.x.x .. do you have a router? what is its ip address?

No this is how it should be. I live in a dormitary, where I have no control over anything. But we got a list that told us, what the numbers are, and it works in ubuntu and Windows. (I have a triple boot of ubuntu, kubuntu and windows).

---

### Post by jakupl on 2009-04-02
bump

---

