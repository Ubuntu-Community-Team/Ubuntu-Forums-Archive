---
title: "Set primary DNS"
date: 2007-01-13
forum: Networking &amp; Wireless
---

### Post by bacsa81 on 2007-01-13
Hello!
I would like to ask for help.
I use wifi with network manager, unfortunately it sets my DNS automatically to my router, but it doesn't resolves the names at all, so I installed bind9 to have the DNS server as localhost, but still at every connection it sets back to the router and I have to change the DNS always manually.
Could someone help me how could I set somewhere the primary DNS, so in resolv.conf localhost will be always the first DNS server?
Thank you in advance!
Csaba

---

### Post by ENN0 on 2007-01-13
Try setting it to static ip and enter it yourself!

---

### Post by dbott67 on 2007-01-13
You can try manually adding the OpenDNS servers (or whatever DNS servers you want to use) to your /etc/resolv.conf file and comment out your current one:
```
sudo gedit /etc/resolv.conf
```
```
[B][COLOR="Red"]nameserver 208.67.222.222
nameserver 208.67.220.220[/COLOR][/B]
**[COLOR="Red"]#[/COLOR]** nameserver 192.168.1.1
```

***In my example, I'm using the OpenDNS IP address.  Change it to yor preferred DNS server (your mileage may vary; objects in the mirror are closer than they appear; and all other standard disclaimers apply)***.

If you notice an improvement (or it cures the problem) then you can make it permanent.  By default, the **dhclient.conf** file will overwrite the **resolv.conf** file each reboot, so you need to edit the file:

1. Backup the file first:
```
sudo cp /etc/dhcp3/dhclient.conf /etc/dhcp3/dhclient.conf.bak
```

2. Edit the dhclient.conf file:
```
sudo gedit /etc/dhcp3/dhclient.conf
```

3. Look for the following line:
```
#prepend domain-name-servers 127.0.0.1;
```
Remove the comment (#) and change it to:
```
prepend domain-name-servers **[COLOR="Red"]208.67.222.222, 208.67.220.220[/COLOR]**;
```

4. Next, look for the **[COLOR="Red"]domain-name-servers,[/COLOR]** and ***remove*** it:

```
**[COLOR="Blue"]prepend domain-name-servers 208.67.222.222, 208.67.220.220;[/COLOR]**
request subnet-mask, broadcast-address, time-offset, routers,
        domain-name, **[COLOR="Red"]domain-name-servers,[/COLOR]** host-name,
        netbios-name-servers, netbios-scope;
#require subnet-mask, domain-name-servers;
```

5. Restart your network
```
dbott@edgy:~$ sudo/etc/init.d/networking restart
```

-Dave

---

### Post by WeyOh on 2007-08-19
Thanks, this solved my issue. There are quite a few threads about this and they should all be put together... *hint*

---

### Post by SanjoEel on 2007-08-20
My first searches turned up nothing, but I must not have searched well enough, this thread is the answer to my problem. Thanks to dbott67! You're awesome Dave. I'll link this thread to mine since it offers the solution to the same issue.

---

### Post by Darganot on 2007-09-01
> **WeyOh said:**
> Thanks, this solved my issue. There are quite a few threads about this and they should all be put together... *hint*

Agreed.

---

### Post by Mecca on 2007-12-16
Just wanted to say Thanks, That Got My Debian etch system churning along nicely:guitar:

---

