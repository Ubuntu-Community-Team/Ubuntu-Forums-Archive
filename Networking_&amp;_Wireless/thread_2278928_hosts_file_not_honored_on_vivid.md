---
title: "hosts file not honored on vivid"
date: 2015-05-19
forum: Networking &amp; Wireless
---

### Post by hendo2515 on 2015-05-19
Today I went to use firefox on my ubuntu vivd desktop to connect to my dev server and its not honoring the hosts file. This used to be a problem in the past with dnsmasq but has not been a problem of late. I did go through all the solutions for dnsmasq but it hasn't made a difference.

Has anyone had the same issue lately?

These are the past two software updates 

105 Upgrade: hplip:amd64 (3.15.2-0ubuntu4, 3.15.2-0ubuntu4.1), libsane-hpaio:amd64 (3.15.2-0ubuntu4, 3.15.2-0ubuntu4.1), firefox-locale-en:amd64 (37.0.2+build1-0ubuntu0.1    5.04.1, 38.0+build3-0ubuntu0.15.04.1), libhpmud0:amd64 (3.15.2-0ubuntu4, 3.15.2-0ubuntu4.1), firefox:amd64 (37.0.2+build1-0ubuntu0.15.04.1, 38.0+build3-0ubuntu0.15.04    .1), libgudev-1.0-0:amd64 (219-7ubuntu4, 219-7ubuntu5), printer-driver-postscript-hp:amd64 (3.15.2-0ubuntu4, 3.15.2-0ubuntu4.1), gir1.2-gudev-1.0:amd64 (219-7ubuntu4,     219-7ubuntu5), printer-driver-hpcups:amd64 (3.15.2-0ubuntu4, 3.15.2-0ubuntu4.1), hplip-data:amd64 (3.15.2-0ubuntu4, 3.15.2-0ubuntu4.1), scudcloud:amd64 (1.0-33, 1.0-    35)
106 End-Date: 2015-05-16  14:49:26
107 
108 Start-Date: 2015-05-20  07:43:20
110 Commandline: aptdaemon role='role-commit-packages' sender=':1.95'
111 Upgrade: thunderbird-locale-en-us:amd64 (31.6.0+build1-0ubuntu1, 31.7.0+build1-0ubuntu0.15.04.1), thunderbird:amd64 (31.6.0+build1-0ubuntu1, 31.7.0+build1-0ubuntu0.15    .04.1), libpam-systemd:amd64 (219-7ubuntu4, 219-7ubuntu5), udev:amd64 (219-7ubuntu4, 219-7ubuntu5), thunderbird-locale-en:amd64 (31.6.0+build1-0ubuntu1, 31.7.0+build1    -0ubuntu0.15.04.1), libudev1:amd64 (219-7ubuntu4, 219-7ubuntu5), libudev1:i386 (219-7ubuntu4, 219-7ubuntu5), thunderbird-gnome-support:amd64 (31.6.0+build1-0ubuntu1,     31.7.0+build1-0ubuntu0.15.04.1), systemd-sysv:amd64 (219-7ubuntu4, 219-7ubuntu5), systemd:amd64 (219-7ubuntu4, 219-7ubuntu5), libsystemd0:amd64 (219-7ubuntu4, 219-7ub    untu5), libsystemd0:i386 (219-7ubuntu4, 219-7ubuntu5)

---

### Post by SeijiSensei on 2015-05-20
Do you have this line in /etc/nsswitch.conf?
```
hosts:          files mdns4_minimal [NOTFOUND=return] dns
```
That tells the resolver to use /etc/hosts ("files") first.

---

### Post by hendo2515 on 2015-05-20
Yes i do. Also did commented out dns=dnsmasq in the networkmanager.conf file

---

### Post by bab1 on 2015-05-20
> **hendo2515 said:**
> Yes i do. Also did commented out dns=dnsmasq in the networkmanager.conf file

Post the output of ```
cat /etc/hosts
```

---

### Post by hendo2515 on 2015-05-20
Certainly
> 127.0.0.1	localhost
127.0.1.1	mel-prgl001

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

#Dev VM on my workstation
10.37.14.231 mydevserver.com.au
#QA in port
#10.38.69.105 mydevserver.com.au
#Prod in EXB
#10.75.223.232 mydevserver.com.au
#10.75.223.234 mydevserver.com.au
#10.75.223.233 mydevserver.com.au
#Prod VIP
#203.28.28.20 mydevserver.com.au
#Port prod
#10.38.69.135 mydevserver.com.au
#Port VIP
#103.29.162.85  mydevserver.com.au
#Port servers
#app1
#10.38.69.135 mydevserver.com.au

---

### Post by bab1 on 2015-05-20
> **hendo2515 said:**
> Certainly
Post the output of these 2 commands```

ping -c2 mel-prgl001

ping -c2 mydevserver.com.au

```

---

### Post by hendo2515 on 2015-05-20
So I boot up this morning and its working as expected. Not sure what happened here. I rebooted about thirty times yesterday after making changes. Thanks everyone for your help

---

