---
title: "How do I test PHP with LAMP?"
date: 2010-07-01
forum: New to Ubuntu
---

### Post by TheAdamJanes on 2010-07-01
Hello,
I just downloaded LAMP and I've been able to add and edit folders in my var/www folder with the "gksu nautilus" command. But, when I test the php files in localhost I get this message:

**Forbidden**

 You don't have permission to access /Form_IP2/myTest.php on this server.
  Apache/2.2.14 (Ubuntu) Server at localhost Port 80


How do I test my PHP?

---

### Post by NikoC on 2010-07-01
I think this looks like a nice guide:
[http://blogote.com/2010/ubuntu/how-to-install-apache-2-on-ubuntu-10-04-with-php5-and-mysql-support-guide.html]("http://blogote.com/2010/ubuntu/how-to-install-apache-2-on-ubuntu-10-04-with-php5-and-mysql-support-guide.html")

Good luck!

Niko

---

### Post by lkjoel on 2010-07-01
> **TheAdamJanes said:**
> Hello,
I just downloaded LAMP and I've been able to add and edit folders in my var/www folder with the "gksu nautilus" command. But, when I test the php files in localhost I get this message:

**Forbidden**

 You don't have permission to access /Form_IP2/myTest.php on this server.
  Apache/2.2.14 (Ubuntu) Server at localhost Port 80


How do I test my PHP?
First of all, just remember, instead of
```
gksu nautilus
```
try
```
gksu nautilus --no-desktop --browser
```
And on /var, go to www's properties.
Be sure that everything is Read and Write.
Hope that helps!

---

### Post by bodhi.zazen on 2010-07-01
> **lkjoel said:**
> First of all, just remember, instead of
```
gksu nautilus
```try
```
gksu nautilus --no-desktop --browser
```And on /var, go to www's properties.
Be sure that everything is Read and Write.
Hope that helps!

On apache, I keep files owned by root, group www-data , and permissions of 440 (ro).

I would advise against permissions of 666.

---

### Post by lkjoel on 2010-07-02
Yes, you are right.
But if someone has a computer only to his/her own self, does it matter?
Sure a hacker can come in and do big damage, but can't the hacker change permissions?
Thanks in advance!

---

### Post by bodhi.zazen on 2010-07-02
> **lkjoel said:**
> Yes, you are right.
But if someone has a computer only to his/her own self, does it matter?

Yes, it matters. If your computer is connected to the internet you are not the only user, more so with servers.

> Sure a hacker can come in and do big damage, but can't the hacker change permissions?
Thanks in advance!

Apache runs as a restricted user, www-data on Ubuntu. So if apache / php is compromised, and your files are world writable, permissions of 666 , game over -> Defaced wed site.

Same if mysql is compromised and on ...

If your files are owned by root:www-data , with permissions of 440, and apache, one needs to first compromise apache (or mysql) and then gain root privileges. This escalation of privileges will be much more difficult with apparmor running (you do run apparmor on your web server I hope ... )

So yes, permissions of 666 or 777 on files served by a LAMP stack is considered to be inappropriate by most everyone with any interest in security.

Unless you want your web site defaced, don't do it. Of course you are a small fish if you are simply running a simple web site at home, but still, I am sure someone somewhere would like to yank your chain.

---

### Post by bodhi.zazen on 2010-07-02
Another example, firefox runs as your user and thus can not change files in /etc or /usr or /bin , so , yes, Linux permissions are critical for security even though you may feel you are the "only user" on the system.

---

### Post by lkjoel on 2010-07-02
Ok thanks a lot bodhi.zazen!
I will change my /var/www settings.
Is there any firewalls that work under linux and is free?_****_[[COLOR=#980101]****[/COLOR]]("http://ubuntuforums.org/member.php?u=89054")

---

### Post by bodhi.zazen on 2010-07-02
> **lkjoel said:**
> Ok thanks a lot bodhi.zazen!
I will change my /var/www settings.
Is there any firewalls that work under linux and is free?

UFW / GUFW

    [http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/](http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/)
    [http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/](http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/)
    [http://blog.bodhizazen.net/linux/firewall-ubuntu-servers/](http://blog.bodhizazen.net/linux/firewall-ubuntu-servers/)

---

