---
title: "How do I unblock a port in FireHOL?"
date: 2009-04-08
forum: New to Ubuntu
---

### Post by bledsoe on 2009-04-08
Hi,

[I posted this question in the Security Discussions forum but got no responses, so perhaps that wasn't the place for it.]

I recently installed dansguardian/tinyproxy/firehol (an internet content filter) on my Ubuntu system, and am generally pretty pleased with it. One problem I've discovered (actually, my teenage son discovered it) is in accessing the "Texas Hold 'Em" app on myspace. The app appears to load, then sits for about 30 seconds or so, then displays the following message:

    Connection Timeout.
    The server may be down for maintenance.
    Your firewall may be blocking access to port 9339.

I assume the problem is with FireHOL, as that's the firewall piece of the dansguardian/tinyproxy/firehol trio and the Texas Hold 'Em app works fine with FireHOL disabled.  I've scoured the online FireHOL documentation but it's greek to me. I also posted to the FireHOL forum on sourceforge, but have not received a response. This seems like such a simple thing to fix, yet I can't figure out how to do it.

My firehol.conf file looks like this (it was taken from a HOWTO on one of the Ubuntu forums):

    version 5

    iptables -t filter -I OUTPUT -d 127.0.0.1 -p tcp --dport 3128 -m owner ! --uid-owner dansguardian -j DROP

    transparent_squid 8080 "root root"

    interface any world
    policy drop
    protection strong
    client all accept
    server cups accept

Many thanks for any suggestions,

---

### Post by lovinglinux on 2009-04-08
I'm not familiar with FireHOL, but I guess this might help you:

[http://ubuntuforums.org/showthread.php?t=132039](http://ubuntuforums.org/showthread.php?t=132039)

BTW, you shouldn't create double posts. If you feel your post is misplaced, then you can ask a moderator to move it by clicking the report icon in the user info sidebar on the left (next to your status).

---

### Post by bledsoe on 2009-04-08
Thanks for the reply (and the tip about double posts, I'll remember that for next time).

I had already read thru the thread you suggested, but it didn't answer my question.

Any other ideas?

---

### Post by lovinglinux on 2009-04-08
> **bledsoe said:**
> Thanks for the reply (and the tip about double posts, I'll remember that for next time).

I had already read thru the thread you suggested, but it didn't answer my question.

Any other ideas?

I know how iptables work, but I don't know how FireHOL works. Nevertheless, it seems to me that you have the necessary rule to allow outgoing browser traffic:

```
client all accept
```

Which basically means (if I understood correctly) that all outgoing traffic will be allowed.

I don't know how myspace applets works, but would be nice to know if you need to open ports to allow incoming connections. Maybe this is the problem.

Check if you have a Firefox extension like AdBlockPlus blocking the content.

You might want to consider using ufw + [gufw](http://gufw.tuxfamily.org/index.html). It's pretty easy to configure and is the recommended firewall manager for Ubuntu.

---

### Post by bledsoe on 2009-04-08
Thanks for those suggestions, they're more than I've been able to come up with so far.  I don't have Adblock Plus installed, but I'll try your code suggestion (maybe later this evening) and see if that works.  Will also look into ufw and gufw, and perhaps I should also learn something about iptables.

BTW, why did you change your mind about your original suggestion to try
```
server custom tcp/9339 default accept
```
That looked like a reasonable thing to try (assuming it does what I'm hoping it does).

---

### Post by lykwydchykyn on 2009-04-08
First thing would be to see if it works with firehol stopped.  Then you'd know if that was actually the problem or not.

I'm not clear whether you need to unblock outgoing 9339 or incoming.  If you can connect to the game with firehol disabled, try running this command while the game is up:
```

sudo netstat -tunap|grep 9339

```
And post the output (if any) here.

---

### Post by KIAaze on 2009-04-08
Try adding one of the following lines at the end of firehol.conf:
```
server custom myspacegame tcp/9339 default accept
server custom myspacegame udp/9339 default accept
server custom myspacegame icmp/9339 default accept

```

Not sure if it works, but that's what's written in the official firehol manual:
[http://firehol.sourceforge.net/adding.html](http://firehol.sourceforge.net/adding.html)
[http://firehol.sourceforge.net/services.html](http://firehol.sourceforge.net/services.html)

P.S.:You might be interested in this too: [https://launchpad.net/webcontentcontrol](https://launchpad.net/webcontentcontrol) ;)

---

### Post by lovinglinux on 2009-04-08
> **bledsoe said:**
> BTW, why did you change your mind about your original suggestion to try
```
server custom tcp/9339 default accept
```
That looked like a reasonable thing to try (assuming it does what I'm hoping it does).

Because while FireHOL options seems pretty self-explanatory, it would be irresponsible to suggest a command that I'm not sure it is correct, specially since it would open a port to all tcp connections.

Anyways, the suggestions provided by lykwydchykyn is the best way to start.

---

### Post by bledsoe on 2009-04-08
Thanks to all for the suggestions.  I'll try them out this evening and post my results.

---

### Post by bledsoe on 2009-04-09
It appears that the problems I was having with the myspace Texas Hold 'Em app are not with dansguardian/tinyproxy/firehol, but may in fact be with the app's developer, [www.zynga.com](www.zynga.com).

Since the app worked fine the first time my son tried it on Ubuntu several weeks ago, and only stopped working after I installed dansguardian/tinyproxy/firehol, I assumed the problem was with dansguardian/tinyproxy/firehol.  Apparently, however, zynga made some change that affects how the app works with Linux systems, so now it won't load at all on my system, even with dansguardian/tinyproxy/firehol disabled.  (I say apparently, because while I found some recent online posts from people complaining about the problem, I can't find anything official from zynga about it.)

Thanks again to those who offered suggestions,

---

