---
title: "How to use sshd"
date: 2007-12-20
forum: Networking &amp; Wireless
---

### Post by gil michael on 2007-12-20
Hi,
i have ubuntu 6.10 and i installed "openssh-server".
I want my friends to be able to connect my computer and download/ upload files.
I have already defined their user names and passwords.

How can i start the server? how can i tell them my ip address? what are the basic commands to handle this job?

Gil

---

### Post by stalker145 on 2007-12-20
> **gil michael said:**
> Hi,
i have ubuntu 6.10 and i installed "openssh-server".
I want my friends to be able to connect my computer and download/ upload files.
I have already defined their user names and passwords.

How can i start the server? how can i tell them my ip address? what are the basic commands to handle this job?

Gil

If you've already configured and enabled the username/passwords for your users, it's all ready to go as the server starts automatically when the computer boots.

Finding your IP address (public WAN) can be done by going to some site, somewhere, that offers the service. I Google'd it and found [http://whatismyipaddress.com/](http://whatismyipaddress.com/) which seems to be working. But then again, I'm not on my network, so I don't know. If you're trying to find your private LAN IP, you can open a terminal and type ```
ifconfig
```

Basic commands can be found by typing ```
man ssh
``` into the terminal. Personally, I only ever use ```
ssh -X IP.add.re.ss program-name
ssh IP.add.re.ss
and
ssh user@IP.add.re.ss
```
Check back if you have more questions.

---

### Post by Whiffle on 2007-12-20
You can also do:

sftp://username@IP.add.re.ss 

in nautilus or konqueror and it will allow you to do drag'n drop file moving.

---

### Post by stalker145 on 2007-12-20
> **Whiffle said:**
> You can also do:

sftp://username@IP.add.re.ss 

in nautilus or konqueror and it will allow you to do drag'n drop file moving.

NICE! 

I'm at work right now, so I must ask... do you need an FTP server set up already? Are you inputting sftp into the Nautilus addess or into the CLI (assuming Nautilus).

---

