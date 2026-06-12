---
title: "rsh help!!!"
date: 2006-10-10
forum: Networking &amp; Wireless
---

### Post by mcrae on 2006-10-10
Hi, I found problems using rsh, it looked like I was doing ssh when I tried rsh, then I have done

```
sudo apt-get install rsh-client
```

but I still have this output

rsh: connect(remote.host [xxx.xxx.xxx.xxx]): Connection refused

...everything seems the same as before

Does someone have an idea...

---

### Post by LeNain on 2006-10-10
Are you sure there is no firewall blocking rsh protocol and that rsh.d is activated on server (in xinetd.conf).

---

### Post by mcrae on 2006-10-10
> **LeNain said:**
> Are you sure there is no firewall blocking rsh protocol and that rsh.d is activated on server (in xinetd.conf).

I think the firewall settings are ok - I have ssh, telnet and xwindows services allowed

I installed xinetd now, but it's trouble for me again - I don't like just to ask "how to..." fix this, but I really don't have so much time to read man pages for enabling rsh.d ...
But thanks a lot!!!

---

