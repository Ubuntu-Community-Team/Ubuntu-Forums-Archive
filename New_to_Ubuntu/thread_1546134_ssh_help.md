---
title: "ssh help"
date: 2010-08-04
forum: New to Ubuntu
---

### Post by furialis on 2010-08-04
I don't know anything about ssh, but would like secure remote access to my home computer. Is there a step-by-step ssh for dummies?

---

### Post by ubudog on 2010-08-04
[Ssh for Dummies]("http://edumacation.com/SshForDummies")  Hope that helps.  If you have any questions, just ask.

---

### Post by Ozymandias_117 on 2010-08-04
```
sudo aptitude install ssh-server
```

Then I would suggest you modify your /etc/ssh/sshd_config and find "allowrootlogin" and change it to "no".

If you have a router, you will have to set up port forwarding for port 22 to your servers IP.

---

### Post by ubudog on 2010-08-04
> **Ozymandias_117 said:**
> ```
sudo aptitude install ssh-server
```

Then I would suggest you modify your /etc/ssh/sshd_config and find "allowrootlogin" and change it to "no".

If you have a router, you will have to set up port forwarding for port 22 to your servers IP.

Also disable password authentication.

---

### Post by ubudog on 2010-08-04
And remember, always restart the ssh server after making a change.
```
sudo /etc/init.d/ssh restart
```

---

### Post by Ozymandias_117 on 2010-08-04
> **ubudog said:**
> And remember, always restart the ssh server after making a change.
```
sudo /etc/init.d/ssh restart
```

Thanks. Forgot to mention that :D

---

### Post by ubudog on 2010-08-04
> **ozymandias_117 said:**
> thanks. Forgot to mention that :d

np.

---

### Post by furialis on 2010-08-04
> **ubudog said:**
> Also disable password authentication.

Would that be the last option, UsePAM ?

---

### Post by ubudog on 2010-08-04
> **furialis said:**
> Would that be the last option, UsePAM ?

No, it should say PasswordAuthentication yes (change the yes to a no).  Then restart your ssh server like I showed before.

You can leave PAM like it is.  Good luck!

---

### Post by prshah on 2010-08-05
> **ubudog said:**
> Also disable password authentication.

> **ubudog said:**
> ```
sudo /etc/init.d/ssh restart
```

Why disable Password Authentication? Without this, OP will have to set up a trusted key first. Given that he is starting SSH, do you think he is better off disabling this first? I would suggest it be kept enabled, with a strong password, and "AllowUsers, AllowGroups, DenyUsers, DenyGroups" keywords used for extra security.

btw, from 10.04 onwards, init.d services are better accessed with the "service" keyword, eg:```
sudo service ssh restart
```

---

### Post by ubudog on 2010-08-05
True, but if you want more security, disabling password authentication (once you have keys set up) would be a good idea.

---

