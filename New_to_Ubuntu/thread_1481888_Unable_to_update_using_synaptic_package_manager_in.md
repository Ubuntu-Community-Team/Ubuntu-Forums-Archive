---
title: "Unable to update using synaptic package manager in ubuntu 8.04"
date: 2010-05-13
forum: New to Ubuntu
---

### Post by arjunshetty on 2010-05-13
Hi,

I recently installed ubuntu 8.04 using wubi.

I am trying to install certain packages using synaptic package manager. But I am getting the following error

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg](http://in.archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg)  Could not connect to in.archive.ubuntu.com:80 (111.91.91.34), connection timed out

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-en_IN.bz2](http://in.archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-en_IN.bz2)  Unable to connect to in.archive.ubuntu.com http:

I am new to linux and I am not sure what to do about this error. Can somebody please help me? 

I am on a network where I have to use a proxy to connect to the internet. The machine is connected to the internet. Firefox and all works fine. I don't know why it is not able to connect during package updates. Please help me.

Regards,
Arjun

---

### Post by nhasian on 2010-05-13
you could try two things.  first open a terminal from applications-> accessories and try to update with this command:

```
sudo apt-get update && sudo apt-get upgrade
```

if that fails you will need to change your server from System-> Administration-> Software Sources.  there is a dropdown labeled Download From you can change.

---

