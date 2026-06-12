---
title: "UncomplicatedFirewall&gt;rule blocking internet access for all programs except whitelist"
date: 2010-10-02
forum: New to Ubuntu
---

### Post by js31 on 2010-10-02
Hi,

I'm new to ufw; in the [manual]("http://manpages.ubuntu.com/manpages/karmic/en/man8/ufw.8.html"), some threads and various configurations people put online, couldn't find anything in this direction -> if there maybe is a possibility to block all programs from access except the ones you got (in my case Opera, ncftpsyncput, Ekiga/zfone and the Ubuntu statistic feedback).

My settings till now are the commands:
```
enable
default deny
limit ssh/tcp
reject out smtp
```

Since some programs said to use a lot different ports, I'm not sure if it makes sense to block particular ones?

---

### Post by jtarin on 2010-10-02
I would like to recommend checking your default Ubuntu firewall ruleset before using any GUI. [Go here for a firewall test]("https://www.grc.com/x/ne.dll?bh0bkyd2").

---

### Post by js31 on 2010-10-02
I tried and soon gave up X) then came to ufw; few commands preconfigured seemed promising. (:

---

