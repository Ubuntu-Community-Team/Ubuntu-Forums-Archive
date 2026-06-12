---
title: "RTNETLINK answers: File exists error with tc script"
date: 2015-01-28
forum: Networking &amp; Wireless
---

### Post by jody6 on 2015-01-28
[FONT=arial narrow][SIZE=6]Hi All , 
I am trying to [COLOR=#444444]throttle a maximum rate  by using TC[/COLOR]
[COLOR=#444444]I was trying this script[/COLOR]

[COLOR=#444444][COLOR=#002e7a]sudo tc qdisc add dev eth0 handle 1: root htb default 11     [/COLOR][/COLOR]
[COLOR=#444444][COLOR=#002e7a]sudo tc class add dev eth0 parent 1: classid 1:1 htb rate 1kbps[/COLOR][/COLOR]
[COLOR=#444444][COLOR=#002e7a]sudo tc class add dev eth0 parent 1:1 classid 1:11 htb rate 1kbps



[/COLOR][/COLOR][COLOR=#000000]Once I run the first command I got this Error 
RTNETLINK answers: File exists


Would please help me to fix it ?[/COLOR][/SIZE][/FONT][COLOR=#444444][FONT=Calibri][COLOR=#002e7a][FONT=arial narrow][SIZE=6]


Thank you [/SIZE][/FONT]

[/COLOR][/FONT][/COLOR]
[COLOR=#002e7a]
[/COLOR]

---

