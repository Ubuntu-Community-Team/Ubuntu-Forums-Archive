---
title: "sudo add-apt-repository ppa:*** no response"
date: 2010-08-31
forum: New to Ubuntu
---

### Post by romar_31 on 2010-08-31
i am running Ubuntu lucid lynx and whenever i try to add repository using the terminal, for example:
```
sudo add-apt-repository ppa:bean123ch/burg
```
i receive no response. is it normal or how long can i wait for success confirmation and such? This is my 3rd thread but no one seems minding the other threads. :(

---

### Post by pmlxuser on 2010-08-31
used yout example it worked so i don't quite get your problem, have you enabled other community  repositories  in the software source ??

try it again using another ppa.

---

### Post by romar_31 on 2010-08-31
> **pmlxuser said:**
> used yout example it worked so i don't quite get your problem, have you enabled other community  repositories  in the software source ??

try it again using another ppa.
thanks for minding this post :D hmm. how would i know if it successfully added to repository? because when i enter them on terminal, nothing happens. but i have found a solution of my own problem, by launching software sources preferences the add the source there ppa:**** :)

---

### Post by philinux on 2010-08-31
> **romar_31 said:**
> thanks for minding this post :D hmm. how would i know if it successfully added to repository? because when i enter them on terminal, nothing happens. but i have found a solution of my own problem, by launching software sources preferences the add the source there ppa:**** :)

[https://help.ubuntu.com/community/Repositories/CommandLine#Adding%20Launchpad%20PPA%20Repositories](https://help.ubuntu.com/community/Repositories/CommandLine#Adding%20Launchpad%20PPA%20Repositories)

---

### Post by sikander3786 on 2010-08-31
> **romar_31 said:**
> thanks for minding this post :D hmm. how would i know if it successfully added to repository? because when i enter them on terminal, nothing happens. but i have found a solution of my own problem, by launching software sources preferences the add the source there ppa:**** :)

You can check for the added/active repositories in Synaptic >>> Settings >>> Repositories >>> Other Software.

The added repositories are listed there and active ones are "checked".

Just to make sure, I added your above mentioned repository and after password I got this out put.

```

Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv A267D98DF71B10F601CFAC1B55708F1EE06803C5
gpg: requesting key E06803C5 from hkp server keyserver.ubuntu.com
gpg: key E06803C5: public key "Launchpad burg" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)

```

Regards.


[COLOR="Red"]Edit:[/COLOR] You can add the repositories via commandline, synaptic package manager or software sources. What ever you like. Adding ppa in software sources or synaptic get the job done.

---

### Post by 3rdalbum on 2010-08-31
Your internet connection is up and running?

---

### Post by romar_31 on 2010-09-02
thanks to all of you. i use proxy server to be able to connect to the internet. (for free lol) maybe the problem has to do something with it.

---

### Post by fahadysf on 2011-01-11
Yes I believe the problem is definitely related to being behind a proxy server. I will update it here as soon as I find a solution.

---

