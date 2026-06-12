---
title: "Did I Break Nautilus?"
date: 2010-08-16
forum: New to Ubuntu
---

### Post by BlazeFire247 on 2010-08-16
I installed nautilus-elementary and when I go to Preferences I don't see a "Tweaks" tab. My location bar has an ugly white space between it. 

I used ```
sudo add-apt-repository ppa:am-monkeyd/nautilus-elementary-ppa
``` and I don't think it worked properly. I did [what this website said]("http://www.webupd8.org/2010/04/install-nautilus-elementary-230-via-ppa.html"), but it didn't seem to work.

I don't know if this is an issue with Elementary GTK or nautilus, but my Places bar on the left has a grey background that sort of sticks out.

---

### Post by BlazeFire247 on 2010-08-16
I have another question:

If I install an old version of nautilus-elementary, will it work?

---

### Post by Frogs Hair on 2010-08-16
Use the ppa purge and try again I installed Elementary Nautilus after reading your post and it works great . You can also restore Nautilus with the purge.

 PPA Purge:  sudo add-apt-repository ppa:THE_PPA
sudo ppa-purge ppa:<repository-name>/<subdirectory>

---

### Post by BlazeFire247 on 2010-08-17
```
takzk22@ubuntu:~$ sudo add-apt-repository ppa:am-monkeyd/nautilus-elementary-ppa[sudo] password for takzk22: 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv 91DB0C47720C152FF466E7BA61E091672E206FF0
gpg: requesting key 2E206FF0 from hkp server keyserver.ubuntu.com
gpg: key 2E206FF0: "Launchpad nautilus-elementary" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
takzk22@ubuntu:~$ sudo ppa-purge ppa:am-monkeyd/nautilus-elementary-ppa
sudo: ppa-purge: command not found

```

I don't seem to have that command..

---

### Post by BlazeFire247 on 2010-08-18
Great. All I forgot to do was to sudo apt-get update && sudo apt-get ugrade :oops: Solved now..

---

