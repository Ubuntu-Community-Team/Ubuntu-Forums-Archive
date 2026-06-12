---
title: "Provider forbade routers"
date: 2015-08-29
forum: Networking &amp; Wireless
---

### Post by Giperboloid on 2015-08-29
[COLOR=#000000][FONT=Ubuntu Beta]Good day to everyone![/FONT][/COLOR]
[FONT=Ubuntu Beta][COLOR=#000000]My dormitory's  provider forbade using routers. We found the solution for Windows:[/COLOR][/FONT]
[COLOR=#000000][FONT=Ubuntu Beta]1) To make reg-file:[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]Windows Registry Editor Version 5.00[/FONT][/COLOR]

[COLOR=#000000][FONT=Ubuntu Beta][HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\services\Tcpip\Parameters][/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]"DefaultTTL"=dword:00000081[/FONT][/COLOR]

[COLOR=#000000][FONT=Ubuntu Beta]2) To execute this commands in console:[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]   netsh int ipv4 set glob defaultcurhoplimit=129[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]   netsh int ipv6 set glob defaultcurhoplimit=129[/FONT][/COLOR]

[COLOR=#000000][FONT=Ubuntu Beta]The question is how should I translate this solution for Ubuntu? [/FONT][/COLOR][IMG]http://forum.ubuntu.ru/Smileys/webby/smiley.gif[/IMG]

---

### Post by Irihapeti on 2015-08-29
I've no doubt this is a frustrating situation to be in.

However, as stated in the  [ Forums Code of Conduct]("http://ubuntuforums.org/misc.php?do=showrules"), which you agreed to when you signed up, we don't support circumventing terms of service, EULAs, regulations and so on.

Thread closed.

---

