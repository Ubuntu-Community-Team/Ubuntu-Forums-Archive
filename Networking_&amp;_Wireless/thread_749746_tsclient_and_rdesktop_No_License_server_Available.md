---
title: "tsclient and rdesktop: No License server Available"
date: 2008-04-08
forum: Networking &amp; Wireless
---

### Post by raidicar on 2008-04-08
Hi!

I installed Ubuntu 7.10. I have rdesktop and tsclient installed on my Ubuntu machine.

When I try and connect Ubuntu to Windows 2003 Server:  

"Disconected: No License server Available"
Suggestions?

Windows 98/XP conect in Windows 2003 Server with Tsclient.

ps: When I've this problem to connect windows 98/XP to Windows 2003 Server:
I initiate the register:
Hkey local machine / software / microsoft / MSlicensing
remove HardwareID and Store.

---

### Post by ahmadzainul on 2008-04-09
I have been worked on rdesktop with LTSP ubuntu 7.04, everything is work well and even all client can access ms windows xp. you may need to install a patch where you  can get at  [http://blogpmenier.dynalias.net/docext/xp/termiserv](http://blogpmenier.dynalias.net/docext/xp/termiserv) xpsp2 i386 1.0.exe.
After that you create user account in win xp sp 2. And you set some user account to allow get access remotely from my computer properties on remote tab.
I wish you a success o this setting
:popcorn:

---

### Post by raidicar on 2008-04-09
ahmadzainul - Pactch installed,account create, but the problem continues occurring...

---

