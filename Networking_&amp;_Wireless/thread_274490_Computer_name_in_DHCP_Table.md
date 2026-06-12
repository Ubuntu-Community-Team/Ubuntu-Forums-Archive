---
title: "Computer name in DHCP Table"
date: 2006-10-09
forum: Networking &amp; Wireless
---

### Post by 64mgb on 2006-10-09
I have a home network with 3 Ununtu boxes and one Windows 2000 box, connected to the internet via a Linksys router which acts as my DHCP server.  When I go to the DHCP clients table in the router, it shows the name of the Windows box fine, but all of the Ubuntu box names show up as garbage.  Any ideas how I can correct this?

Thanks,
Rich

---

### Post by koshari on 2006-10-10
add a friendly name in the network config properties,

---

### Post by 64mgb on 2006-10-10
> **koshari said:**
> add a friendly name in the network config properties,
I'm not sure what you're saying.

Rich

---

### Post by Boelcke on 2006-10-10
I believe there are a number of ways to do this.  For various reasons, some of which are lost to me now, I found some advice along these lines:

In your /etc/nsswitch.conf file, change this:

```
hosts: files dns
```

to 

```
hosts: files dns wins
```

And install winbind with Synaptic.

Also, I might've added this to nsswitch.conf

```
# Added the winbind to passwd and group
passwd:         compat winbind
group:          compat winbind
shadow:         compat
```

Sorry for my ambiguity, but I'm forgetting now.  It's one of those things where you have the problem, understand the solution, and then completely forget about it.  ;)

---

### Post by 64mgb on 2006-10-11
Thanks Boelcke, I'll tinker with those settings.

Rich

---

### Post by spd106 on 2006-10-12
[http://www.ubuntuforums.org/showthread.php?t=177832](http://www.ubuntuforums.org/showthread.php?t=177832), see post #3

---

### Post by 64mgb on 2006-10-12
Thanks spd106...that looks like it has promise...I'll try it tonight!

Rich

---

### Post by 64mgb on 2006-10-12
I went home at lunch time and tried this and it works perfectly.  Too bad the computer name needs to be maintained in at least 3 different places.

Now I need to see if I can use the remote desktop connection by using the computer name rather than the ip address.  Actually, it would work before if I used "vnc:/<computer name>:0", but wouldn't work with "<computer name>:0".

Thanks,
Rich

---

