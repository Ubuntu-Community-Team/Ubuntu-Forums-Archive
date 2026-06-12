---
title: "Best way to protect linux server - Paranoid"
date: 2009-12-17
forum: New to Ubuntu
---

### Post by mamut0o1 on 2009-12-17
Hello; I just finished setting up a webserver on my linux machine. I have also a router from which I allow web access to my box and shh protocol. How can I make sure no other ports are listening? what would be best to block any other traffic;
any other recomendations will be appreciated.

Thanks!

---

### Post by lewisforlife on 2009-12-17
`

---

### Post by lewisforlife on 2009-12-17
> I have also a router from which I allow web access to my box and shh protocol.


Are you logging into your SSH with a password?  If so, that is not a safe option, it is very susceptible to brute force attacks.  Use RSA keys to authenticate to your SSH server if you have not already.  Check out [https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)


(Edit:  Sorry for the multiple post, don't know how this happened, I was trying to edit my previous message.)

---

### Post by bodhi.zazen on 2009-12-17
Well, you are asking a broad question.

I suggest you start with the stickies at the top of the security section :

[Ubuntu Security - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=510812") 

And if you wish, snort + OSSEC + possibly Apparmor.

for you ssh server, use keys, disable passwords, and user at either fail2ban or denyhosts.

apache alone is fairly secure, but as you add modules, such as php, then you could have problems, so it depends on your content.

You can add mod_evasive and mod_security if you wish.

Last, take a look at IPTables

[http://bodhizazen.net/Tutorials/iptables/index.html](http://bodhizazen.net/Tutorials/iptables/index.html)

---

### Post by mamut0o1 on 2009-12-17
> **lewisforlife said:**
> Are you logging into your SSH with a password?  If so, that is not a safe option, it is very susceptible to brute force attacks.  Use RSA keys to authenticate to your SSH server if you have not already.  Check out [https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)


(Edit:  Sorry for the multiple post, don't know how this happened, I was trying to edit my previous message.)

I'm currently using a password..but I was thinking if I could set it up so only can be access by one IP.
I will check the guide you sent me.

Thanks; let me know what you think

---

### Post by mamut0o1 on 2009-12-17
> **bodhi.zazen said:**
> Well, you are asking a broad question.

I suggest you start with the stickies at the top of the security section :

[Ubuntu Security - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=510812") 

And if you wish, snort + OSSEC + possibly Apparmor.

for you ssh server, use keys, disable passwords, and user at either fail2ban or denyhosts.

apache alone is fairly secure, but as you add modules, such as php, then you could have problems, so it depends on your content.

You can add mod_evasive and mod_security if you wish.

Last, take a look at IPTables

[http://bodhizazen.net/Tutorials/iptables/index.html](http://bodhizazen.net/Tutorials/iptables/index.html)

How secure is to setup deny access to directories and files with apache? 

Can IpTables secure a linux server as a firewall? or Do I still need a firewall?

thank you for your reply.

---

### Post by bodhi.zazen on 2009-12-17
Setting access in Apache is one of several layers of security.

iptables is your firewall (technically iptables is a front end to netfilter).

---

### Post by lewisforlife on 2009-12-18
> **mamut0o1 said:**
> I'm currently using a password..but I was thinking if I could set it up so only can be access by one IP.
I will check the guide you sent me.

Thanks; let me know what you think

The only problem with setting it up so only 1 IP can access it is that if you take your laptop to a friends house, or somewhere else, you will be at a different IP address and will not be able to access your server.

---

### Post by ukripper on 2009-12-18
For me fail2ban has been must-have on the server after the firewall.

you can simply install from ubuntu repos
```
sudo apt-get install fail2ban
```

copy to jail.local
```
sudo cp -v /etc/fail2ban/jail.conf /etc/fail2ban/jail.local
```

Edit jail.local not jail.conf
```
sudo vi /etc/fail2ban/jail.local
```

After editing the services you want fail2ban to monitor, then restart the service.
```
sudo /etc/init.d/fail2ban restart
```

that's it fail2ban is ready to watch like a hawke for any DOS attacks.

---

### Post by lavinog on 2009-12-18
> **mamut0o1 said:**
> shh protocol.

That would be an awesome name for a protocol.

---

### Post by mamut0o1 on 2009-12-18
> **lavinog said:**
> That would be an awesome name for a protocol.

I agree; I invented the name for it  :)

---

### Post by mamut0o1 on 2009-12-18
> **ukripper said:**
> For me fail2ban has been must-have on the server after the firewall.

you can simply install from ubuntu repos
```
sudo apt-get install fail2ban
```

copy to jail.local
```
sudo cp -v /etc/fail2ban/jail.conf /etc/fail2ban/jail.local
```

Edit jail.local not jail.conf
```
sudo vi /etc/fail2ban/jail.local
```

After editing the services you want fail2ban to monitor, then restart the service.
```
sudo /etc/init.d/fail2ban restart
```

that's it fail2ban is ready to watch like a hawke for any DOS attacks.

That's neat; I will install it; Thank you all

---

### Post by CoolDreamZ on 2009-12-22
I was looking for this solution (lots of brute force attacks in /var/log/auth.log).

Works perfectly, thank-you very much!

---

### Post by ukripper on 2009-12-22
If anyone looking for vieweing logs via email without using a mailserver. Try my guide here [http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1279054](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1279054)
this works with 8.04 and 9.04 server and desktops. For 9.10 there is a slight change. If someone looking to install logwatch and sendemail on 9.10 server, i can help you with it. I have recently built NAS server on 9.10 and included logwatch setup on it.

---

