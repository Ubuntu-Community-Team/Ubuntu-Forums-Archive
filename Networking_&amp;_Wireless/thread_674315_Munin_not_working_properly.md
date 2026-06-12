---
title: "Munin not working properly"
date: 2008-01-21
forum: Networking &amp; Wireless
---

### Post by murbanci on 2008-01-21
I have installed munin on my computer and am able to access the web page where i am supposed to be able to monitor my computer, however, none of the plugins are showing up.  I have made sure that they are all installed and all the config files appear to be fine.  What do I need to do to be able to view the plugins?  Thanks for any help.

---

### Post by kenzie on 2008-01-30
I'm having the same issue with Ubuntu 7.10 -- Munin website is up but there are no links to graphs. The only issue I see in the logs is:

```
==> /var/log/munin/munin-update.log <==
Jan 30 17:08:01 [27970] - Could not connect to ####.com(127.0.0.1): Bad file descriptor - Attempting to use old configuration
```

Also, according to some of the docs I should be able to telnet localhost 4949 and get a reply, but it times-out.

Does anyone have munin working on 7.10? (It was a breeze to setup on 6.06).

---

### Post by kenzie on 2008-01-30
I was able to get it working by following the instructions here:
[http://ubuntuforums.org/showthread.php?p=4239979#post4239979]("http://ubuntuforums.org/showthread.php?p=4239979#post4239979")

```

sudo ifconfig lo localhost
sudo route add localhost dev lo

```

Now I can connect to localhost, and munin and monit are both working. Unfortunately I don't know how to make this change permanent, as I need to re-issue the commands after each reboot. If anyone can guide me through that I'd appreciate it. Thanks.

---

