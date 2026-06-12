---
title: "DNS lost after restart"
date: 2007-01-23
forum: Networking &amp; Wireless
---

### Post by nimphelos on 2007-01-23
I am usingg 6.10 on my PC. Some time ago I installed sendmail for testing. And then I uninstalled it. After a few days I  restarted my PC but after restarting my PC lost DNS connection. I tried to restart networking 
```
/etc/init.d/networking restart
```but it answered  ```
name=;; connection timed out; no servers could be reached
``` then I tried to fix it from GUI. Administration->Networking->DNS tab there is two fields "DNS servers" and "Search" domains. I entered my local router 10.0.0.138 to DNS servers field. And all fixed. But after restarting I lost my DNS connection again. Whats the problem?

---

### Post by milton1 on 2007-01-23
I doubt that your router is a dns server. Set your router as default gateway and use your isp for dns server.

---

### Post by nimphelos on 2007-01-23
> **milton1 said:**
> I doubt that your router is a dns server. Set your router as default gateway and use your isp for dns server.
My router is a DNS server. Here is the network configuration:
```

# The primary network interface
auto eth0
iface eth0 inet static
address 10.0.0.2
netmask 255.255.255.0
gateway 10.0.0.138

```

---

### Post by milton1 on 2007-01-23
I apologize if I sounded terse previously, but I don't see how your router can be a dns. DNS, Domain Name System, translates hostnames to ip addresses for web browsing. Does your router maintain a database of hostnames and their related ip addresses? If so, tell me what kind it is so I can get one. If not, you have to tell your system where to look for this translation. In either case, failure to contact a dns server should not cause your networking to fail. It is more likely that the problem lies elsewhere. Hope this helps.

---

### Post by SendDerek on 2007-01-23
Will this thread help?

[How-To Stabilise your DNS addresses]("http://www.ubuntuforums.org/showthread.php?t=282034")

---

### Post by dannyboy79 on 2007-01-23
> **nimphelos said:**
> My router is a DNS server. Here is the network configuration:
```

# The primary network interface
auto eth0
iface eth0 inet static
address 10.0.0.2
netmask 255.255.255.0
gateway 10.0.0.138

```


your router is NOT a DNS Server I am 99% sure of this. What it does do however is use your ISP's DNS servers and forwards that info onto your computer. that's what a lot of home routers do. To be sure that you'll always be connected to DNS servers, I just simply put the numbers that show up in my routers config setup into the dns location within the networking tab. that should ensure you always have reference to dns servers. also, if you're using dhcp, sometimes your /etc/resolv.conf (or is it resolve.conf) get's overwritten when you get a new ip lease from your dhcp server so I believe to solve this I added a line at the end of the eth0 entry within /etc/network/interfaces file like this:
dns-nameservers xx.xxx.xx.xx

and that should do it. although I can't say for sure because I have since switched to static ip cause my ubuntu dapper install is a samba, sshd, and ftp server.

---

### Post by nimphelos on 2007-01-23
```
Will this thread help?

How-To Stabilise your DNS addresses

```
OpenDNS is a great idea. I didn't heard of it before. I was sad about my ISPs DNS. I have changed my router configuration to those DNS servers. And I changed my local files as the post said. I will reboot now. We will se if it's work...

> **dannyboy79 said:**
> your router is NOT a DNS Server I am 99% sure of this. What it does do however is use your ISP's DNS servers and forwards that info onto your computer. that's what a lot of home routers do. 

My router really have a DNS server guys. I am using Alcatel Speddtouch 500 series you can check in product page. And also I am using DNS server in local network. I am sure about that.

---

### Post by nimphelos on 2007-01-23
It still doesn't work. 

It's so strange it works when I set it form GUI but after restart all settings are lost. Maybe this will help 

