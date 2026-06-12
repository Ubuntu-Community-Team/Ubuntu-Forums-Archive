---
title: "SSH Tunneling port 80"
date: 2009-11-08
forum: New to Ubuntu
---

### Post by pi.boy.travis on 2009-11-08
Hi!

OK, here is my dilemma.  I am trying to access my webmail account, however, my schools http filtering blocks GMail.  Couldn't I, with PuTTY on a Windows machine, tunnel port 80 and browse the web through my Ubuntu SSH server?  How would I set this up?  I have PuTTY and Firefox on my flashdrive, and OpenSSH server installed on my remote Ubuntu server.

Thanks!

---

### Post by RealG187 on 2009-11-08
If you wanna bypass filters use a progam called Ultra Surf.

With that said, there probably is a way, but I don't know it.

---

### Post by teward on 2009-11-08
> **pi.boy.travis said:**
> Hi!

OK, here is my dilemma.  I am trying to access my webmail account, however, my schools http filtering blocks GMail.  Couldn't I, with PuTTY on a Windows machine, tunnel port 80 and browse the web through my Ubuntu SSH server?  How would I set this up?  I have PuTTY and Firefox on my flashdrive, and OpenSSH server installed on my remote Ubuntu server.

Thanks!

Won't work if port 80 is being filtered.  They'll filter out PuTTY and similar SSH connections (if they're anything like my high school was).

---

### Post by pi.boy.travis on 2009-11-08
> **TrekCaptainUSA said:**
> Won't work if port 80 is being filtered.  They'll filter out PuTTY and similar SSH connections (if they're anything like my high school was).

Could I use some uncommon port, and then instruct Firefox to browse using that port?

---

### Post by pi.boy.travis on 2009-11-08
OK, so I am trying to get this to work on my Ubuntu laptop, just to try to get it working.  Here is what I am using:

```
ssh -L 9000:my-remote-server's-FQDN:80 mail.google.com -N
```

Then I point my browser to localhost:9000, but I get "Connection refused."

What am I doing wrong?

---

### Post by pi.boy.travis on 2009-11-08
I've solved it!

```
ssh -D 9000 -N server-FQDN
```

The I configure Firefox to use my remote server as a SOCKS host.

---

