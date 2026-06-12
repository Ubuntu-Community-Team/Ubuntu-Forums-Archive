---
title: "SSH -pexpect -chmod failure"
date: 2008-07-30
forum: Networking &amp; Wireless
---

### Post by Kaniknas on 2008-07-30
I am running Ubuntu 8.04 on a mac mini through Parallels Desktop as a VM.  THe VM is used to control an AFM via a DSP board which can only run in a *nix architecture.  I need to initiate the board which involves making a special character file, loading firmware into its memory, etc...  However, after the firmware is loaded, the permissions on the file (/dev/sranger0) are automatically changed such that I no longer have writing permissions.  I am trying to automate this entire process through pexpect, a python module and ssh.  I can change the permissions via ssh through sudo chmod, but for some reason this flat out fails silently when I attempt to do it via pexpect.  I get the feeling that this may be due to some security setting in Ubuntu that I don't know about, as other sudo commands don't have this problem.  Does anyone know what the problem or solution might be?

-Thanks

---

### Post by Kaniknas on 2008-07-30
I resolved the problem on my own.  It was related to a timing issue... the board needed time to digest the firmware.

-thanks

---

