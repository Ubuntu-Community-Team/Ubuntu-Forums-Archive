---
title: "repository index problems- NO_PUBKEY"
date: 2011-05-02
forum: New to Ubuntu
---

### Post by homerwookey on 2011-05-02
Hi all,
Could someone point me in the right direction for how to update my repositories? I keep getting this message every time I try reloading synaptic package manager

GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2836CB0A8AC93F7AFailed to fetch [http://ppa.launchpad.net//backports/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net//backports/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

Thanks in advance

---

### Post by oldos2er on 2011-05-02
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 2836CB0A8AC93F7A
```

---

### Post by homerwookey on 2011-05-02
typed that in, this was the result

 sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 2836CB0A8AC93F7A
[sudo] password for paul: 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys 2836CB0A8AC93F7A
gpg: requesting key 8AC93F7A from hkp server keyserver.ubuntu.com
gpg: key 8AC93F7A: public key "Launchpad Kubuntu Updates" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)



still getting the same message when I try updating the repositories
anyone have any ideas?

---

### Post by oldos2er on 2011-05-02
Just to confirm, you ran **sudo apt-get update** and you're still getting the NO PUBKEY error, or the 404? There is no "backports" directory at [http://ppa.launchpad.net](http://ppa.launchpad.net), so you'll need to disable that one.

---

### Post by homerwookey on 2011-05-02
Ok sorry to all for wasting your time, Ive just had chance to have a good look through the threads and found this which explains my issues and how to sort them out.

[http://ubuntuforums.org/showthread.php?t=1497195](http://ubuntuforums.org/showthread.php?t=1497195)

Thanks Ann for your help ;)

---

### Post by oldos2er on 2011-05-02
No problem. Glad you solved it.

---

