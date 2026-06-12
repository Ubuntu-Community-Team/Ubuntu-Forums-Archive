---
title: "NTP Time Server Setting Jaunty"
date: 2009-04-15
forum: New to Ubuntu
---

### Post by yeehi on 2009-04-15
Hello!

I was rather surprised to find that there was no automatic synch set up with an Internet time server on my Jaunty installation.

How can we verify that the system is synching properly to a time server, once it has been set up?

Can we synch with a stratum zero clock?

---

### Post by llamabr on 2009-04-15
You can run ntpdate.  You could also put it in your inet.d file, so that it runs on startup.

---

### Post by yeehi on 2009-04-15
I try that ntpdate,  but I get an error messaage:

ntpdate[27608]: no servers can be used, exiting

---

### Post by sgosnell on 2009-04-15
Are you online?  Did you specify a server?  Did you use sudo?

```
sudo ntpdate time-a.nist.gov
```

---

### Post by llamabr on 2009-04-15
```
sudo ntpdate rolex.peachnet.edu
```

---

