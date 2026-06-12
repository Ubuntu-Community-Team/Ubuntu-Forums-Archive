---
title: "Dns Problem"
date: 2008-07-13
forum: Networking &amp; Wireless
---

### Post by Loukisgr on 2008-07-13
Hello,

i want to ask something about DNS. Lately i see that i can't ping my second computer by using it's computername e.g kirkos which is using xp form my ubuntu. The same happens in the other way.(xp can't ping ubuntu).

I am using static ip's and by using them i can ping each other. I use as a dns server my router. Ubuntu machine is in domain(speedygr).

I have already added in the /etc/resolv.conf the

192.168.1.2(ubuntu's ip) speedy speedygr speedy.speedygr

In xp i use wins pointing the ubuntu.

What am i missing? The xp pc works perfectly as i tested it by pinging a 3rd pc

Thanks in advance.

p.s i was used to use dhcp3 in ubuntu but after update to 8.04 it doesn't starts. i use samba too.

---

### Post by pytheas22 on 2008-07-13
Try adding this line to /etc/resolv.conf:
```

nameserver 192.168.1.1
```

Does it help?

---

### Post by Loukisgr on 2008-07-13
i have already added that,

/etc/resolv.conf

search lan 192.168.1.2 192.168.1.1
domain SPEEDYGR
nameserver 192.168.1.1

/etc/hosts

127.0.0.1 localhost SPEEDY.SPEEDYGR
192.168.1.2 SPEEDY.SPEEDYGR SPEEDYGR SPEEDY.SPEEDYGR

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

that's what it contains. Another think is that from the day i created the domain i get the message (unable to resolve host speedy) when i use sudo.

That's right of course as ubuntu thinks my new computername is speedy.speedygr

thanks anyway!!. Better idea?

---

### Post by pytheas22 on 2008-07-13
What does:
```

ipconfig /all
```

on your Windows box tell you (with regards specifically to DNS)?

---

### Post by Loukisgr on 2008-07-14
As i said windows works perfectly. It has 192.168.1.3 as an ip and 192.168.1.1 as a dns and default gateway. I enabled wins too pointing the ubuntu.

In linux i have 192.168.1.2 as an ip, 192.168.1.1 as a gateway and dns

---

### Post by pytheas22 on 2008-07-14
> windows works perfectly. It has 192.168.1.3 as an ip and 192.168.1.1 as a dns and default gateway.

In that case it should work to add just the line:
```

nameserver 192.168.1.1
```

to /etc/resolv.conf.  Could you try deleting or commenting out everything else in that file, and adding just the line above?  You've got a lot of other stuff in there now and I'm not sure what it is doing.  After you make the change, reboot or run:
```

sudo /etc/init.d/networking restart
```

and see if it makes a difference.

---

### Post by Loukisgr on 2008-07-14
sorry no luck at all...

to make matters worse i installed ubuntu to my laptop and i had the same problem. DNS works only for websites.

---

### Post by Loukisgr on 2008-07-14
Can you check it to your home lan if you have one? I think there might be a wrong (by default) configuration

---

### Post by pytheas22 on 2008-07-14
Sorry that didn't help.

My LAN just uses this information in /etc/resolv.conf:
```

### BEGIN INFO
#
# Modified_by:  NetworkManager
# Process:      /usr/bin/NetworkManager
# Process_id:   5431
#
### END INFO


nameserver 192.168.1.1
```

192.168.1.1 is my gateway.

But I don't need to resolve local machine names; I always just connect them using their IPs.

Also, this is just a shot in the dark, but maybe installing samba would help.  It doesn't make too much sense, but maybe Ubuntu needs samba to resolve Windows hostnames or something.  Couldn't hurt to try.

---

### Post by Loukisgr on 2008-07-15
np ;) it's just too strange... 

Can you ping them with their computer names?

Maybe i have to make the ubuntu as dns server.

I will install another linux to try. I tryied another in my job which worked perfect.

---

### Post by Loukisgr on 2008-07-15
the strange think continues..... I just used a live cd(linux mint) and now xp can resolve the linux's machine name but not the opposite!!!! Maybe due to live cd but still strange....

Anyway i stoped the firestarter from my ubuntu and suddenly i had the same reaction as the above. It's a step but still my linux can't ping with hostnames

---

### Post by Loukisgr on 2008-07-15
I have found a solution!!!! Try and tell me it worked fine to me ;)

gedit /etc/nsswitch.conf

and alter 
hosts:          files wins bcast dns mdns4_minimal [NOTFOUND=return] mdns4

Let me explain here. I added wins for windows clients and bcast because every network card has it's own resolution table ;)

It worked for mebecause they are in the same domain. Still no luck if not.

---

### Post by Iowan on 2008-07-15
[Another ]("http://ubuntuforums.org/showthread.php?t=778898") possibility?

---

