---
title: "Firewall Monitor"
date: 2010-02-05
forum: New to Ubuntu
---

### Post by spikoley on 2010-02-05
Is there a firewall monitor to show you attempted connections?

---

### Post by *Raz0r* on 2010-02-05
There is a firestarter

---

### Post by spikoley on 2010-02-06
> ***Raz0r* said:**
> There is a firestarter

I was looking for something more sophisticated.

---

### Post by MrWES on 2010-02-06
> **spikoley said:**
> Is there a firewall monitor to show you attempted connections?

Most attempted connections occur on port 22, the port used for SSH. You could install Denyhosts which will depending on how you set it up, add the IP to the /etc/hosts.deny file and therefore block it.

[http://ubuntuforums.org/showthread.php?t=450853]("http://ubuntuforums.org/showthread.php?t=450853")

Or the simple way is to look at the /var/auth.log

Bill

---

### Post by airtonix on 2010-02-06
> **spikoley said:**
> Is there a firewall monitor to show you attempted connections?

These articles might be of interest to you : 
[list]
[*] [http://www.cyberciti.biz/tips/top-linux-monitoring-tools.html](http://www.cyberciti.biz/tips/top-linux-monitoring-tools.html)
[*] [http://www.linuxquestions.org/questions/linux-networking-3/network-traffic-monitor-my-incoming-and-outgoing-ports-632259/](http://www.linuxquestions.org/questions/linux-networking-3/network-traffic-monitor-my-incoming-and-outgoing-ports-632259/)
[*] [http://www.linux.com/archive/articles/50649](http://www.linux.com/archive/articles/50649)
[/list]

Some applications you might find handy : 
[list]
[*] jnettop
[*] ntop
[*] ```
watch -d "netstat -ntauple"
```
[*] ipstate : [http://linuxpoison.blogspot.com/2010/02/iptstate-display-iptables-state.html](http://linuxpoison.blogspot.com/2010/02/iptstate-display-iptables-state.html)
[*] fwmon : [http://www.scaramanga.co.uk/fwmon/](http://www.scaramanga.co.uk/fwmon/)
[*] iptraf
[*] [Razorback]("http://www.intersectalliance.com/projects/RazorBack/index.html#ScreenShots") with [Snort]("http://www.snort.org/") 
[/list]

---