```
$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          addr=10.0.0.2,           name=;; connection timed out; no servers could be reached
Updating databases ...
Reading configuration from /etc/mail/sendmail.conf.
Validating configuration.
Creating /etc/mail/databases...
Updating Makefile ...
Reading configuration from /etc/mail/sendmail.conf.
Validating configuration.
Creating /etc/mail/Makefile...
Updating sendmail.cf ...
Updating auth ...
hostname: Host name lookup failure
Creating /etc/mail/relay-domains
# Optional file...
The following file(s) have changed:
  /etc/mail/sendmail.cf
** ** You should issue `/etc/init.d/sendmail reload` ** **
Reloading Mail Transport Agent configuration: sendmail.
                                                                         [ ok ]

```
After GUI work done.
```

$ sudo /etc/init.d/networking restart

 * Reconfiguring network interfaces...                                                                                       addr=10.0.0.2,           name=nimphelos.firefinger
Updating databases ...
Reading configuration from /etc/mail/sendmail.conf.
Validating configuration.
Creating /etc/mail/databases...
Updating Makefile ...
Reading configuration from /etc/mail/sendmail.conf.
Validating configuration.
Creating /etc/mail/Makefile...
Updating sendmail.cf ...
Updating auth ...
sasl2-bin not installed, not configuring sendmail support.

To enable sendmail SASL2 support at a later date, invoke "/usr/share/sendmail/update_auth"

Creating /etc/mail/relay-domains
# Optional file...
The following file(s) have changed:
  /etc/mail/sendmail.cf
** ** You should issue `/etc/init.d/sendmail reload` ** **
Reloading Mail Transport Agent configuration: sendmail.
```

---

### Post by milton1 on 2007-01-23
Sorry I doubted you. That box does claim to be a dns server.

---

### Post by dannyboy79 on 2007-01-24
this should work for dapper, [http://ubuntuforums.org/showthread.php?t=305275](http://ubuntuforums.org/showthread.php?t=305275)

if you have edgy thy this; it's the very last post in the thread: [http://www.ubuntuforums.org/showthread.php?t=306308&highlight=dns+settings+overwritten](http://www.ubuntuforums.org/showthread.php?t=306308&highlight=dns+settings+overwritten)

good luck!

oh, sorry for doubting your router was a dns server.

---

### Post by nimphelos on 2007-01-24
> **dannyboy79 said:**
> 
oh, sorry for doubting your router was a dns server.

My router is very sad. It thinks it get insulted. Ping it to make it happy please ^^

---

### Post by nimphelos on 2007-01-24
Hurray guys all set.Here is the solution. 

First I opened "/etc/resolvconf/resolv.conf.d". There are 4 files 

"base, head, original, tail"

I opened 4 files and just "original" has DNS information.

In "head" it says 

> # Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN


I opened manual page for resolvconf. Manual page says        
> /etc/resolvconf/resolv.conf.d/base File containing basic resolver information.  The lines in this file are included in the  resolver  configuration file even when no interfaces are configured.


Then I saved "orginal" as "base". Because "orginal" has DNS information.

```

sudo rm /etc/resolvconf/resolv.conf.d/base
sudo cp /etc/resolvconf/resolv.conf.d/orginal /etc/resolvconf/resolv.conf.d/base

```

After reboot everything was fine.

---

### Post by dannyboy79 on 2007-01-24
i am glad you got it. did my links help?

---

### Post by nimphelos on 2007-01-24
> **dannyboy79 said:**
> i am glad you got it. did my links help?

[This]("http://www.ubuntuforums.org/showpost.php?p=1804774&postcount=6") entry helped me a lot.  Thanks for your help.

---

### Post by bve on 2007-02-07
Hey I know you got your problem solved but I thought you uninstalled sendmail.

If that's the case then why all the references to sendmail when you restart your network service? [http://www.ubuntuforums.org/showpost.php?p=2054008&postcount=8](http://www.ubuntuforums.org/showpost.php?p=2054008&postcount=8)

Just doesn't seem right to me...

---

### Post by dannyboy79 on 2007-02-07
bve, I get those same sendmail errors but my sendmail works so what is the deal with those errors??? I actually don't really have sendmail setup as a mail server, I only have it set up so that I receive emails on my Treo 700P of like my tripwire reports, my cron jobs if they fail, and my logcheck reports. and I do get all these emails throughout the day so is there anything actions required on my part to make those errors go away or can I just ignore them? thanks if you can help.

---

