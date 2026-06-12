---
title: "resetting iptables and samba"
date: 2007-10-17
forum: Networking &amp; Wireless
---

### Post by -emory- on 2007-10-17
Hey everyone, I've got a bit of a problem, well, a solution that created a minor problem. I finally got internet connection sharing to my xbox, and shares sharing folders over a network to my xbox as well. I want to now be able to read these files that are supposedly shared from my desktop over the network to my office desktop downstairs and my laptop. For a while I messed around with the samba settings and had firestarter running with all different kinds of policies. I never really like firestarter, and recently found a script to share internet connection without firestarter, thus making firestarter useless to me. 
Whenever I try to access shares on my laptop or office computer I get the error that (somewhere along the lines of) "Access denied, you don't have permission to view this" It seems to me to be the same kind of error that I get with a firewall. On my laptop I get a different error as well, Whenever I try to access the shared folders  Iget prompted with a login screen. I enter the only username and password that I would have set (even though I never set up a user/pass for samba) and press OK but it says my password was incorrect. I'm pretty sure that if I could only just reset iptables and samba settings to their default I could get this to work pretty easily, and not mess up so much on teh way. Does anyone know how to fix this? Also, does anyone know how to set samba so that there is not any password required to login? I think this may be the problem, but I can't be sure. Thanks everyone in advance,
emory

---

### Post by mpokrywka on 2007-10-18
To set samba to work without passwords you need to set:
```
security = share
guest account = nobody # or other user that has unix access to shares
```
and in your share definition
```
guest ok = yes
```
(if your share is writeable then files will be owned by user set above)

To tighten security you can set samba to listen only on your internal network interface instead of default all interfaces:
```

    bind interfaces only = yes
    interfaces = lo eth0 # I assume eth0 is your LAN interface
```

---

### Post by -emory- on 2007-10-20
so this is all in my samba.conf file?

---

### Post by -emory- on 2007-10-20
I think I might have screwed around with it a bit too much... I still can't acess my shares on any computer. Could you maybe copy and paste yours (you can take out any passwords of course) just so I can see what exactly i'm doing wrong in mine?

---

