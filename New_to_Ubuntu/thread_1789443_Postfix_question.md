---
title: "Postfix question"
date: 2011-06-23
forum: New to Ubuntu
---

### Post by dan40 on 2011-06-23
Hi, I'm a relative newbie to Ubuntu server, but I have all of these up and running successfully with one exception:

- Ubuntu server
- ssh
- Squirrelmail
- Webalizer
- phpmyadmin
- Mysql
- Postfix
- Dovecot, POP3, IMAP, sasl
- Clam Antivirus
- Webmin

Now, that being said, with regard to email, I use Postfix but I have a really annoying problem:  I can send email to  and from addresses in my local network, and I can send email from outside my network to an address in in my local network, BUT, I cannot send email from my local network to an external email address and it's frustrating the heck out of me.

I know it's just a matter of tweaking one line in a config file, but I'm not sure which one to tweak.  I've followed the configuration documentation to the letter but this one little piece keeps me from getting the full benefit.

Could anyone please suggest what the problem might be?  I can post my config files if necessary.

Thanks,
Dan

---

### Post by ruffEdgz on 2011-06-23
When you look at your /etc/postfix/main.cf file, what is your relayhost variable set as?
```

grep "relayhost" /etc/postfix/main.cf

```
This variable helps your postfix with the next hop for non-local sending of email. If you leave the variable blank, it will find the closest mx record to use to send out emails.

Postfix reading on 'relayhost': [http://www.postfix.org/postconf.5.html#relayhost](http://www.postfix.org/postconf.5.html#relayhost)

---

### Post by dan40 on 2011-06-23
Hi ruffEdgz, it's currently set to:
 
relayhost =
 
It's blank... doesn't that mean "do not relay"?

---

### Post by ruffEdgz on 2011-06-24
From my understanding of the relayhost, leaving it blank will cause postfix to look for the MX record of an email is needs to send. Placing anything in there will bypass that look up. I couldn't find any documentation from postfix's site but I did find an example of using the 'relayhost =' in the link provided (and it helps with sending emails internally and externally): [http://www.postfix.org/STANDARD_CONFIGURATION_README.html#intranet](http://www.postfix.org/STANDARD_CONFIGURATION_README.html#intranet)

Also, you might want to make sure you ISP will allow out going traffic through port 25 (if that is the port you are using) as some ISP's will block that by default. You might want to talk to them or find any documentation on their site about sending email.

Just have some other questions:
[list]
[*]Are you using transport_maps variable?
[*]Are you using inet_interfaces variable and whats the value?
[/list]
**Just FYI**: when I was making my first smtp server, the three main variables I had to make sure worked was:
---
inet_interfaces
relayhost
transport_maps (optional)
---
Hope this helps.

---

