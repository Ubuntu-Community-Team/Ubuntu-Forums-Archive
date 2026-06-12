---
title: "How can I tell WHY a port is open"
date: 2014-04-05
forum: Networking &amp; Wireless
---

### Post by cable_guy on 2014-04-05
Hi all,

I did a port scan on my ubuntu box and found a larger number of ports open than I would have expected, I know what some of them are but not others, is there a way to check what service is using the ports please?

---

### Post by steeldriver on 2014-04-05
You can use netstat and/or lsof

e.g. to list all **l**istening **p**orts for both **t**cp and **u**dp
```

sudo netstat -nltup

```

or for a particular port (e.g. for 5900, the default VNC port for display :0)
```

sudo netstat -nltup | grep :5900

sudo lsof -i :5900

```

---

### Post by cable_guy on 2014-04-05
thank you very much, most helpful steeldriver. If you're interested, XBMC and Plex count for a hell of a lot of ports!

---

### Post by SeijiSensei on 2014-04-06
If you did the scan from the computer itself, it probably used the "localhost" interface and not the network adapter.  That doesn't mean those same ports are visible from outside the computer over the network.  Try running a scan from another computer.  I bet some ports like 3306 for MySQL don't show up in an scan from outside.  Many such services are limited to localhost by default in Ubuntu for security reasons.

---

### Post by cable_guy on 2014-04-07
I scanned it from my Android phone

---

