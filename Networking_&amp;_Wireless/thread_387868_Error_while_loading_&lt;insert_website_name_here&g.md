---
title: "Error while loading &lt;insert website name here&gt;"
date: 2007-03-18
forum: Networking &amp; Wireless
---

### Post by Mr. 680x0 on 2007-03-18
Using a Linksys Wireless B PCMCIA card in Kubunu with Konquerer as my web browser, I keep getting this messgage constantly with practically every site I visit (with a different website URL in it of course):

An error occurred while loading [http://mail.lycos.com/lycos/Index.lycos:](http://mail.lycos.com/lycos/Index.lycos:)
Unknown host mail.lycos.com

Is there any way to fix this?  It's a major pain in the *** to try to browse the internet with this coming up constantly.

--John

---

### Post by Mr. C. on 2007-03-18
Please show output from Terminal window of:

```
cat /etc/resolv.conf
```

MrC

---

### Post by Mr. 680x0 on 2007-03-21
after I enter that it says:
```
nameserver 192.168.1.1
```
That's the internal IP of my router.

---

### Post by Mr. C. on 2007-03-21
Ok, that's what I thought.   Review my post here:

[http://ubuntuforums.org/showthread.php?t=389377&highlight=mrc+DNS](http://ubuntuforums.org/showthread.php?t=389377&highlight=mrc+DNS)

This will resolve your issues.

MrC

---

### Post by Mr. 680x0 on 2007-04-15
I couldn't get my issues resolved.  I'm using Ubuntu instead of Kubuntu now and having no problems.  Since I installed in safe graphics mode, I can't get my laptop LCD to go past 1024x768, even though it's a 1600x1200 screen.

---

