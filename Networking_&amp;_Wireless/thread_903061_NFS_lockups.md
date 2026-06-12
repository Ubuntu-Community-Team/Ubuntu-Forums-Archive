---
title: "NFS lockups"
date: 2008-08-27
forum: Networking &amp; Wireless
---

### Post by skibler on 2008-08-27
I have a fresh installation of Ubuntu on a macbook laptop. When I mount an nfs share from it everything appears to work for a while. But within minutes any NFS activity will stop/hang.

Other clients connect to the nfs server without issues. dmesg on the macbook reports a time out after a while. Nautilus does not fail gracefully here and you basically have to reset the computer to get it to behave itself again.

This is very frustrating. I am not sure what to do as it "just works" with other computers I have tried. THis same macbook had OSX on it last week and was connecting with NFS to the same server without issues.

---

### Post by dmizer on 2008-08-27
NFS does not handle network disconnects well. Do you frequently drop your connection to the server?

---

