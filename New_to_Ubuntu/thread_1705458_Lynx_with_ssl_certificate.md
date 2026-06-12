---
title: "Lynx with ssl certificate"
date: 2011-03-12
forum: New to Ubuntu
---

### Post by Smash85 on 2011-03-12
Hello!
I've got small problem with lynx and ssl cerficates. 
I want to display some website, but to do this, my browser (Lynx Version 2.8.8dev.5) must use ssl certificate. I have no idea how to 'attach' certificate to lynx. I search this on google but no effects. 
Maybe someone could give me a little hint ; )

---

### Post by yeats on 2011-03-12
This thread from 2008: 

[http://ubuntuforums.org/showthread.php?t=1008513](http://ubuntuforums.org/showthread.php?t=1008513)

suggests installing the lynx-cur package to fix this.  Can you try that?

---

### Post by Smash85 on 2011-03-13
yeah I've read this topic but connecting to websites over https it's not the point( I have lynx-cur and it works pretty good).
My main problem is to attach ssl certificate to lynx. 
I've tried to edit /etc/lynx-cur/lynx.cfg and put something like this:
```

SSL_CERT_FILE::/etc/ssl/certs/my_cert.pem
```
But no results : (

---

