---
title: "sudo apt-get update error"
date: 2009-03-01
forum: New to Ubuntu
---

### Post by al.adab on 2009-03-01
hello,

I've noticed the following error (on a *sudo apt-get update*) in the past few days: 

[I]Fetched 616B in 3s (204B/s)
Reading package lists... Done
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6AF0E1940624A220
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 60D11217247D1CFF
W: You may want to run apt-get update to correct these problems
[/I]

I did run it again, but keep on getting the same message. Any idea? Thanks.

---

### Post by binbash on 2009-03-01
[http://www.ubuntu-inside.me/2009/02/howto-fix-signaturekeyserver-problems.html](http://www.ubuntu-inside.me/2009/02/howto-fix-signaturekeyserver-problems.html)

---

### Post by forger on 2009-03-02
> **binbash said:**
> [http://www.ubuntu-inside.me/2009/02/howto-fix-signaturekeyserver-problems.html](http://www.ubuntu-inside.me/2009/02/howto-fix-signaturekeyserver-problems.html)

The updated version:
[thread=1056099]**Update your Launchpad PPA repositories and apt keys**[/thread]

---

### Post by al.adab on 2009-03-02
thanks both :) error fixed.

---

