---
title: "Server or netbook edition?"
date: 2009-12-16
forum: New to Ubuntu
---

### Post by tabish007 on 2009-12-16
Hi,

I want to install Ubuntu on a machine which will be used as a localhost. I will install Apache, php, mysql and will run it as local server.

What edition do i need to choose? ubuntu server ot netbook?

Regards

---

### Post by jamieleshaw on 2009-12-16
You need Server Edition, a netbook is a type of ultra-portable laptop deigned for browsing the Internet.

---

### Post by tom.swartz07 on 2009-12-16
> **tabish007 said:**
> Hi,

I want to install Ubuntu on a machine which will be used as a localhost. I will install Apache, php, mysql and will run it as local server.

What edition do i need to choose? ubuntu server ot netbook?

Regards

Ideally, you would use the server edition, and then install the ubuntu-desktop package once you get it up and running. this will give you a visual desktop to use, rather than command line everything.

good luck!

---

### Post by plusnplus on 2009-12-16
Hi tabish007,
server edition come without gui interface. if you not familiar with command text, it is better you install desktop edition.
after finish installation, you can install more application you need it.

---

### Post by tabish007 on 2009-12-16
> **plusnplus said:**
> Hi tabish007,
server edition come without gui interface. if you not familiar with command text, it is better you install desktop edition.
after finish installation, you can install more application you need it.

Ok.. you are right.. I am not used to with the command line interface. So if I am going to use the desktop edition, will I be able to install apache and all and will LAN and file sharing works in this as well?

Thank you

---

### Post by jamieleshaw on 2009-12-16
> **tabish007 said:**
> Ok.. you are right.. I am not used to with the command line interface. So if I am going to use the desktop edition, will I be able to install apache and all and will LAN and file sharing works in this as well?

Thank you
Yes, they will! ;)

---

### Post by Temposs on 2009-12-16
You can install everything just fine with the desktop edition. People who use the Server Edition on a machine(like me) want a machine that isn't using any more cpu cycles than necessary(from having a GUI running) and just does what's needed as fast as possible. But, I've also previously set up a desktop edition as a server and it was also very easy and runs just fine.

---

### Post by 3rdalbum on 2009-12-16
The Server edition is for people who know what they are doing with Ubuntu. The netbook edition is for netbook computers, funnily enough :-P

Just install the Desktop edition and use the command:

```
sudo tasksel lamp-server
```

in the terminal application to install the Apache, MySQL and PHP packages. Or install them from Synaptic Package Manager.

The Desktop edition is pretty much just the server edition, but with a slightly different kernel and a Graphical User Interface.

---

### Post by plusnplus on 2009-12-16
just curios,
in server edition, is by default apache already installed or still need to be install?

---

### Post by lukeiamyourfather on 2009-12-16
> **plusnplus said:**
> just curios,
in server edition, is by default apache already installed or still need to be install?

Apache can be installed along with the server, just select the web server packages during the server installation. If you're not sure you can always try it first in a virtual machine using something like VirtualBox (which is free and has an open source version). Cheers!

---

