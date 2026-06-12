---
title: "Upgraded to 11.04, Software Centre not working"
date: 2011-05-02
forum: New to Ubuntu
---

### Post by Ghostlove on 2011-05-02
I upgraded to Natty yesterday and all is good. I'm working in Ubuntu Classic as I don't like Unity.

However, my Software Centre isn't working. When I try to open it, the box stays grey and hovering my cursor over it gives me the 'waiting' cursor.

Can anyone help?

ETA: sudo software-center opens it for me, but I'd like to not have to do that...

---

### Post by Spyderkid on 2011-05-02
use

sudo apt-get update && sudo apt-get upgrade

?

---

### Post by Ghostlove on 2011-05-02
That seemed to work! Thank you! :D

---

### Post by matus12345 on 2011-05-15
Hello!
I have this problem with Ubuntu software center but i cant fix it because i get with first command 
"sudo apt-get update" error :
```
E: Type „“deb“ is not known on line 1 v in list of sources /etc/apt/sources.list
E: Cant read list of sources.  (my translation)
```and sources.list contains: ```
“deb [http://archive.offensive-security.com]("http://archive.offensive-security.com/") pwnsauce main microverse macroverse restricted universe multiverse”
```Thanks for any responses

---

### Post by 143ramdon on 2011-07-26
ubuntu software centre shows a grey window when opened... can any one help....

---

### Post by r3d_E on 2011-08-05
I have had a problem with the software center for a few days now. It opens fine but when I go into any specific category it just sits there as if loading but doesn't do anything. I have tried:

sudo apt-get upgrade & sudo apt-get update and with both I get the same error.

Error:
```
E: Type 'ain' is not known on line 3 in source list /etc/apt/sources.list.d/deluge-team-ppa-natty.list
E: The list of sources could not be read.
```

Any help would be greatly appreciated. Thanks

---

