---
title: "Qemu networking + seamlessvirtualization doesn't work"
date: 2007-05-12
forum: Networking &amp; Wireless
---

### Post by deadland on 2007-05-12
Hi there,

I created a virtual machine following this wiki entry:

[https://help.ubuntu.com/community/SeamlessVirtualization]("https://help.ubuntu.com/community/SeamlessVirtualization")

Host: ubuntu Feisty
Guest: Windows XP home (is this the problem?)

I started the vm by using this command:

```
qemu -m 384 -redir tcp:3389::3389 windows.img
```

to acces the desktop:

```
rdesktop -A -s "c:\seamlessrdp\seamlessrdpshell.exe C:\Programme\Internet Explorer\iexplore.exe" localhost:3389 -u virtual

```

and I get the following error message:

```
Autoselected keyboard map de
ERROR: recv: Connection reset by peer
```

notes:
- the user "virtual" is locked out
- the  WinXP Firewall is deactivated
- the WinXP-vm has no problems to access the internet

I am lost, please help me ...

---

### Post by deadland on 2007-05-20
Okay, its because I am using Windows XP home edition.

Bad luck :(

---

### Post by ktulu1115 on 2007-07-06
I get the same error with rdesktop trying to connect to both Windows XP Pro and Windows 2003 Server Standard Editions - I know the guest OS isn't the issue in my case.  Attempting to get SeamlessVirtualization setup - [https://help.ubuntu.com/community/SeamlessVirtualization](https://help.ubuntu.com/community/SeamlessVirtualization)

Windows firewall is turned off on both machines and can access internet from them, can also ping from Ubuntu host machine.

Only thing I can think of is some compatibility issue - running Feisty 64-bit here.  Ideas??

EDIT: Also running bridged networking on both machines - most HOWTO's say to use host-only networking - could this be the problem??

---

### Post by deadland on 2007-07-06
Well I never got it work with qemu, so I switched to vmware-server and bridged-networking. That helped me, but thats not the solution you are searching for. Sorry

---

