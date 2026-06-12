---
title: "open office 3 authentication certificate"
date: 2009-02-03
forum: New to Ubuntu
---

### Post by powel212 on 2009-02-03
Hi
Anybody know where to find the open office 3 authentication certificate.
Thanks

---

### Post by BDNiner on 2009-02-03
What do you mean by authentication certificate?

---

### Post by powel212 on 2009-02-03
Also called "Automatic Signing Key"

I have Ooffice 3 installed but the repository appears to require a signing key for update and my system is telling my I don't have the key.

Thanks

---

### Post by powel212 on 2009-02-04
Here is my error code:

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 60D11217247D1CFF

---

### Post by jerome1232 on 2009-02-04
[https://launchpad.net/~openoffice-pkgs/+archive/ppa](https://launchpad.net/~openoffice-pkgs/+archive/ppa)

That is their overview page on ppa, there's a link to this key there but here's the direct link

[http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x60D11217247D1CFF](http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x60D11217247D1CFF)

Just copy that into a text file, save it, then use the System-Administration-Software Sources-Authentication Tab, Import key to import it.

I found it by googling, "ppa open office"

---

### Post by powel212 on 2009-02-04
Awesome. Thanks. Worked like a charm

Kudos.

---

