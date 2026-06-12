---
title: "How to talk to Active Directory with Hardy."
date: 2008-05-28
forum: Networking &amp; Wireless
---

### Post by mohenjo on 2008-05-28
Hi all,

I'm a first-time Ubuntu user who is more than used to Windows networks.  I've installed Ubuntu 8.04 on a test laptop here at work and want to hook it up to my Win2k3 AD network, but am sort of at a loss as to where to go to set that up.

Just to clarify a bit more, I'm working with the desktop version and want to be able to have it authenticate to our AD domain.  I'm unfortunately a pretty new linux user, though I'm spending as much time as I can afford here on the forums.

Any advice or assistance would be much appreciated!

::edit::
I've found a package called Authentication Properties (in Ubuntu's add/remove applications, looking at all available applications) which mentions that it can be used to configure a workstation to authenticate against a server (saying whether it's ldap, kerberos, AD, or other).  The unfortunate thing for me is that our network requires users be connected to our domain before we can access the internet, so I will attempt to install this tonight from home and see if it produces the results I seek.

---

### Post by jimv on 2008-05-28
I think the package you are looking for is called likewise-open.  

[https://help.ubuntu.com/8.04/serverguide/C/likewise-open.html](https://help.ubuntu.com/8.04/serverguide/C/likewise-open.html)

---

