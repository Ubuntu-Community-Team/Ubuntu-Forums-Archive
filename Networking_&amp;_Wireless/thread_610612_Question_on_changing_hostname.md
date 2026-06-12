---
title: "Question on changing hostname"
date: 2007-11-12
forum: Networking &amp; Wireless
---

### Post by satimis on 2007-11-12
Hi folks,


Ubuntu 7.04 server amd64


I need to change hostname from;```

ubuntu.satimis.com
```

to:```

mail.satimis.com

```


Apart making changes on;

1)
$ sudo postconf -e myhostname=mail.satimis.com
$ cat /etc/postfix/main.cf | grep myhostname```

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
myhostname = mail.satimis.com

```

$ sudo /etc/init.d/postfix restart```

 * Stopping Postfix Mail Transport Agent postfix                         [ OK ] 
 * Starting Postfix Mail Transport Agent postfix                         [ OK ] 

```


2)
Edit /etc/hosts as;```

127.0.0.1       localhost.localdomain   localhost
192.168.0.10    mail.satimis.com        mail

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

Edit  /etc/hostname as;```

mail.satimis.com

```


$ sudo newaliases
$ sudo hostname mail.satimis.com
Both w/o complaint


$ uname -n
mail.satimis.com
$ hostname -a
mail 
$ hostname -s
mail
$ hostname -d
satimis.com
$ hostname -f
mail.satimis.com
$ hostname
mail.satimis.com
$ hostname -i
192.168.0.10
$ hostname -y
(none)


I don't have /etc/sysconfig/network file and "sysconfig" directory


Please advise any other files I need to edit as well.  TIA


Edit:

Found following errors:-


1)
$ cat /etc/resolve.conf;```

nameserver 202.14.67.4
nameserver 202.14.67.14
satimis@#ubuntu

```
202.14.67.4
202.14.67.14

are DNS of ISP.

I think there is a mistake here.  Whether delete "satimis@#ubuntu" and replace it with "mail.satimis.com"?


2)
At booting on text scrolling;```

Warning:unable to determin IP address of 
'ubuntu_mail.satimis.com' error: no value servers 
configured - Fatal error processing configuration file 
'/etc/proftpd/proftpd.con   [fail]

```


3)
Login as satimis.  On console, it prompt;```

mail:~$ 

```

Not```

satimis@mail:~$

```


4)
$ dig satimis.com```


; <<>> DiG 9.3.4 <<>> satimis.com
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 56433
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 2, ADDITIONAL: 2

;; QUESTION SECTION:
;satimis.com.                   IN      A

;; ANSWER SECTION:
satimis.com.            3600    IN      A       220.232.213.178

;; AUTHORITY SECTION:
satimis.com.            3600    IN      NS      ns43.domaincontrol.com.
satimis.com.            3600    IN      NS      ns44.domaincontrol.com.

;; ADDITIONAL SECTION:
ns43.domaincontrol.com. 2008    IN      A       208.109.78.180
ns44.domaincontrol.com. 3341    IN      A       208.109.80.75

;; Query time: 240 msec
;; SERVER: 202.14.67.4#53(202.14.67.4)
;; WHEN: Mon Nov 12 22:36:20 2007
;; MSG SIZE  rcvd: 129

satimis@#ubuntu
```


Please advise how to fix the problem.  TIA


B.R.
satimis

---

