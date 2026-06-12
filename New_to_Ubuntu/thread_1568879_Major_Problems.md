---
title: "Major Problems"
date: 2010-09-06
forum: New to Ubuntu
---

### Post by Suzanne42 on 2010-09-06
I am using Ubuntu 10.04 & its totally buggy. I have no clue how to  fix anything so I am looking for help here. Recently, my Update Manager  failed to update the system.

This is the error:
GPG error: [http://download.virtualbox.org]("http://download.virtualbox.org/")  karmic Release: The following signatures were invalid: BADSIG  54422A4B98AB5139 Oracle Corporation (VirtualBox archive signing key)  <info@virtualbox.org>Failed to fetch [http://ppa.launchpad.net/user/ppa-name/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/user/ppa-name/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

The other error I get is when I boot Ubuntu, there's an error called  busybox. It says stopped waiting for root device, a command intrafms  comes & I have to continuously press exit to reach my desktop. I  have googled for a long while on both these errors but can't find a  solution for either. Can some kind soul explain in layman terms? Thanx.

---

### Post by ikt on 2010-09-06
> **Suzanne42 said:**
> I am using Ubuntu 10.04 & its totally buggy. I have no clue how to  fix anything so I am looking for help here. Recently, my Update Manager  failed to update the system.

This is the error:
GPG error: [http://download.virtualbox.org]("http://download.virtualbox.org/")  karmic Release: The following signatures were invalid: BADSIG  54422A4B98AB5139 Oracle Corporation (VirtualBox archive signing key)  <info@virtualbox.org>Failed to fetch [http://ppa.launchpad.net/user/ppa-name/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/user/ppa-name/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

If you go into: System > Admin > Software Sources > third party sources, and if you see virtualbox listed, untick it.

The other issue going to need more info on, is it similar to this?:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/360378](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/360378)

---

### Post by Suzanne42 on 2010-09-06
Yes, that's the exact problem. Its been plaguing me for days now. Do you know the solution for it? I did as specified for the first problem, no issues, thanx. But what can I do 4 the sec one? Some solutions I saw asked me to type something when the computer boots but nothing works. I can only just keep typing exit repeatedly until I exit.

---

### Post by Suzanne42 on 2010-09-06
Btw could u pls explain in layman terms what I should do to resolve this issue (busybox). There doesn't seem a clear answer in the link u posted, neither m I an Ubuntu pro 2 do a trial on my comp, thanx in advance.

---

### Post by ikt on 2010-09-14
> **Suzanne42 said:**
> Btw could u pls explain in layman terms what I should do to resolve this issue (busybox). There doesn't seem a clear answer in the link u posted, neither m I an Ubuntu pro 2 do a trial on my comp, thanx in advance.

Heya, sorry for the slow response I don't check as often as I should, but yeah it's a known issue and they are working on fixing it, there doesn't appear to be a work around but a lot of people on that page are putting in their opinions of how to fix it.

---

