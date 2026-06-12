---
title: "What command to install clamav 0.95.1"
date: 2009-04-16
forum: New to Ubuntu
---

### Post by st4 on 2009-04-16
I reinstalled Ubuntu to get rid of avast linux home edition and clamav 0.94.2. I downloaded clamav 0.95.1, what command do I use to install it? Thanks

---

### Post by porchrat on 2009-04-16
You don't need to download it you can get 0.92 in the repositories.

Just go to System --> Administration --> Synaptic package manager

Then go to 'search' and type "clamav"

it will find it for you, then click the checkbox and select 'apply'

---

### Post by st4 on 2009-04-16
> **porchrat said:**
> You don't need to download it you can get 0.92 in the repositories.

Just go to System --> Administration --> Synaptic package manager

Then go to 'search' and type "clamav"

it will find it for you, then click the checkbox and select 'apply'Thanks for the reply, but that's an outdated version. When I run that, I get a message saying it's an outdated engine.

---

### Post by kukibird1 on 2009-04-16
It looks like you will have to compile the new version from source. The repos only carry version 0.94 .

running sudo apt-get build-dep will give you what you need to build this new version. 

[http://www.clamav.net/download/packages/packages-linux]("http://www.clamav.net/download/packages/packages-linux")

---

