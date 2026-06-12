---
title: "ppp0 does not come up at system start"
date: 2006-11-01
forum: Networking &amp; Wireless
---

### Post by Xnor on 2006-11-01
Hello!

My new 6.10 Ubuntu doesn't want to start the interface ppp0 automatically at boot. I'm using a known good /etc/network/interfaces from a Debian install. It's configured to bring up a tunnel (ppp0) automatically. It worked on Deb/Sarge, but now I have to enter: ```
sudo ifup ppp0
```, before surfing the net through that interface. 

Can you give me a hint please?

yours

Xnor

---

### Post by kkinder on 2006-11-01
In /etc/network/interfaces, you can add an "auto ppp0" line -- that should do it.

---

### Post by Xnor on 2006-11-01
Hello!

Thanks for that, but the "auto" keyword is already there. It is a working config with Debian. The problem should be somewhere else. My eth1 was also  not coming up automatically until I enabled it in the GUI in the Network mgmt. (There is no possibility to choose ppp0 there.)

Xnor

---

### Post by kkinder on 2006-11-01
Perhaps there was an error on starting. Can you look around the logs in /var/log and see if anything seems relevant? Also, can you paste your /etc/network/interfaces file?

---

### Post by Xnor on 2006-11-01
Hi!
Here is my /etc/network/interfaces: 
```

auto lo
        iface lo inet loopback

# The primary network interface
auto eth0
        iface eth0 inet dhcp
        up route add -host 10.0.0.3 gw 10.6.0.1
        up route add -net 10.0.0.0 netmask 255.0.0.0 gw 10.6.0.1
        up iptables-restore < /etc/network/firewall-rules

auto ppp0
        iface ppp0 inet ppp
        provider vcgraz

auto eth1
        iface eth1 inet static
        address 192.168.1.3
        netmask 255.255.255.0

```
In the /var/log/boot I've found the following interesting thing: 
```
Nov  1 20:53:07 rcS:  * Configuring network interfaces...       .[80G .[74G[ ok ]                                                                            
Nov  1 20:53:08 rcS: cd: 33: can't cd to /var/run/pppconfig  
```
In /var/log/ppp-connection-errors
```
pptp warn[pptp_gre_bind:pptp_gre.c:95]: connect: Network is unreachable                                                                                      
pptp fatal[main:pptp.c:275]: Cannot bind GRE socket, aborting.
```

Well until now that's all I've found. 

yours

Xnor

---

### Post by Xnor on 2006-11-01
Hi!

Creating that /var/run/pppconfig did of course not help. (But anyway, I tried it. ](*,) )
So I would really appreciate any help, that is the point where I am absolutely stuck. 

thanks!

Xnor

---

### Post by kkinder on 2006-11-01
And yet it works fine when you use ifup/ifdown? That's most curious. Perhaps Edgy's new init.d replacement, upstart, didn't get all the dependencies in place before trying to put up the interface.

Have you tried configuring ppp from scratch in (k)ubuntu and seeing if that works?

---

### Post by Xnor on 2006-11-01
Yes it works perfectly with ifup/down.  
I was installing the ppp and pptp-linux package which comes with Ubuntu, then  
I was configuring them and they work. Did you mean this by configuring from scratch ?   
IMHO you should have right with your assumption about upstart. I don't think there are any problems in the config files of ppp. 
Too bad I have no idea about upstart. 

Thanks!

Xnor

Ps. now I'm searching for some docs about that upstart thing...

---

