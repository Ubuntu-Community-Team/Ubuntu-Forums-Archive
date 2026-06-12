---
title: "sendmail mail() ubuntu"
date: 2008-07-06
forum: Networking &amp; Wireless
---

### Post by danilevsky on 2008-07-06
Hi guys!
I have a problem with sendmail and php function mail()
so, i've installed sendmail
```
sudo aptitude install sendmail
sudo aptitude install nmap 
```

checking 25 port:
```
dmitry@danilevsky:~$ nmap -sT localhost

Starting Nmap 4.53 ( http://insecure.org ) at 2008-07-06 21:13 EEST
Interesting ports on drupal (127.0.0.1):
Not shown: 1707 closed ports
PORT    STATE SERVICE
22/tcp  open  ssh
25/tcp  open  smtp
80/tcp  open  http
139/tcp open  netbios-ssn
445/tcp open  microsoft-ds
587/tcp open  submission
631/tcp open  ipp

Nmap done: 1 IP address (1 host up) scanned in 0.179 seconds
```

my /etc/php5/apache2/php.ini:
```
sendmail_path = /usr/sbin/sendmail -t -i
```

and finaly my php script:
```
  1 <?php
  2 if(mail('my@mail.com', 'subject', 'text')) {
  3     print 'sent';
  4 }
  5 else {
  6     print 'failed';
  7 }
  8 ?>
```

This code returns sent., but no email in my mail...

/var/log/apache2/error.log is empty

What can be the problem?

---

