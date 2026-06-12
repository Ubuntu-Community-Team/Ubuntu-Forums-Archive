---
title: "libssl-dev"
date: 2008-04-19
forum: Networking &amp; Wireless
---

### Post by mrbuntuman on 2008-04-19
im trying to get libssl-dev but i keep getting a dep error ::

 apt-get install libssl-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libssl-dev: Depends: libssl0.9.8 (= 0.9.8a-7ubuntu0.5) but 0.9.8e-5ubuntu3 is to be installed
              Depends: zlib1g-dev but it is not going to be installed
E: Broken packages

any idea ?

thank u

---

### Post by mrbuntuman on 2008-04-19
i guess im the only one hving this issue lol sucks to be me hehe

---

### Post by StOoZ on 2008-04-19
run sudo 
> apt-get update 
> apt-get upgrade
and then Try again.

and if it continues , check this out:
[https://bugs.launchpad.net/ubuntu/+source/openssl/+bug/78138]("https://bugs.launchpad.net/ubuntu/+source/openssl/+bug/78138")

---

### Post by mrbuntuman on 2008-04-20
Will do thks  for the reply.

---

