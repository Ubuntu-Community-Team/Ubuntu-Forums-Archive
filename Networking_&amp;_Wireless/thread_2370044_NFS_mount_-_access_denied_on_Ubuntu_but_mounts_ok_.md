---
title: "NFS mount - access denied on Ubuntu but mounts ok on CentOS"
date: 2017-08-29
forum: Networking &amp; Wireless
---

### Post by zepherdog6 on 2017-08-29
Hi, 
[FONT=arial]
[COLOR=#111111]I'm running some NFS mount tests this morning and getting some weird results[/COLOR]
[COLOR=#111111]Disclaimer - newbie to linux and netapp - any help is greatly appreciated![/COLOR]
[COLOR=#111111]
CentOS will mount, Ubuntu will not[/COLOR]
[/FONT][COLOR=#111111][FONT=Ubuntu][FONT=arial]Same commands are issued - is there something special I need to do on Ubuntu?[/FONT]
[/FONT][/COLOR]
```
mount –t nfs 10.250.1.5:/Vol003 /mnt/db
```

[COLOR=#111111][FONT=Ubuntu][FONT=arial]From Cento[/FONT]s
[IMG]https://i.stack.imgur.com/gd5hi.png[/IMG][/FONT][/COLOR]
[FONT=arial][COLOR=#111111]
From Ubuntu
[IMG]https://i.stack.imgur.com/1Uidy.png[/IMG][/COLOR]
[COLOR=#111111]
Any ideas[/COLOR]
[COLOR=#111111]Cheers Mike[/COLOR][/FONT]

---

### Post by zepherdog6 on 2017-08-30
[COLOR=#111111][FONT=Ubuntu]Is an issue with my base Ubuntu Image - deployed and AWS Ubuntu AMI and the NFS mount command worked......[/FONT][/COLOR]

---

### Post by zepherdog6 on 2017-08-30
[COLOR=#333333][FONT=&amp]On the 14.04 Ubuntu Image, that i was experiencing issues on, I needed to add this options[/FONT][/COLOR]
```
**-o v3**[COLOR=#333333][FONT=&amp] 
```
and it mounted. This wasn't required for my 16.04 image[/FONT][/COLOR]

---

