---
title: "Firefox via ssh?"
date: 2009-03-19
forum: New to Ubuntu
---

### Post by darksideforge on 2009-03-19
Would somebody mind telling me what I'm doing wrong? Thanks.

```
ssh user@domain.com
password:
[user@domain]$ /bin/su
password:
[user@domain]# cd /bin
[root@domain bin]# firefox
Error: no display specified
[root@domain bin]# 
```

---

### Post by adult swim on 2009-03-20
you need to make sure you have x11 forwarding set to on in your /etc/ssh/sshd_config file and then ```
ssh -X user@domain.com
```

---

### Post by HermanAB on 2009-03-20
...and your local machine must be running X.  If it is Windows, use Xming.

Cheers,

Herman

---

### Post by darksideforge on 2009-03-20
> **adult swim said:**
> you need to make sure you have x11 forwarding set to on in your /etc/ssh/sshd_config file and then ```
ssh -X user@domain.com
```

done, but still can't launch firefox :(

---

### Post by LakesProse on 2009-03-29
> **darksideforge said:**
> done, but still can't launch firefox :(
What's the error message ? on which OS are you ?

---

### Post by hyper_ch on 2009-03-29
x11 also needs to be activated on the remote server's openssh server settings

---

### Post by hovzio on 2009-03-29
> **hyper_ch said:**
> x11 also needs to be activated on the remote server's openssh server settings

This is done in the sshd_config file on the server side.File is located in:

/etc/ssh/sshd_config


X11Forwarding needs to be set to yes.

---

