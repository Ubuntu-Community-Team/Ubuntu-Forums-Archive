---
title: "[SOLVED] Adding local domains to postfix"
date: 2009-01-02
forum: New to Ubuntu
---

### Post by gerreth on 2009-01-02
Hi,

I have the domain gerreth.intern configured on my computer.
Tried to connect this to courier-imap.

I used this guide: [https://help.ubuntu.com/community/PostfixBasicSetupHowto](https://help.ubuntu.com/community/PostfixBasicSetupHowto)

This is what i told my computer to do:

```
sudo postconf -e "gerreth.intern = mail.gerreth.intern, localhost.localdomain, localhost, gerreth.intern"
```

```
sudo postconf -e "gerreth.intern = 127.0.0.0/8, 192.168.1.0/24"
```
I checked my ip, this step can't be wrong.

```
sudo postconf -e "inet_interfaces = all"
```

```
sudo  /etc/init.d/postfix restart
```
He says everything is alright...

```
netcat mail.yourdomain.com 25

```
Gives this error:
forward host lookup failed: Unknown host :  Connection timed out

I really cant find the place i screwed it,

Thx for reading/helping!
.
Gerreth

---

### Post by gerreth on 2009-01-03
Please :KS

---

### Post by albinootje on 2009-01-03
> **gerreth said:**
> 

```
netcat mail.yourdomain.com 25

```
Gives this error:
forward host lookup failed: Unknown host :  Connection timed out


mail.yourdomain.com should be replaced by your domain, gerreth.intern
```
netcat gerreth.intern 25

```

But how did you set up your own domain ?
Did you install and configure a local DNS-server like Bind or DjbDNS ?
Or did you just change /etc/hostname and /etc/hosts ?

And, I assume you want to have postfix for in- and out-going emails, right ?

---

### Post by gerreth on 2009-01-03
> **albinootje said:**
> mail.yourdomain.com should be replaced by your domain, gerreth.intern
```
netcat gerreth.intern 25

```

But how did you set up your own domain ?
Did you install and configure a local DNS-server like Bind or DjbDNS ?
Or did you just change /etc/hostname and /etc/hosts ?

And, I assume you want to have postfix for in- and out-going emails, right ?


I have bind and ldap succesfully running. Postfix is running aswell.(i can send emails from root@localost to someoneelse@localhost, so that should be ok) I typed that last line wrong, i used:

```
netcat mail.gerreth.intern 143
```

---

### Post by albinootje on 2009-01-03
> **gerreth said:**
> I have bind and ldap succesfully running. Postfix is running aswell.(i can send emails from root@localost to someoneelse@localhost, so that should be ok) I typed that last line wrong, i used:

```
netcat mail.gerreth.intern 143
```

Okay, good :)

Sort out your "port 25 to the outside" problem.
Are you using firewall software on your Ubuntu machine and/or router/modem ?

---

### Post by gerreth on 2009-01-03
> **albinootje said:**
> Okay, good :)

Sort out your "port 25 to the outside" problem.
Are you using firewall software on your Ubuntu machine and/or router/modem ?

I had ufw installed, but turned it off now. I have to go now :( but i'll check.

---

### Post by gerreth on 2009-01-03
Checked the router, IMAP and POP3 are allowed.

I configured it for IMAP, so the router can't be the problem =/

Any suggestions?

---

### Post by albinootje on 2009-01-03
> **gerreth said:**
> Checked the router, IMAP and POP3 are allowed.

I configured it for IMAP, so the router can't be the problem =/

Any suggestions?

Is SMTP allowed on your router ?

Make sure you do some reading about "open relay" in general and for Postfix specifically , since you're new to this. 
It's important to not give spammers any chance to abuse your mail-server.

---

### Post by gerreth on 2009-01-03
> **albinootje said:**
> Is SMTP allowed on your router ?

Make sure you do some reading about "open relay" in general and for Postfix specifically , since you're new to this. 
It's important to not give spammers any chance to abuse your mail-server.

Sorry forgot to mention, SMTP is allowed.

I used the manuals at [https://help.ubuntu.com/](https://help.ubuntu.com/)

- [https://help.ubuntu.com/community/BIND9ServerHowto](https://help.ubuntu.com/community/BIND9ServerHowto)
- [https://help.ubuntu.com/community/OpenLDAPServer](https://help.ubuntu.com/community/OpenLDAPServer)
- [https://help.ubuntu.com/community/Courier](https://help.ubuntu.com/community/Courier)
- [https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix)

Bind was easy, Ldap was harder and courier and postfix are quite difficult, not to mention need to find out all about horde.

Do you perhaps have other good guides for courier/postfix/horde?

I checked a lot of sites on the web and they al have different syntax :o *confused*

Thx

---

### Post by albinootje on 2009-01-03
Okay!
Well, if you don't mind removing courier-imap and horde completely, then I recommend : dovecot-imap + squirrelmail
Much easier to install/configure/maintain, and more flexible imho.

Mailservers that I use for years now, are loosely based on howtos like this :

[http://rimuhosting.com/support/settingupemail.jsp?mta=postfix](http://rimuhosting.com/support/settingupemail.jsp?mta=postfix)
[http://wiki.dovecot.org/HowTo/DovecotLDAPostfixAdminMySQL](http://wiki.dovecot.org/HowTo/DovecotLDAPostfixAdminMySQL)

See also :
[http://wiki.dovecot.org/HowTo/DovecotOpenLdap?action=show&redirect=DovecotOpenLdap](http://wiki.dovecot.org/HowTo/DovecotOpenLdap?action=show&redirect=DovecotOpenLdap)

---

### Post by gerreth on 2009-01-04
> **albinootje said:**
> Okay!
Well, if you don't mind removing courier-imap and horde completely, then I recommend : dovecot-imap + squirrelmail
Much easier to install/configure/maintain, and more flexible imho.


I'm not free to choose what packages I use to fully configure the server, but when this project is done I will take a look at dovecot and squirrelmail :)

Thx for the links

---

