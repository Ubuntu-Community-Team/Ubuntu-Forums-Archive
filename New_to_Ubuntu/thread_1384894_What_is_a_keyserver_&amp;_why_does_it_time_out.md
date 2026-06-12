---
title: "What is a keyserver &amp; why does it time out?"
date: 2010-01-18
forum: New to Ubuntu
---

### Post by neu5eeCh on 2010-01-18
Just wanted to try out GnoMenu 2.2. Entered the following (as instructed):

sudo add-apt-repository ppa:gnomenu-team/ppa

Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv D9E565BAE102F0ACAB5D257FF45E32D195B47D2A
gpg: requesting key 95B47D2A from hkp server keyserver.ubuntu.com
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error

So...

Now what?

---

### Post by sandyd on 2010-01-18
> **VTPoet said:**
> Just wanted to try out GnoMenu 2.2. Entered the following (as instructed):

sudo add-apt-repository ppa:gnomenu-team/ppa

Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv D9E565BAE102F0ACAB5D257FF45E32D195B47D2A
gpg: requesting key 95B47D2A from hkp server keyserver.ubuntu.com
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error

So...

Now what?
just a minor hiccup. its back up.

The keys are used to verify that your not using packages from an untrusted (and possibly malicious) source

---

### Post by neu5eeCh on 2010-01-18
Thanks, but I'm afraid it's still hiccuping. I would post the latest timeout message, but it's identical.

---

### Post by bodhi.zazen on 2010-01-18
a key server is a public server where people put their GPG keys.

[http://en.wikipedia.org/wiki/Key_server_%28cryptographic%29](http://en.wikipedia.org/wiki/Key_server_%28cryptographic%29)

such keys have many functions from signing packages to emails =)

---

### Post by neu5eeCh on 2010-01-18
Thanks Bodhi... so why is it timing out? Is there a work-around? Any suggestions?

---

### Post by sandyd on 2010-01-19
> **VTPoet said:**
> Thanks Bodhi... so why is it timing out? Is there a work-around? Any suggestions?
i think its more like your internet connection is having a problem.
ive been pinging it for the last 15 minutes, and theirs no problem. (sorry server admins, i HAD to do that)

---

### Post by neu5eeCh on 2010-01-19
//i think its more like your internet connection is having a problem.//

If so, it's a  selective problem. 

In every other respect, there's nothing wrong with my Internet connection. Just did a speed test and it's burnin' hot. Do you have any other suggestions?

---

### Post by bodhi.zazen on 2010-01-19
> **VTPoet said:**
> //i think its more like your internet connection is having a problem.//

If so, it's a  selective problem. 

In every other respect, there's nothing wrong with my Internet connection. Just did a speed test and it's burnin' hot. Do you have any other suggestions?

Are you running a firewall ?

---

### Post by neu5eeCh on 2010-01-19
Hi Bodhi, you almost got credit for this solve. 

After Carlee insisted that the server was available, that only left a handful of options. I checked my DSL modem's firewall. It was set to Maximum Security. I disabled it and was able to proceed.

Thanks to both of you.

---

