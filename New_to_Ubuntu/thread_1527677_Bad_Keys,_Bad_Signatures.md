---
title: "Bad Keys, Bad Signatures"
date: 2010-07-09
forum: New to Ubuntu
---

### Post by barney385 on 2010-07-09
I installed a new kernel update yesterday, and today I'm getting GPG errors. Not that they are related. Here are the GPG errors I'm getting in terminal:

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: The following signatures were invalid: BADSIG 1780999033C3C104 Launchpad GDM2Setup
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: The following signatures were invalid: BADSIG 35DA01C261E46227 Launchpad Default PPA
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: The following signatures were invalid: BADSIG 6AF0E1940624A220 Launchpad PPA for TualatriX

Any ideas would be greatly appreciated.

---

### Post by SpyderBite on 2010-07-09
Here's an example of how I fix the same errors from time to time.

[I]Fixing Broken Keys: W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY
[/I]
gpg --keyserver keyserver.ubuntu.com --recv-key  368BB0C046F34169
gpg -a --export 368BB0C046F34169 | sudo apt-key add -

Where as 368BB0C046F34169 is your problem key #. eg. 6AF0E1940624A220 from your OP.

---

### Post by barney385 on 2010-07-09
> **SpyderBite said:**
> Here's an example of how I fix the same errors from time to time.

[I]Fixing Broken Keys: W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY
[/I]
gpg --keyserver keyserver.ubuntu.com --recv-key  368BB0C046F34169
gpg -a --export 368BB0C046F34169 | sudo apt-key add -

Where as 368BB0C046F34169 is your problem key #. eg. 6AF0E1940624A220 from your OP.

I did that for each key and it appeared to work fine. 

sudo apt-get update gave me the same error.

Oh well, thanks anyway.

---

### Post by barney385 on 2010-07-12
I still haven't found a solution for this...anyone?

---

