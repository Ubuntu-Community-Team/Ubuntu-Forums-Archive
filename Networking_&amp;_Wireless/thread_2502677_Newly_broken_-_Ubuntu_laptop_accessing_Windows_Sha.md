---
title: "Newly broken - Ubuntu laptop accessing Windows Shared folders using Samba"
date: 2024-11-24
forum: Networking &amp; Wireless
---

### Post by boohyperad on 2024-11-24
I have shared folders on Windows 10 that I _can still access via other Windows machines and iOS phones_. 
BUT my Ubuntu laptop has suddenly lost access.

Based on suggestions in older threads I have tried...... 
 - totally uninstalled SAMBA (packages, related dependencies, and config files) & re-installed version 4.19.5 
 - updating and upgrading the system
 - a shutdown and reboot at both ends
 - editing smb.conf file to...
       --------- adding "min protocol = SMB2"
       --------- changed this and also tried "protocol = SMB3"
However, I am still denied access, but only on my Ubuntu machine.

Using "Other Locations" in the Files App I still get....       (I mainly rely on GUI interfaces as I am a coding neophyte)
 - smb://PC_NAME.....   I get alerted "Unable to access location... Connection Refused."
If i try...
 - smb://192.168.1.xxx....I get prompted to with "Authentication Required... username/domain/password" but entering these terms just results in the alert refreshing with the 'password' field again empty.
Both of these methods used to work.

Any help greatly appreciated, but please explain as simply as you can   ;)

---

### Post by boohyperad on 2024-11-26
[h=2][/h] 		 				 				 					 				 		 			 				[INDENT] 					[SOLVED]
Further scourering of previous threads on this topic found solution for me...
Thanks to "Morbius1" from thread...     [https://ubuntuforums.org/showthread.php?t=2435292](https://ubuntuforums.org/showthread.php?t=2435292)
Adding  ".local " after my PC host-name in file manager's location bar fixes issue for me (never had to do this in the past)
Thanks Mobius1  ;^)

--------------------------------------------------------

[COLOR=#000000]You can get that error message from trying to  access from your file manager any server that has disabled smb1. It's  becasue of a bug in a sub-componenet of gvfs.[/COLOR]

[COLOR=#000000]Access it this way in your file managers location bar:[/COLOR]
[COLOR=#000000]Code:
[COLOR=#417394]smb[/COLOR]://win10-host-name.local/share-name[/COLOR]
[COLOR=#000000]You have to specify the [/COLOR][COLOR=#417394]windows[/COLOR][COLOR=#000000] host name and share name explicitly. You can't use [/COLOR][COLOR=#417394]smb[/COLOR][COLOR=#000000]://win10-host-name.local by itself to see the list of shares.[/COLOR]
[/INDENT]

---

