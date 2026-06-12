---
title: "swat and samba problem"
date: 2010-06-12
forum: New to Ubuntu
---

### Post by lance bermudez on 2010-06-12
[http://www.linuxjournal.com/magazine/paranoid-penguin-samba-security-part-i?page=0,1](http://www.linuxjournal.com/magazine/paranoid-penguin-samba-security-part-i?page=0,1)

[http://www.linuxjournal.com/article/10256](http://www.linuxjournal.com/article/10256)

[http://www.linuxjournal.com/article/10292](http://www.linuxjournal.com/article/10292)

[http://www.linuxjournal.com/article/10336](http://www.linuxjournal.com/article/10336)

I have not been able to get this to work. I have lance as a user. no firewall it turned on.

---

### Post by cariboo on 2010-06-12
I truly hope you aren't trying to use samba over the internet, it's just an invitation to get cracked. If you want to do file sharing over the internet, use sshfs, it is much more secure, and encrypted too. For a howto have a look [here]("https://help.ubuntu.com/community/SSHFS").

---

### Post by lance bermudez on 2010-06-13
I'm not trying to go over the internet neither is the howtos they are for going over your own home network.

---

### Post by Morbius1 on 2010-06-13
May I ask what it is you're trying to do. Just share some directories over you home network or is this something bigger?

If you need help with your current set up please post the output of the following commands:

```
net usershare info
sudo net usershare info
testparm -s
```

---

