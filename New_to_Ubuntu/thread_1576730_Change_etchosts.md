---
title: "Change etc/hosts"
date: 2010-09-17
forum: New to Ubuntu
---

### Post by Gameboyman99 on 2010-09-17
Hi, new guy here so I might need a walkthrough on this:

I'm trying to change my computer name so I searched and found how, but everyone's saying how to change etc/hosts too. Here's what my file has, and I want to change the name/hostname from "ubuntu" to "Newby1":

[B]127.*.*.*    localhost
127.*.*.*    ubuntu.ubuntu-domain    ubuntu

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
[/B]
Um, I really hope none of this is private, like my IP, maybe(The "*'s" are in place of part of my IP)
I'm guessing that if I change the "ubuntu" by itself it will give me an error/crash??

Thx,
        Gameboyman99

---

### Post by cariboo on 2010-09-17
This is what my hosts file looks like:

```
cat /etc/hosts
192.168.1.215	chilanko-maverick	# Added by NetworkManager
127.0.0.1	localhost.localdomain	localhost
**127.0.1.1**	chilanko-maverick
192.168.1.250	willy
192.168.1.235	puntzi
192.168.1.245	mcleese
192.168.1.225	alexis
```

I have bolded the ip address you want to change. you also have to change /etc/hostname, you can do that by typing at the prompt:

```
sudo hostname Newby1
```

The changes won't take place until you've rebooted.

Those 127.X.X.X are just loopback addresses, everyone has those, they are non-routable. The 192.168.X.X are also private ip addresses and are non-routable. Non-routable means they can't be accessed from the internet.

---

### Post by sisco311 on 2010-09-17
EDIT: D'oh! cariboo907 beat me to it. =)


Hi and welcome to the forums!

Don't worry the [loopback IP address]("http://en.wikipedia.org/wiki/Localhost") is not private. :)

Just add a new line with your desired hostname:
```
127.*.*.*    localhost
127.*.*.*    ubuntu.ubuntu-domain    ubuntu
**127.0.1.1    Newby1**

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

---

### Post by Gameboyman99 on 2010-09-17
> cat /etc/hosts 192.168.1.215	chilanko-maverick	# Added by NetworkManager 127.0.0.1	localhost.localdomain	localhost **127.0.1.1**	chilanko-maverick 192.168.1.250	willy 192.168.1.235	puntzi 192.168.1.245	mcleese 192.168.1.225	alexis
So already I'm lost, sry :(
Do I need/want to change my IP right there? I just want my network name changed from "ubuntu" to "Newby1"
Will I need to change that^^^ to change my network display name?? Or just the etc/hostname(Which I did)?

---

### Post by Gameboyman99 on 2010-09-17
Oh, thanks sisco311, I'll try that and reboot...

---

### Post by Gameboyman99 on 2010-09-17
Ok, Thx both O' you!!
Works fine!

---

