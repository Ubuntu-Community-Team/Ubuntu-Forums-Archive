---
title: "trouble with unity"
date: 2011-06-15
forum: New to Ubuntu
---

### Post by cmwhidmore on 2011-06-15
I am running ubuntu 11.04 (narwhal), and on my first login, the system complains that I do not have the hardware to support Unity. 

Previously, i had ubuntu studio (also narwhal) installed, and Unity ran without issue. It even worked I ran it on a live USB. Is there something I'm missing?

---

### Post by collisionystm on 2011-06-15
studio may ship with a different kernel than 11.04

---

### Post by cmwhidmore on 2011-06-15
let me rephrase- is there somethig I can do? I've run unity before with narwhal- and nothing has changed since..

---

### Post by Muskegman on 2011-06-15
It just means that you dont have the hardware drivers activated yet, go to "system settings" "additional drivers" let it do a search for additional drivers and then choose the recommended driver. Click on "activate" then close the window. Reboot your pc and all should be good.

---

### Post by cmwhidmore on 2011-06-15
"no proprietary drivers are in use on your system". Damn, i thought that would've done it.

---

### Post by wildmanne39 on 2011-06-15
> **cmwhidmore said:**
> "no proprietary drivers are in use on your system". Damn, i thought that would've done it.
Hi, run this is a terminal
```
/usr/lib/nux/unity_support_test -p
``` and post it back here by clicking on new reply and click # and paste the information between the brackets.

---

### Post by cmwhidmore on 2011-06-15
```

bash: /usr/lib/nux/unity_support_test: No such file or directory

```

Okay... now I finally got it to work.. needed a full shutdown... but now i can't see any of the icons on the left... and all my windows go nuts when i mouse over them...

they flip/rotate/pixelate/white out...

help?

---

### Post by wildmanne39 on 2011-06-15
> **cmwhidmore said:**
> ```

bash: /usr/lib/nux/unity_support_test: No such file or directory

```

Okay... now I finally got it to work.. needed a full shutdown... but now i can't see any of the icons on the left... and all my windows go nuts when i mouse over them...

they flip/rotate/pixelate/white out...

help?
Hi, run the command just as I wrote it no bash in from of it.

---

### Post by cmwhidmore on 2011-06-16
> **wildmanne39 said:**
> Hi, run the command just as I wrote it no bash in from of it.

I did. That last post was me showing you an error reported by bash..

And to repeat my point (because i'm not sure you got it the first time around):
[QUOTE=cmwhidmore] I finally got it to work.. needed a full shutdown... but now i can't  see any of the icons on the left... and all my windows go nuts when i  mouse over them...

they flip/rotate/pixelate/white out...

help?[/QUOTE]

---

### Post by wildmanne39 on 2011-06-16
> **cmwhidmore said:**
> I did. That last post was me showing you an error reported by bash..

And to repeat my point (because i'm not sure you got it the first time around):Hi, does it have a windows 95 look? Can you post a screen shot it would be helpful.

---

### Post by cmwhidmore on 2011-06-18
Sure- here's what the problem looks like

---

### Post by wildmanne39 on 2011-06-18
> **cmwhidmore said:**
> Sure- here's what the problem looks likeHi, run this command in a terminal
```
sudo lshw
```and post the outcome  here by clicking on new reply and click # and paste the information between the brackets.

---

