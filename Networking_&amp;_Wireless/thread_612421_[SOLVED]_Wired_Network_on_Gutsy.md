---
title: "[SOLVED] Wired Network on Gutsy?"
date: 2007-11-13
forum: Networking &amp; Wireless
---

### Post by Dark Aspect on 2007-11-13
Hi

I have a problem with gutsy thats kind of fixed but I was wanting an shortcut if there was one.Every time I boot my system in order for my wired network to work I must go to system/administration/network and manually enter the following under my DNS settings:

> 208.67.222.222
208.67.220.220

I was curious to know if some one who has this problem found a shortcut so I would not have to do this every time I restart my system.Thank in advance for any replies.

---

### Post by Digitallysick on 2007-11-13
do you have a router?  or are you directly connected to your modem?  Your modem should "give" you the dns settings , but if not, you can setup your router to use whatever dns you program, i use open dns. Your talking about broadband correct? (high speed dsl/cable)

---

### Post by Dark Aspect on 2007-11-14
> **Digitallysick said:**
> do you have a router?  or are you directly connected to your modem?  Your modem should "give" you the dns settings , but if not, you can setup your router to use whatever dns you program, i use open dns. Your talking about broadband correct? (high speed dsl/cable)
I am using a broadband connection directly connected to a D-Link ADSL modem.My internet works fine I was just wanting to skip having to edit my network DNS every time I boot up. 

Open DNS?Is that an application from the repositories?

---

### Post by Dark Aspect on 2007-11-14
Bump........

Not trying to annoy but I was wanting to see if anyone else knew of a possible shortcut.Since I had made this post late at night I thought it might have been missed by a few people.

---

### Post by infurnus on 2007-11-15
See if this doesnt help
```

sudo cp /etc/resolv.conf /etc/resolv.conf.backup
sudo nano /etc/resolv.conf

```
enter the following details test.com is where you would put in your host name for your ISP.
```

search test.com
nameserver 208.67.220.220
nameserver 208.67.222.222

```
For instance mine is:
```

search tu.ok.cox.net
nameserver 208.67.220.220
nameserver 208.67.222.222

```
I also have this setup in the linksys router.

---

### Post by Dark Aspect on 2007-11-15
> **infurnus said:**
> See if this doesnt help
```

sudo cp /etc/resolv.conf /etc/resolv.conf.backup
sudo nano /etc/resolv.conf

```
enter the following details test.com is where you would put in your host name for your ISP.
```

search test.com
nameserver 208.67.220.220
nameserver 208.67.222.222

```
For instance mine is:
```

search tu.ok.cox.net
nameserver 208.67.220.220
nameserver 208.67.222.222

```
I also have this setup in the linksys router.

That worked wonders,thanks.My network it working flawlessly now.

---

