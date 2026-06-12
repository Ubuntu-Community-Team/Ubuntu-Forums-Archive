---
title: "Where can I manually configure search domains?"
date: 2008-11-03
forum: Networking &amp; Wireless
---

### Post by phil888 on 2008-11-03
I have been unable to access windows shares since upgrading to Intrepid. problem documented in several threads. In Hardy I was able to work around this by manually entering our search domains, e.g., xyz.net, abc.com, in the network manager applet, the settings were not persistent so I had to do it every time I logged into the office network but it worked and I was able to browse and access the windows network with nautilus. The new network manager is different and though I have entered the search domains and they appear to be persistent I am having the same issues accessing windows shares that I had in Hardy if I did not manually enter the search domains. I would like to check the file in which they are stored can anyone tell where the search domain information is stored? 

Thanks.

---

### Post by davidmcq on 2008-11-24
You can edit /etc/resolv.conf

add the following line:

search yourdomain.com

Every time you re-boot this file will be over written and you  will have to do it again. If anyone can tell me where the search domain is now stored I would love to know too. D'oh!

---

### Post by bab1 on 2008-11-24
I'm curious.  Since I have configured my systems manually, I don't have these problems.  But I believe that the problem of NM overwriting the resolv.conf file is due to the dhcdbd daemon.  This is the dbus vfs damon.  The man page says the config file is:```
/usr/share/dbus-1/services/dhcdbd.service
```

Post the contents of the file for us to see.

See ```
man dhcdbd
``` for more info.

---

### Post by davidmcq on 2008-11-24
david@david:~$ cat /usr/share/dbus-1/services/dhcdbd.service
[D-BUS Service]
Name=com.redhat.dhcp
Exec=/usr/sbin/dhcdbd



I'm not quite sure where redhat got into it, but it should be irrelevant because i'm not using DHCP... static IP

---

### Post by bab1 on 2008-11-24
> I'm not quite sure where redhat got into it, but it should be irrelevant because i'm not using DHCP... static IP

Redhat is where Network Manager came from.  The NM is what keeps you from permanently changing your configuration. Unfortunately NM is running even if you have a static IP address configured.

---

### Post by davidmcq on 2008-11-25
So where does NM cache or save the ip no, search domain and DNS info?

Is the interface info is still stored in /etc/network/interfaces ?

---

### Post by Iowan on 2008-11-25
AFAIK, interface info is still stored in /etc/network/interfaces... although some threads report a working system with only "lo" information stored there.

---

### Post by bab1 on 2008-11-25
I believe that NM controls the IP addressing regardless of what is in /etc/network/interfaces, if you let it.

I'll bet these are binary glob files and not viewable by the user.

I would remove NM if you do not need it.

@davidmcq,

I'm sorry, I have not way of verifying my suspicions.  As I said, I have manually configured my network settings and never use NM.

---

