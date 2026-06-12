---
title: "still cannot whitelist ports in MoBlock"
date: 2009-05-20
forum: New to Ubuntu
---

### Post by switch10 on 2009-05-20
I followed directions on this post.  [http://ubuntuforums.org/showthread.php?t=590196](http://ubuntuforums.org/showthread.php?t=590196)

I still get a connection refused.  whats the deal??

---

### Post by switch10 on 2009-05-20
I just enabled incoming pop in MoBlock.  I know this is not good, but I can't find a solution

---

### Post by jre on 2009-05-20
You should write what your problem is. Just pointing to another thread won't get you many answers ...

Since that other thread configuration moved to /etc/blockcontrol/blockcontrol.conf and you have to do a "sudo blockcontrol restart" to apply the changes. You may also use mobloquer (the GUI).

To find out which port is really blocked set in /etc/blockcontrol/blockcontrol.conf ```
LOG_IPTABLES="LOG --log-level info"
```, restart blockcontrol and then check live the blocked packets with ```
sudo tail -f /var/log/syslog
```

Last but not least: you have to whitelist OUTgoing connections when you want to receive mail.

---

### Post by switch10 on 2009-05-21
the problem I was having is the title of this post.  cannot whitelist ports in moblock.  I thought it was pretty straight forward.

Either way it randomly started working shortly after my second post.

---

### Post by jre on 2009-05-21
I wanted to know what ports for which purpose/application you wanted to whitelist. There are differences in the directions (in and out) and the protocol (e.g. TCP, UDP).

I guess it started to know because you restarted blockcontrol or just rebooted.

---

