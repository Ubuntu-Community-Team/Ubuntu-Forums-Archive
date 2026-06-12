---
title: "linux command"
date: 2011-06-21
forum: New to Ubuntu
---

### Post by sireesha on 2011-06-21
I am new to linux and ubuntu as well. 
I would like to know what will be the result of this command:
 
lsb_release -a; cat /etc/resolv.conf

thank u

---

### Post by Thewhistlingwind on 2011-06-21
[http://linux.die.net/man/1/lsb_release](http://linux.die.net/man/1/lsb_release)

Seems harmless enough.

In the future, to get information about a command use:

man command

Replace command with your desired utility.

---

### Post by amauk on 2011-06-21
It will output the release information for your system and the DNS information (where your machine goes to translate domain names to IP addresses)

Output on my machine is

**lsb_release -a**```
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu oneiric (development branch)
Release:	11.10
Codename:	oneiric
```**cat /etc/resolv.conf**```

domain config
search config
nameserver 192.168.1.254
```

---

### Post by nothingspecial on 2011-06-21
Never don't ask if you are not sure.

You did the right thing.

---

### Post by iclestu on 2011-06-21
> **amauk said:**
> 
Output on my machine is

**lsb_release -a**```
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu** oneiric** (development branch)
Release:    11.10
Codename:    **oneiric**
```

Coool!

Now, since we are in the presence of greatness can I put my personal request that 12.04 is codenamed plucky penguin or something in honour of tux who hardly gets a lookin these days with all distros (and even releases) having thier own mascots/branding!

OP- Please forgive me hijacking your thread with trivialities!

---

### Post by amauk on 2011-06-21
> **iclestu said:**
> Now, since we are in the presence of greatnessI'm just a user not an Ubuntu developer, so I'm not sure I deserve that title...

> **iclestu said:**
> can I put my personal request that 12.04 is codenamed plucky penguin or something in honour of tux who hardly gets a lookin these days with all distros (and even releases) having thier own mascots/branding!I am, however, a Sysadmin
and 12.04 will be an LTS release so it'll be used on a lot of servers and still supported in 2017. For that reason, I'm personally pushing for Pungent Porpoise

---

