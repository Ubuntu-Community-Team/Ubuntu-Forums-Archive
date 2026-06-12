---
title: "Difficulty accessing Oracle on Ubunutu from other systems"
date: 2009-01-22
forum: New to Ubuntu
---

### Post by dgodf on 2009-01-22
Hi,

I recently built a virtual (using VMWare) Ubuntu system. I've installed Oracle XE, which works fine. My issue is that I cannot access the Oracle XE HTTP interface from any other system, e.g. if I open firefox within my Ubuntu VM, I can connect, but from other machines I simply get a "page not found". I can ping the VM from other systems, so I'm confident the IP address I'm using is correct.

Any suggestions as to how I might rectify this would be appreciated. Eventually I want to set up the same environment using Ubuntu server/JEOS, so my only option to access the Oracle HTTP interface will be from another system.

Many thanks!!

David

---

### Post by blueridgedog on 2009-01-22
It sounds like a vmware issue.  What is the host OS?  Did you setup vmware networking as bridged, nat or host only?

[http://www.vmware.com/support/ws55/doc/ws_net_basics.html](http://www.vmware.com/support/ws55/doc/ws_net_basics.html)

---

