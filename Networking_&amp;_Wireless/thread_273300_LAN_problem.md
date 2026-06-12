---
title: "LAN problem"
date: 2006-10-07
forum: Networking &amp; Wireless
---

### Post by elking on 2006-10-07
hello everyone
so my lan card is indentified and working and everythin
i can ping any website
but i can only open google related websites :S
google.com gmail.com ....etc

anyother website isnt working
downloading any package isnt working
i used DHCP once and static once not working

i used to get something like that in windows but i used a prog called Dr.TCP to change the MTU and the TCP receive window
maybe dats the problem
so is there anyway to the same in ubuntu ?!

Thanks
Bye

---

### Post by handy on 2006-10-07
Try turning off **ipv6** in **Firefox** as follows:

Enter **about:config** in the address field.

Enter **ipv6** in the new **Filter:** field.

Double click on the one & only line left in the main view window to change it's boolean value to **true**.

I can not browse at all without doing the above.

Also, if you have problems accessing the repo's as well?  Have a look at [this link]("http://www.ubuntuforums.org/showthread.php?t=128254&page=2"), try **option 3** from **post 13.**

Best I can do for you... :KS

---

### Post by elking on 2006-10-07
thanks for ur help , but am sry noone of them fixed the problem :S its really frustrating 
and i cant download anyth

waitin for any other suggestions
thanks

---

### Post by yyagol on 2006-10-08
Is it a DNS problem ? because many people have problem regarding DNS .
did you put google.com, gmail.com at your etc/hosts ?
can you ping any site by numbers?(like 67.18.216.114 )
do you have resolving : ```
$ dig -t A cnn.com
```

---

### Post by elking on 2006-10-08
1- the dns is configured but everytime i boot again it clears and i have to set it again
2- No i didnt touch it its a clean install
3- yes i can ping anyth in the world
4- i can resolve

but still i cant open any website or download any package :S:S plz help

---

### Post by Iowan on 2006-10-09
[http://ubuntuforums.org/showpost.php?p=685713&postcount=8]("http://ubuntuforums.org/showpost.php?p=685713&postcount=8")
Does anything here help?

---

