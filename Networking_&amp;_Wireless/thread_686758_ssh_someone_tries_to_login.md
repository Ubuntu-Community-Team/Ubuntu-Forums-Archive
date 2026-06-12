---
title: "ssh: someone tries to login"
date: 2008-02-03
forum: Networking &amp; Wireless
---

### Post by borobudur on 2008-02-03
My log file tells me that someone from outside tries to login to my ssh server:

```
Feb  3 16:35:13 jawa sshd[5891]: pam_unix(ssh:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=190.84.50.137 
Feb  3 16:35:15 jawa sshd[5891]: Failed password for invalid user shell from 190.84.50.137 port 47935 ssh2
Feb  3 16:35:17 jawa sshd[5940]: reverse mapping checking getaddrinfo for static-ip-cr1908450137.cable.net.co [190.84.50.137] failed - POSSIBLE BREAK-IN ATTEMPT!
Feb  3 16:35:17 jawa sshd[5940]: Invalid user linux from 190.84.50.137
```Is that a reason to worry about?

---

### Post by psyburn on 2008-02-03
Yes it is a problem however it should not worry you in that particular case.
He failed to login. However these attempts have not stopped in the last year that I have had a Linux router box.

Many things were suggested when I looked around the internet for info on how to stop it.
Some suggested changing the port number from 22 to something else above port 1024 (security by obscurity, bleh)
Others suggested disabling password logins and only using RSA key authenitcation. (can be inconvenient)
I found an option for /etc/ssh/sshd.conf called AllowUsers *usernames* because I have 3 login names who ssh in this works great (note: all of these names are not in the dictionary and root is not one of them

I use AllowUsers, PermitRootLogin no, and use RSA keys.

On top of this protect my own ssh systems I use **denyhosts**

```
Terminal:
sudo apt-get install denyhosts
```

I then edit /etc/denyhosts.conf and enable synchronization to get the list of other known bad hosts
That gets them rejected right away, like so in the logs:
```
/var/log/auth.log:
Feb  2 18:21:17 notnervhq sshd[7941]: refused connect from ::ffff:65.125.141.91 (::ffff:65.125.141.91)

```

Mind you, it is a blacklisting program and you could blacklist yourself

To make sure I don't accidentally blacklist myself on my LAN I added
```
/etc/hosts.allow:
sshd: 10.0.0.0/8 
```
since I use different parts of the 10. private LAN block
another common one would be 
```
/etc/hosts.allow:
sshd: 192.168.X.0/24
```
X you'll have to replace with 0 or 1 or sometimes 2
But this only applies to a box your using on your LAN and not a colo box some where else

---

### Post by HermanAB on 2008-02-03
Yup, this goes on all the time.  See this: [http://aeronetworks.ca/ssh-kiddies.html](http://aeronetworks.ca/ssh-kiddies.html)

BTW, all security is obscurity.  Some methods are just more obscure than others.

Cheers,

Herman

---

### Post by borobudur on 2008-02-06
Thanks to psyburn and HermanAB!

I turned it off at the moment but I will convert some of the suggestions as soon as I'll find the time for it.

Cheers!

---

