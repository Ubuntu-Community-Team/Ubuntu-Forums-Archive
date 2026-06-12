---
title: "repository not added successifully"
date: 2010-11-06
forum: New to Ubuntu
---

### Post by amitpokhrel on 2010-11-06
hello everyone!!
I don't know whether it is a problem or not but whenever i try to add any repository (for example..when I was trying to add repository of theme) from terminal I get this information-

[I]Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv A6E348801F28F6B59D308A6036960FC31E5F36F0
gpg: requesting key 1E5F36F0 from hkp server keyserver.ubuntu.com
gpg: key 1E5F36F0: "Launchpad PPA for Fortunato Ventre" not changed
gpg: Total number processed: 1
gpg: unchanged: 1[/I]

But all other updates and downloading after adding repository command are successfully done.
can anyone suggest something

---

### Post by Elfy on 2010-11-06
Looks like you already have it - hence the not changed and unchanged comments.

Check in /etc/apt/sources.list.d/

for the PPA

---

