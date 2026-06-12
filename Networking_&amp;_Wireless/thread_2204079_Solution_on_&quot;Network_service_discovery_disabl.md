---
title: "Solution on &quot;Network service discovery disabled&quot;?"
date: 2014-02-06
forum: Networking &amp; Wireless
---

### Post by Hvidemose on 2014-02-06
For several versions of Ubuntu, I've got this message when I connect to my network:
[IMG]http://ubuntudanmark.dk/forum/download/file.php?id=512[/IMG]
[COLOR=#000000][FONT=Ubuntu Mono]Network service discovery disabled
[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]Your current network has a .local domain,
which is not recommended and incompatable
with Avahi network service discovery.
The service has been disabled.[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]
[/FONT][/COLOR]

The reason seems to be that I use a different DNS. It must be said that I do not experience problems other than getting this annoying message. 


As I understand, the program Avahi is used for printer location, etc.., so it might not be wise to uninstall it (?). BUT I would really like to get rid of the message, so it does not show up time and time again ... 


Does anyone have a possible solution?

---

### Post by Hvidemose on 2014-02-07
Ok, I just disabled it by entering terminal as root, and [COLOR=#000000]edited the file /etc/default/avahi-daemon:[/COLOR]

```
[COLOR=#000000][FONT=Ubuntu Mono]gksu gedit /etc/default/avahi-daemon[/FONT][/COLOR]
```
[COLOR=#000000]
and changed the line [/COLOR]**[COLOR=#000000]AVAHI_DAEMON_DETECT_LOCAL=1 [/COLOR]**[COLOR=#000000]to [/COLOR]**[COLOR=#000000]AVAHI_DAEMON_DETECT_LOCAL=0[/COLOR]**

---

