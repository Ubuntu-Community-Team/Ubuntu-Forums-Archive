---
title: "Epson ink levels utility"
date: 2009-05-20
forum: New to Ubuntu
---

### Post by john geary on 2009-05-20
I have downloaded mtink so that I can check ink levels etc, but it informs me that I have to join Ip group before I can use it,How do you join? it doesnt tell you.

---

### Post by Didius Falco on 2009-05-20
> **john geary said:**
> I have downloaded mtink so that I can check ink levels etc, but it informs me that I have to join Ip group before I can use it,How do you join? it doesnt tell you.

Hi John,

If you take a look at the other thread you started (I think the title was about "escputil", but you mentioned mtink in it) I linked to to a thread that would walk you through setting up mtink.

Here is a link to your other thread:

[http://ubuntuforums.org/showthread.php?t=1164342](http://ubuntuforums.org/showthread.php?t=1164342)

Here is a link to to the thread I referred you to:

[http://ubuntuforums.org/showthread.php?t=1148178&highlight=mtink](http://ubuntuforums.org/showthread.php?t=1148178&highlight=mtink)

To add yourself to the lp group, open a Terminal from **Applications/Accessories/Terminal** and type in  ```
sudo adduser john lp
```, substituting your username for john, if it is different.

To confirm that you have been added to the lp (note that it is a lowercase L, not an I or a 1...) group, type ```
cat /etc/group | grep lp
``` in the Terminal shell.

You should see something like this: ```
lp:x:7:john
```From there, just follow the instructions in the thread about configuring mtink. You'll get the benefit of our learning experience without having to re-invent the wheel. <G>

I hope this helps...

Regards,

Didius

---

### Post by john geary on 2009-05-20
Didius
Many thanks, I did it via the terminal commands,not being the sharpest knife in the drawer I also :Ddid not check the port it was trying to use in the PREFERENCES,its now running fine.

---

### Post by Didius Falco on 2009-05-20
Glad to be of any help. I really should take that thread and make a quick HowTo out of it. It would be less confusing for others and less embarrassing for me. :oops: 


Regards,

Didius

---

