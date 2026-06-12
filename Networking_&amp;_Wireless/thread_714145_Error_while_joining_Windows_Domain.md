---
title: "Error while joining Windows Domain"
date: 2008-03-03
forum: Networking &amp; Wireless
---

### Post by EvilMarshmallow on 2008-03-03
Hey all,

I've been following this tutorial: [http://ubuntuforums.org/showthread.php?t=280702](http://ubuntuforums.org/showthread.php?t=280702)

However, I can't get the step where I add the computer to the domain to work properly!

net ads join -U ADMIN

returns

Using short domain name -- G2K
Failed to set servicePrincipalNames.  Please ensure that the DNS domain of this server matches the AD domain, or regoin with using Domain Admin credentials.
Deleted account for 'UBUNTUBOX' in realm 'MYREALM'
Failed to join domain: Type or value exists

I have checked my AD for any sign of the hostname I used, to no avail.  I have also tried several different logins, all with Domain Administrator rights.  Please help!

---

### Post by mindasyS on 2008-03-18
I had this same error.  Check your /etc/hosts file and make certain that the FQDN of your host is there.

127.0.0.1     localhost      mymachine.domain      mymachine

Once I fixed that, it let me join it to the domain.

---

