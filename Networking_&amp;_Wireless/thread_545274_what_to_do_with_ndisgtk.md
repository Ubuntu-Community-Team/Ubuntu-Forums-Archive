---
title: "what to do with ndisgtk?"
date: 2007-09-07
forum: Networking &amp; Wireless
---

### Post by martin.renders on 2007-09-07
**This post could be related to an Ubuntu bug filed at**: [http://ubuntuforums.org/showthread.php?t=179270](http://ubuntuforums.org/showthread.php?t=179270) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				i'm trying to install my wireless card InProComm IPN2220 and i've tryed to install with ndiswrapper, but the edition i've used doesn't fit my kernel, so i've installed ndisgtk, that is the same ndiswrapper for my kind of kernel, so i did.

sudo apt-get install ndisgtk
and it did it,
then sudo ndisgtk neti2220
and the wireless connection window started, 
when i browse into the folder that contains .inf file, and click ok,
ubuntu answer me: 
sh: ndiswrapper: not found
FATAL: Could not open '/lib/modules/2.6.20-16-lowlatency/kernel/ubuntu/misc/ndiswrapper/ndiswrapper.ko': No such file or directory

any help is appreciated . Martin.

---

### Post by amgat on 2007-09-07
What does "sudo lspci" say?

---

