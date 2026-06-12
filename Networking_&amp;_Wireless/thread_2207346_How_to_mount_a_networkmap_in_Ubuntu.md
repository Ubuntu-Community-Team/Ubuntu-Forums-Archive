---
title: "How to mount a networkmap in Ubuntu"
date: 2014-02-23
forum: Networking &amp; Wireless
---

### Post by Ubi_one_2014 on 2014-02-23
[COLOR=#333333][FONT=Lucida Grande]Hi[/FONT][/COLOR]

[COLOR=#333333][FONT=Lucida Grande]TS119 1TbHD with FW 4.0.2 ( NAS)[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]OS= Ubuntu Linux 13.10[/FONT][/COLOR]

[COLOR=#333333][FONT=Lucida Grande]TS119 Config:[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]created some users with access to several maps[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]maps are MP3, Upload, Pictures, and some others[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]User share got R/W access to MP3 and Upload[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]guest access to map MP3 is enabled[/FONT][/COLOR]

[COLOR=#333333][FONT=Lucida Grande]Ubuntu Config:[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]created directory /mnt/TS119 and /mnt/UP[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]mounted both dir's to the map MP3 and Upload with the command:[/FONT][/COLOR]

[COLOR=#333333][FONT=Lucida Grande]mount -t cifs -o username=share,password=XX //192.168.178.11/MP3 /mnt/TS119[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]mount -t cifs -o username=share,password=XX //192.168.178.11/Upload /mnt/UP[/FONT][/COLOR]

[COLOR=#333333][FONT=Lucida Grande]both directory&#347; appeared in Dolphin[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]i can open that directory&#347; to see all my MP3 and Uploads[/FONT][/COLOR]

[COLOR=#333333][FONT=Lucida Grande]Issue:[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]i can not write to both dir's nor i can create new dir's .[/FONT][/COLOR]

[COLOR=#333333][FONT=Lucida Grande]I need write access to bot directory's[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]How do i do that?[/FONT][/COLOR]

---

### Post by Morbius1 on 2014-02-23
How about taking possession of the mounted share:

>  [COLOR=#333333][FONT=Lucida Grande]mount -t cifs -o username=share,password=XX,[/FONT][/COLOR][COLOR=#0000cd][FONT=Lucida Grande]**uid=1000**[/FONT][/COLOR][COLOR=#333333][FONT=Lucida Grande] //192.168.178.11/MP3 /mnt/TS119[/FONT][/COLOR]
That's asumming your uid is 1000. To find out run this command:
```
id
```

---

### Post by Ubi_one_2014 on 2014-02-23
[B]thanks,

solved by adding uid=[username]

example
[COLOR=#333333]*[FONT=Lucida Grande]mount -t cifs -o username=share,password=XX,[/FONT]*[/COLOR][COLOR=#0000cd]*[FONT=Lucida Grande]uid=[username-on-ubuntu][/FONT]*[/COLOR][COLOR=#333333]*[FONT=Lucida Grande] //192.168.178.11/MP3 /mnt/TS119[/FONT]*[/COLOR]
[/B]

---

