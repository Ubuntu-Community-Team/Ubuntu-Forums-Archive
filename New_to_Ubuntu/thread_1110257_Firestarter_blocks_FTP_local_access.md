---
title: "Firestarter blocks FTP local access"
date: 2009-03-29
forum: New to Ubuntu
---

### Post by mistypotato on 2009-03-29
For some reason, Firestarter will not allow me to connect locally to my FTP server.

I have explicitly allowed the other desktop's IP address on the FTP port and yet no matter what, it refuses to let the connection through.

I'm baffled.  As soon as I turn off firestarter, bingo....no trouble connecting.

Anyone got any ideas on this?

thanks :KS

---

### Post by jsuhr on 2009-08-04
Same issue here with Jaunty. Get it figured out?

---

### Post by kg84 on 2009-08-04
\Edit:

Deleted comment as I now see that you have specified the ip AND the appropriate port(s).

---

### Post by dmizer on 2009-08-04
I highly suggest uninstalling Firestarter. Purge it completely from your system as it doesn't tend to work well, and doesn't always do what you tell it to do.

Install GUFW instead. It's also a GUI firewall configuration front end, but it operates much more gracefully in Ubuntu.

---

### Post by jsuhr on 2009-08-04
Thanks dmizer, will do. Busy now but will post later after purge / install.

---

### Post by jsuhr on 2009-08-04
Hmm, not sure what I'm doing wrong. I'm only able to connect if I "allow ftp anywhere." FYI I have two computers on a basic router provided by my ISP. I have checked their respective IP's with "ifconfig." Not sure what else to do, or if it is that big of an issue, but if possible would like some insight.

---

### Post by dmizer on 2009-08-04
If you have a router, is there a specific need you have for a local firewall in addition to the firewall provided by your router?

---

### Post by jsuhr on 2009-08-04
Actually no, I don't. I very recently set the router and the instructions in the box were not very detailed. After a little searching I found what I needed online. Thanks for the help.

---

