---
title: "SSH and Github"
date: 2011-07-13
forum: New to Ubuntu
---

### Post by micajah on 2011-07-13
I am trying to set up GitHub and can not get past the part of generating the key. When I follow this step


```
$ ssh-keygen -t rsa -C "your_email@youremail.com"
```

I get an output of 

```
open /home/username (which is me)/.ssh/id_rsa failed: Permission denied
Saving the key failed: /home/username (which is me)/.ssh/id_rsa
```


Several months ago when I installed OpenSSH I setup a .pem key. I no longer need this key. 

How do I get in and edit my ssh settings? 

I have tried uninstalling OpenSSH, but the .ssh directory stile exists - with the .pem key. 

From my limited point of view, I think it would be easier to completely uninstall all references to ssh and start clean. 

Can anybody help me?

---

### Post by skatinjj on 2011-07-13
> **micajah said:**
> I am trying to set up GitHub and can not get past the part of generating the key. When I follow this step


```
$ ssh-keygen -t rsa -C "your_email@youremail.com"
```



Try:

```
$ sudo ssh-keygen -t rsa -C "your_email@youremail.com"
```

Without actually doing the whole process just throwing this out there.

---

### Post by micajah on 2011-07-14
Thanks for the advice, this did the trick.

The only thing I am uncertain about is the difference between having the key pair stored in /root/.ssh/id_rsa versus /home/user (me)/.ssh/id_rsa

The tutorial on the github help section shows /home/user (me)/.ssh/id_rsa

---

