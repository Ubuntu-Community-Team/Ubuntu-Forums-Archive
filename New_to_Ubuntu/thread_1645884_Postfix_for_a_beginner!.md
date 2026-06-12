---
title: "Postfix for a beginner!"
date: 2010-12-15
forum: New to Ubuntu
---

### Post by nahallac on 2010-12-15
I am setting up my first Linux server, and am muddling my way through learning the basics (I've started another thread with some starter questions).
 
I have chosen one initial purpose for my server, to act as an internal smtp relay as a frontend for my Exchange 2010 server. Whenever using a new product I find I can only learn if I fully understand terminology, so I was wondering if I could get some help?
 
The postmap command to create Postfix maps seems to crop up a lot. In very lay terms, what is a Postfix map and what purpose does it serve?
 
I'd also like to know what a hash: or ldap: staement is? From what I understand it is part of a database table, is that far wrong?
 
Sorry for the basic questions, it's just that the documentation I have been reading assumes an understanding of Linux I don't yet have. I'm humble enough to make myself look a bit silly as long as I learn!

---

### Post by Gone fishing on 2010-12-15
The howtoforge perfect server tutorials are usually quite good 

[http://www.howtoforge.com/perfect-server-ubuntu-10.04-lucid-lynx-ispconfig-3](http://www.howtoforge.com/perfect-server-ubuntu-10.04-lucid-lynx-ispconfig-3)

ldap is an authentication database system for Linux. I use it on my sever as a backend for samba, Linux client authentication, postfix and squid.

Here's a couple more links

[https://help.ubuntu.com/10.04/serverguide/C/openldap-server.html](https://help.ubuntu.com/10.04/serverguide/C/openldap-server.html)
[https://help.ubuntu.com/10.04/serverguide/C/samba-ldap.html](https://help.ubuntu.com/10.04/serverguide/C/samba-ldap.html)

---

### Post by nahallac on 2010-12-15
Sorry, I should say that I am aware of LDAP. I was just using that as an example of a statement followed by a colon. In Postfix I see this a lot in how tos:
 
[FONT=Courier New]hash:/etc/postfix/virtual[/FONT]

Thank you for the ISPConfig and general server guide, but at the moment I am looking to just run a pretty plain box with nothing but Postfix on top and then go from there. I'm not into the idea of running any GUI frontend as I'm trying to learn Linux the 'pure' way!
 
I have set the basics in my main.cf, and have commented out local in the master.cf as I have Exchange as my MUA. I'm looking to go from there... An understanding of what I mentioned in my first paragraph will help, as I believe it's tied in with dragging in the users from Exchange.
 
I also see the concept of post maps a lot, can anyone give me a lay explanation?

---

### Post by nahallac on 2010-12-15
Sorry to bump this, but I'm keen to have a bit of dialogue on this topic! There's only so much I can interpret when simply reading blogs and tutorials, I need a real life human to interact with...

---

### Post by Gone fishing on 2010-12-16
This might be of interest

> The postfix main.cf configuration file can specify the location of several small database files (the "maps"):
virtual_alias_maps =
        hash:/etc/postfix/virtual

transport_maps =
        hash:/etc/postfix/transport

relay_domains =
        $mydestination,
        $mydomain,
        hash:/etc/postfix/relays
...
and so on. These are "hash" maps that are that are maintained in Berkeley DB format (there are other map formats, but we're not addressing them here). The files are maintained in regular text format, then "compiled" into the DB format with the postmap command, which is provided with Postfix.

from [http://unixwiz.net/techtips/postfix-makefiles.html](http://unixwiz.net/techtips/postfix-makefiles.html)

When I did my sever I used the perfect server guides and missed out the ISPConfig stuff. I seem to remember (I didn't use Ubuntu) that the postfix needed Amavis - I hadn't installed it a couldn't work out why Postfix was using this odd port for several hours

---

### Post by nahallac on 2010-12-16
Thank you, that certainly is of interest. That page is EXACTLY what I've been looking for!
 
I will look into Amavis, as obviously running a plain Postfix configuration with no mail checking or filtering is a bit iffy.
 
I will continue with my config tonight and report back...

---

### Post by nahallac on 2010-12-16
.

---

### Post by nahallac on 2010-12-16
Ok, so I now understand the concept of a Postfix map, and that it uses a Berkely DB format file as the basis for it. However, why in main.cf does the path to the map (for example virtual_alias_maps) have to have the hash:/ prefix? Why can't you just put the path to the .db file? Does Postfix need to know that they are hash files?
 
I am also going to manually create my relay_recipient map at first. How would I format the file? Would I have email address on the LHS, and any old entry on RHS to meet the required format?

---

### Post by nahallac on 2010-12-18
Anyone have any input on how to manually create the relay recipient map?
 
I was also looking for recommendations as to how to route mail to my Exchange server from Postfix. Do people generally use internal MX records, or edit the transport map (I believe that's the right method of statically routing it)?

---

### Post by stmiller on 2010-12-18
> **nahallac said:**
> Anyone have any input on how to manually create the relay recipient map?
 


Yes. You create a text file /etc/postfix/relay_recipients and put in something like this:

```
user@example.com   OK
```


Then you can do:

```
postmap hash:/etc/postfix/relay_recipients
```

which will generate the relay_recipients.db


[http://www.postfix.org/documentation.html](http://www.postfix.org/documentation.html)

:)

---

### Post by nahallac on 2010-12-18
Thank you, I just didn't know if there were formatting requirements for the text file? For example, does it have to be a space or tab between the LHS and RHS?
 
Sorry if these are basic questions, I'm still new to Linux!

---

### Post by nahallac on 2010-12-19
I've noticed something else looking through mail.log in /var/log. There are messages there about failed connections to my internal domain:
 
Dec 19 12:50:07 postfix-hostname postfix/smtp[20882]: 07A68220E66: to=<username[EMAIL="username@child.domain.co.uk"]@child.domain.co.uk[/EMAIL]>, relay=none, delay=132212, delays=132191/0.02/21/0, dsn=4.4.1, status=deferred (connect to child.domain.co.uk[x.x.x.x]:25: Connection timed out)
 
Why would that be? I don't have anything in my Postfix config that I know of that points to my internal domain, all the entries are for my externally hosted domain (which is a parent of my internal one).

---

### Post by Gone fishing on 2010-12-21
Let me also recommend Webmin  [http://www.webmin.com/](http://www.webmin.com/) has a nice postfix module. Makes things easier - but you then need to run Apache on the server

---

