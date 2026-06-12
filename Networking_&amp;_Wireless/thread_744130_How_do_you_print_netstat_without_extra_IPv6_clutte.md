---
title: "How do you print netstat without extra IPv6 clutter?"
date: 2008-04-03
forum: Networking &amp; Wireless
---

### Post by xluryan on 2008-04-03
When I use netstat -tunp, I get entries like this:

```

::ffff:192.168.1.:42232

```

How can I get netstat to print those entries without the ::ffff: at the start of those lines?

---

### Post by Kebabman on 2008-04-03
Adding '-A inet' into your command should just show results for the inet address family.

---

### Post by xluryan on 2008-04-03
That *kind of* worked. Consider this:

```

Active Internet connections (w/o servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 192.168.1.105:42232     192.168.1.105:5900      ESTABLISHED20258/2
tcp6       0    432 ::ffff:192.168.1.105:22 ::ffff:12.34.137.:41219 ESTABLISHED20256/sshd: ryan [p
tcp6       0      0 ::ffff:192.168.1.1:5900 ::ffff:192.168.1.:42232 ESTABLISHED6362/vino-server

```

I'm remoted in to my home computer from work. I am also tunneling VNC through my SSH session. As you can see, I cannot view the entire remote IP address because it's cut off due to the fact that the ::ffff: preceeding the actual IP makes the entry too long.

Appending '-A inet' to my command gives me this:
```

Active Internet connections (w/o servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 192.168.1.105:42232     192.168.1.105:5900      ESTABLISHED20258/2

```

Any suggestions?

---

