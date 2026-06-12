---
title: "Reversed IP Address"
date: 2007-04-19
forum: Networking &amp; Wireless
---

### Post by epee on 2007-04-19
I had a quick search but didn't find a topic on this. Installed Ubuntu less than a week ago - going for 100% Windows replacement.

Although I'm obviously able to network, I get some strange IP address reversals on my local network in some circumstances.

e.g. I ping a host on the local network and then 'ping' shows the ip address backwards - i.e. 14.2.168.192 and FAILS to contact the host.

If I then 'ping 192.168.2.14' - it works.

This is with Feisty Fawn 7.04 with all current updates.

Anyone come across this one?

---

### Post by spd106 on 2007-04-19
This is very odd, could you please post your /etc/resolv.conf and /etc/nsswitch.conf files.

---

### Post by epee on 2007-04-19
> **spd106 said:**
> This is very odd, could you please post your /etc/resolv.conf and /etc/nsswitch.conf files.

resolv.conf:
> nameserver 192.168.2.5
nameserver 192.168.2.1

nsswitch.conf:
> # /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis

---

### Post by epee on 2007-04-19
Example from my machine:
> user@machine:~$ ping hostname
PING hostname (14.2.168.192) 56(84) bytes of data.

--- hostname ping statistics ---
12 packets transmitted, 0 received, 100% packet loss, time 11006msNote the IP address it's resolved the 'hostname' to.

Now if I actually ping the IP address:
> user@machine:~$ ping 192.168.2.14
PING 192.168.2.14 (192.168.2.14) 56(84) bytes of data.
64 bytes from 192.168.2.14: icmp_seq=1 ttl=128 time=13.0 ms
64 bytes from 192.168.2.14: icmp_seq=2 ttl=128 time=2.43 ms
64 bytes from 192.168.2.14: icmp_seq=3 ttl=128 time=2.45 ms

---

### Post by spd106 on 2007-04-19
Do you run your own DNS server or is it simply a forwarder?

---

### Post by epee on 2007-04-20
> **spd106 said:**
> Do you run your own DNS server or is it simply a forwarder?My Cable modem/firewall/router does DHCP - I think that includes DNS for local network.

---

### Post by epee on 2007-04-20
BTW - I'm currently using a USB/Wireless adapter ([Belkin F5D6050u]("http://www.belkin.com/uk/support/product/?lid=enu&pid=F5D6050u")) - though I'll check out the wired port soon.

I also have a [Belkin F5D7051uk]("http://catalog.belkin.com/IWCatProductPage.process?Product_Id=203472") USB/Wireless adapter, but that wasn't recognised during install.

---

### Post by netztier on 2007-04-20
> **epee said:**
> Example from my machine:
Note the IP address it's resolved the 'hostname' to.

```

user@machine:~$ ping hostname
PING [COLOR="Red"]hostname (14.2.168.192)[/COLOR] 56(84) bytes of data.

--- hostname ping statistics ---
12 packets transmitted, 0 received, 100% packet loss, time 11006ms
```


Well, somehow, name resolution for "hostname" seems terribly b0rken. 

What are the results of **nslookup hostname** and/or **dig hostname**?

best regards

Marc

---

### Post by epee on 2007-04-20
> **netztier said:**
> Well, somehow, name resolution for "hostname" seems terribly b0rken. Indeed.

> **netztier said:**
> What are the results of **nslookup hostname** and/or **dig hostname**
```
user@machine:~$ nslookup hostname
Server:         192.168.2.5
Address:        192.168.2.5#53

Non-authoritative answer:
Name:   hostname
Address: 14.2.168.192
```Which is backwards...

---

### Post by inzpektor on 2007-04-23
I had the same problem on my local network - I couldn't use hostnames.

What I did was to install **winbind**:

```
sudo apt-get install winbind
```

...and then I changed the line in /etc/nsswitch.conf from:

```
hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
```

to:

```
hosts:          files mdns4_minimal **wins** [NOTFOUND=return] dns mdns4
```

Then:

```
sudo /etc/init.d/samba restart
sudo /etc/init.d/winbind restart
```

Now, hostnames work again.

---

### Post by epee on 2007-04-25
> **inzpektor said:**
> 
...and then I changed the line in /etc/nsswitch.conf from:That breaks my system - no Internet access after that.

> **inzpektor said:**
> 
```
sudo /etc/init.d/samba restart
```
Gets me > sudo: /etc/init.d/samba: command not found

> **inzpektor said:**
> 
Now, hostnames work again.In my case, it is all still wrong.

So, anyone got any better idea?

---

### Post by epee on 2007-04-25
OK, now installed Samba as per [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

And still nslookup reports reversed IP addresses. :mad:

---

### Post by spd106 on 2007-04-25
Can you try a live cd?

---

### Post by epee on 2007-04-26
> **spd106 said:**
> Can you try a live cd?I could, but what am I trying?

My system was installed from a 7.04 (beta) download, and all updates applied since. The problem has been there from shortly after the install - possibly even before any updates were applied.

---

### Post by Wicca on 2007-04-26
Looks like something is wrong in the zonefile of the DNS. It's odd, but it almost seems like that a PTR-record (meant for a reverse lookup) is placed as a A-record (normal lookup), in which case you'll get the IP address reversed.   

> **epee said:**
> resolv.conf:
nameserver 192.168.2.5
nameserver 192.168.2.1


> **epee said:**
> My Cable modem/firewall/router does DHCP - I think that includes DNS for local network.

Which of the above nameservers in your resolv.conf is your router? Take the **other one** out (just comment it) and restart your interfaces..

```
sudo ifdown -a
sudo ifup -a
```

..and see what happens.

Also, just te be sure, can you post your /etc/hosts?

---

### Post by netztier on 2007-04-28
> **epee said:**
> Indeed.


```
user@machine:~$ nslookup hostname
Server:         192.168.2.5
Address:        192.168.2.5#53

Non-authoritative answer:
Name:   hostname
Address: 14.2.168.192
```Which is backwards...

What do the forward and reverse zone files on 192.168.2.5 (which seems to be the DNS giving out this answer)  look like? Please post them.

best regards

Marc

---

