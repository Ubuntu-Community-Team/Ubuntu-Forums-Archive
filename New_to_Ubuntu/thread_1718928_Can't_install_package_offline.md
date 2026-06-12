---
title: "Can't install package offline"
date: 2011-04-01
forum: New to Ubuntu
---

### Post by robotz421 on 2011-04-01
I am trying to install a package from the offline repository.  It is libkrb5-3 under Lucid 10.04 amd64.  When I try to open it with the Gdebi package installer, instead of popping up a window and showing me whether I can install the package or not like it does for other packages, Gdebi opens the window but then closes it again right away and exits.  I have downloaded the file twice and tried it so I don't think there is anything wrong with the download.  The actual file is libkrb5-3_1.8.1+dfsg-2ubuntu0.8_amd64.deb.  Any ideas?

---

### Post by andrewthomas on 2011-04-01
> **robotz421 said:**
>   The actual file is libkrb5-3_1.8.1+dfsg-2ubuntu0.8_amd64.deb.  Any ideas?
Navigate to the directory that the file is in and 

```
sudo dpkg -i libkrb5-3_1.8.1+dfsg-2ubuntu0.8_amd64.deb
```If the file has any unresolved dependencies it will let you know.

---

### Post by robotz421 on 2011-04-01
Okay, thanks for your post.  I think I have a bit of a situation.  Dpkg said I had an unresolved dependency because libkrb5support0 on my system was an old version so I got the new version from the offline repository and tried to install it.  When I do that Gdebi says I have broken dependencies and says I should run sudo apt-get install -f or gksudo synaptic.  When I try the apt-get it says it wants to delete 370 packages many of which look important such as many starting with gnome so I did not do that.  It also says there is 1 package not fully installed or removed.  When I try synaptic it says I have two packages which are broken but if I want to remove these two I also have to remove a lot of others which look important.  The two packages synaptic says are broken are libgssapi-krb5-2 and libkrb5-3.  I have just been installing a few packages so I think that is what caused the problem.  Libkrb5-3 is one I installed and I think the other one might be related to the ones I was installing too.  I think I have to tread lightly here to avoid messing up my whole system.  What should I do?

---

### Post by andrewthomas on 2011-04-02
Here is what you need to install libkrb5-3
```
http://security.ubuntu.com/ubuntu/pool/universe/k/krb5/krb5-admin-server_1.8.1+dfsg-2ubuntu0.8_amd64.deb
http://security.ubuntu.com/ubuntu/pool/universe/k/krb5/krb5-kdc_1.8.1+dfsg-2ubuntu0.8_amd64.deb
http://security.ubuntu.com/ubuntu/pool/main/k/krb5/krb5-user_1.8.1+dfsg-2ubuntu0.8_amd64.deb
http://security.ubuntu.com/ubuntu/pool/main/k/krb5/libgssapi-krb5-2_1.8.1+dfsg-2ubuntu0.8_amd64.deb
http://security.ubuntu.com/ubuntu/pool/main/k/krb5/libgssrpc4_1.8.1+dfsg-2ubuntu0.8_amd64.deb
http://security.ubuntu.com/ubuntu/pool/main/k/krb5/libk5crypto3_1.8.1+dfsg-2ubuntu0.8_amd64.deb
http://security.ubuntu.com/ubuntu/pool/main/k/krb5/libkadm5clnt-mit7_1.8.1+dfsg-2ubuntu0.8_amd64.deb
http://security.ubuntu.com/ubuntu/pool/main/k/krb5/libkadm5srv-mit7_1.8.1+dfsg-2ubuntu0.8_amd64.deb
http://security.ubuntu.com/ubuntu/pool/main/k/krb5/libkdb5-4_1.8.1+dfsg-2ubuntu0.8_amd64.deb
http://security.ubuntu.com/ubuntu/pool/main/k/krb5/libkrb5-3_1.8.1+dfsg-2ubuntu0.8_amd64.deb
http://security.ubuntu.com/ubuntu/pool/main/k/krb5/libkrb5support0_1.8.1+dfsg-2ubuntu0.8_amd64.deb
```and you probably have these already but it can't hurt to reinstall
```
http://mirrors.us.kernel.org/ubuntu//pool/main/k/keyutils/libkeyutils1_1.2-12_amd64.deb
http://mirrors.us.kernel.org/ubuntu//pool/main/e/e2fsprogs/libcomerr2_1.41.11-1ubuntu2_amd64.deb
http://mirrors.us.kernel.org/ubuntu//pool/main/e/e2fsprogs/libss2_1.41.11-1ubuntu2_amd64.deb
```Just download them all into a directory and either select them all at once and try to install with gdebi or just ```
dpkg -i *
```in the directory

---

### Post by robotz421 on 2011-04-03
Yes, I am familiar with those package names.  I was in the process of installing them when the problem occurred.  So you are saying it is safe to go through the process again and reinstall and this won't cause any further problems?  What about the package that is not fully installed or removed?

---

### Post by robotz421 on 2011-04-06
Okay, I tried what you suggested.  Gdebi still complained about dependencies but dpkg seems to have worked.

---

