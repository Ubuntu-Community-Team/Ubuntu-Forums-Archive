---
title: "Upgraded to 16.10 - now my internet stopped working!"
date: 2017-04-18
forum: Networking &amp; Wireless
---

### Post by 01gaeren on 2017-04-18
I recently upgraded to 16.10 and my Ethernet stopped working. 

Can anyone help me?

---

### Post by kc1di on 2017-04-18
Hello 01gaeren  and welcome to Ubuntu,

can you give us some more info , especially the Ethernet card your machine is using?

if you can get to a terminal and type this command it will give that information:
```
lspci | egrep -i --color 'network|ethernet'
```

you can just copy it from here into the terminal and hit enter. 
Then let us know the results.

---

### Post by raccoonstrait on 2017-04-18
[COLOR=#000000]Not sure if you have the same issue as I did, but there is a bug out there. See response #2 on this thread, it solved my issue.[/COLOR]

[https://ubuntuforums.org/showthread.php?t=2358631](https://ubuntuforums.org/showthread.php?t=2358631)

[COLOR=#000000]RaccoonStrait[/COLOR]

---

