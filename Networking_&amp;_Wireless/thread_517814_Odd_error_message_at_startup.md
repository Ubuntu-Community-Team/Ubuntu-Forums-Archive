---
title: "Odd error message at startup"
date: 2007-08-05
forum: Networking &amp; Wireless
---

### Post by Sporkmaster on 2007-08-05
> Could not look up internet address for [My computer's name].
This will prevent Xfce from operating correctly.
It may be possible to correct the problem by adding
[My computer's name] to the file /etc/hosts on your system.

[My computer's name] does not literally appear in the message, my computer's actual name appears.

Oddly, my computer's name DOES appear in that file

**/etc/hosts**
> 127.0.0.1 localhost
127.0.1.1 [My computer's name].[My domain name]

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts


This started shortly after I stopped using wireless and got a wired connection. Because I'm typing this message from this computer, the Internet obviously works, and whenever I use the Internet, the guages on my panel for the eth0 wired connection spike, while those for the eth1 wireless connection do not. Therefore I'm using wired.

Anyway, long story short, what does this mean and how can I get it to go away, because it causes an extra 20 seconds of boot time and I don't see any problems with my computer.

---

### Post by noob12 on 2007-08-05
And **grep "hosts:" /etc/nsswitch.conf** says?

---

### Post by PaulFr on 2007-08-05
Perhaps XFCE is looking for just [My computer's name] in /etc/hosts and not [My computer's name].[My domain name]. If this is correct, your /etc/hosts line should read```
127.0.1.1    [My computer's name].[My domain name]     [My computer's name]
```.

---

### Post by noob12 on 2007-08-05
I think PaulFr hit it on the money.

---

### Post by Sporkmaster on 2007-08-05
Yep, that got it. Thanks alot! :)

---

