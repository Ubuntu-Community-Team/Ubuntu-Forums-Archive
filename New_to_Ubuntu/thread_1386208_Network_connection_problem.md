---
title: "Network connection problem"
date: 2010-01-20
forum: New to Ubuntu
---

### Post by Troll_the_Great on 2010-01-20
Hello folks!

I have an issue with my network connection and I hope you good people can help me. :)
I connect to the internet through a PPPOE connection. I have a laptop (witch is dual booting Ubuntu and XP) and a desktop with XP. Naturally I want internet on both my computers so I bought a router. So far so good. 
The weird thing is that I can have internet on only one computer once if.If I run Ubuntu and connect to the internet, the desktop disconnects automatically. If I am connected to the internet with the desktop (XP) I can't connect with Ubuntu.
The real weird thing is that if I run XP on  both machines (laptop and desktop) I can connect to the internet with both.
Any help would be very appreciated, especially because I haven't used XP for the past year and a half, and I don't miss it one bit :D.
Thanks in advance!

---

### Post by cariboo on 2010-01-20
How does your laptop connect to the router? I would also suggest check /etc/resolv.conf to see what Ubuntu is using for dns. If it is using the router ip address for dns, you will have to change it in network manager to wherever you get your dns addresses from.

Right click The network manager icon in the top panel, select your device, then click the edit button. Next click the IPv4 tad and select Automatic (DHCP) Adresses Only from the method drop down. Manually enter your dns address and click apply, enter your pasword, and you should be done.

---

### Post by Troll_the_Great on 2010-01-20
> **cariboo907 said:**
> How does your laptop connect to the router? I would also suggest check /etc/resolv.conf to see what Ubuntu is using for dns. If it is using the router ip address for dns, you will have to change it in network manager to wherever you get your dns addresses from.

Right click The network manager icon in the top panel, select your device, then click the edit button. Next click the IPv4 tad and select Automatic (DHCP) Adresses Only from the method drop down. Manually enter your dns address and click apply, enter your pasword, and you should be done.

Here is how my /etc/resolv.conf looks like:

```
cat /etc/resolv.conf
### BEGIN INFO
#
# Modified_by:  NetworkManager
# Process:      /usr/bin/NetworkManager
# Process_id:   5450
#
### END INFO



nameserver 82.76.253.115
nameserver 82.76.253.125
```

This is my DNS?
I attached a print screen with my router settings, maybe it will help.
If I right click on Network Manager I have only "Enable Networking" "Enable Wireless" "Connection Information" and "About" so I don't know what you mean by "select your device".
I can left click on it and then go to "Manual configuration" and from there I can choose "Enable roaming mode", or, if I uncheck this option I have "Static IP address", "Automatic Configuration" and "Local Zeroconf network (IPv4 LL).
So what do I do from here?

---

### Post by Troll_the_Great on 2010-01-21
Bump!

---

### Post by Troll_the_Great on 2010-01-22
OK, I managed to make it work, but I don't why. I went into Network Manager, I deselected "Enable Roaming Mode" and choose Automatic Configuration (DHCP). Of course it didn't work, so I went back  to "Enable Roaming Mode", clicked OK, and after that it suddenly worked. I don't know why, because I didn't change anything... The bad thing is that if I restart the computer, I go back to the same problem.
Can anyone help?
Thank in advance!

---

### Post by Troll_the_Great on 2010-01-23
Bump!

---

### Post by Iowan on 2010-01-23
What IP address(es) do you get on the two machines before/after the bump. (Wondering if they're fighting for the same address). Also, (at risk of sounding naive) are you connecting to router via wire or wireless?

---

### Post by Troll_the_Great on 2010-01-23
> **Iowan said:**
> What IP address(es) do you get on the two machines before/after the bump. (Wondering if they're fighting for the same address). Also, (at risk of sounding naive) are you connecting to router via wire or wireless?

Now, I have 192.168.1.101 on the laptop and 192.168.1.102 on the desktop. I don't know what IP's I had before. I am connected via a wire on the both computers.

---

### Post by Troll_the_Great on 2010-02-05
Bump!

EDIT: I had to restart the laptop (witch is running Ubuntu) and I'm back to the same problem. I can have internet on just one computer at a time.
The computers have different internet addresses (Ubuntu 192.168.1.101, Windows 192.168.1.100) so I don't know what the problem is. If I restart the laptop and start it in windows (I dual boot) all is OK, but when I start linux I have this problem.
Please HELP!

---

### Post by Troll_the_Great on 2010-02-06
Bump!

---

### Post by Troll_the_Great on 2010-02-07
Bump!

---

### Post by Troll_the_Great on 2010-02-08
Bump!

---

### Post by Iowan on 2010-02-08
I presume the machines can ping each other? Subnet mask is standard 255.255.255.0?

---

### Post by Troll_the_Great on 2010-02-09
> **Iowan said:**
> I presume the machines can ping each other? Subnet mask is standard 255.255.255.0?

Yes, the machines can ping each other and yes, the subnet mask is 255.255.255.0

---

### Post by Iowan on 2010-02-09
I doubt it has any bearing - but what are results of **route -n**?

---

