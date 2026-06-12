---
title: "[SOLVED] Samba shares broken bug - Ubuntu-to-Windows workaround?"
date: 2008-01-22
forum: Networking &amp; Wireless
---

### Post by VvWolverinevV on 2008-01-22
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/samba/+bug/47386](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/47386) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hi.  I am currently experiencing exactly this bug:
[quote=Ed Comer]When I try to access the [Ubuntu] shares via “Start->My Network Places”, the Dapper shares do not display.

When I try to access the [Ubuntu] shares via “Start->My Network Places->View Workgroup Computers”, the [Ubuntu] machine icon displays, but when I click on it, it fails with a “The network path was not found” error dialog box.

When I try to access the Windows shares from [Ubuntu] via Places-Network Servers, the Windows Network icon is displayed but when I click on the icon, the dialog box window clears to a blank and the shares do not display.
[/quote]

It is possible to work around the Windows-to-Ubuntu problem by accessing the Windows IP via Places>Connect to Server.  Is there a similar workaround for the Ubuntu-to-Windows problem?

Some older threads on the Windows-to-Ubuntu problem:
[http://ubuntuforums.org/showthread.php?t=298909](http://ubuntuforums.org/showthread.php?t=298909)
[http://ubuntuforums.org/showthread.php?t=430806](http://ubuntuforums.org/showthread.php?t=430806)
[http://ubuntuforums.org/showthread.php?t=491437](http://ubuntuforums.org/showthread.php?t=491437)

*Edit*
This problem was caused by the Firestarter firewall for me.

---

