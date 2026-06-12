---
title: "ubuntu networking issue - HELP !!!"
date: 2014-10-27
forum: Networking &amp; Wireless
---

### Post by MorneDJ on 2014-10-27
First, I do not know Linux that well, but I have previously installed a few servers that I use as NAS devices. I now have a new HP Microserver that I want to use as a DHCP as well as a NAS server, and after the install the network worked perfectly using dhcp. I then changed the interfaces file to read (without the comments):

```

auto lo
iface lo inet loopback

# auto em1
# iface em1 inet dhcp

iface em1 inet static
   adress 192.168.0.211
   netmask 255.255.255.0
   network 192.168.0.0
   broadcast 192.168.0.255
   gateway 192.168.0.254


```

Yet, the network didn't want to restart. Restarting the PC showed:

At the Ubuntu 14.04 startup screen it shows 
Waiting for network configuration ... (or something similar)

So I edited the interface file and commented out the static stuff and only left 
auto em1
iface em1 inet dhcp

Yet, same problem. Now it did not want to connect at all. Cannot ping anything (```
connect: Network is unreachable
```
ifconfig -a gives
```

em1     Link encap:Ethernet  HWaddr 28:blah
           BROADCAST MULTICAST MTU:1500  Metric:1
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:1000
           RX bytes:0 (0.0 B)   TX bytes:0 (0.0 B)   
           Interrupt:18

loLink   Link encap:Local Loopback
           inet addr:127.0.0.1  Mask:255.0.0.0
           inet6 addr: ::1/128  Scope:Host
           UP LOOPBACK RUNNING   MTU:65536  Metric:1
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:1000
           RX bytes:0 (0.0 B)   TX bytes:0 (0.0 B)   
           Interrupt:18

```

Had to retype this, and did not type the MAC address.

ifup -a gives
/etc/network/interfaces:2: misplaced option
ifup: couldn't read interfaces file "/etc/network/interfaces"

Anyone have any idea what I can do ?

---

### Post by chili555 on 2014-10-27
> /etc/network/interfaces:2: misplaced optionThat means there is something misplaced or mistyped in line 2. 

I suggest you amend the file to read:```
auto lo
iface lo inet loopback

auto em1
iface em1 inet static
   ad[COLOR="#FF0000"]d[/COLOR]ress 192.168.0.211
   netmask 255.255.255.0
   gateway 192.168.0.254
   dns-nameservers 8.8.4.4 192.168.0.254
```Proofread carefully twice.

Then restart the interface:```
sudo ifdown em1 && sudo ifup -v em1
```The -v for verbose should give you some details as to what is or isn't going wrong. Check:```
ping -c3 www.google.com
```

---

### Post by TheFu on 2014-10-27
Don't comment this line:
```
auto em1
```
then restart the networking service.

---

### Post by MorneDJ on 2014-10-28
Thanks all, resolved. AS I had not internet or network connectivity I retyped that files here. It was correct. 

I misspelled address here, not in the file
the 
auto em1 line was not commented out. The First one was commented out, associated with the dhcp following line. I had a second line of 
auto em1

After struggling for 2 days with this I reinstalled ubuntu. I now have other issues that causes the server to hang (some kernel panic) but it was reported on the net so I should be able to sort this out. Having fun again :)

---

### Post by Bucky Ball on 2014-10-28
Great news. Please mark the thread as solved by following the second link in my signature and post a new thread if you have any further issues. Good luck. ;)

---

