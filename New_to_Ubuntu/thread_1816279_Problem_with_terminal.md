---
title: "Problem with terminal"
date: 2011-08-01
forum: New to Ubuntu
---

### Post by moadeep on 2011-08-01
Hello All,

I'm having a trivial but irritating problem when typing commands into my terminal. For longer commands, the string continues at the start of the same line 'overwriting' my prompt instead of carrying over to the next line (images attached).

Any ideas?

Moa

---

### Post by moadeep on 2011-08-03
Any ideas?

I only noticed this when I customised my prompt earlier this week so it is probably related to this. Here is my PS1 variable: - [COLOR=Red]\e[0;33m[\u:\w]$ \e[m[/COLOR]

---

### Post by skatinjj on 2011-08-03
I don't mess with this, but after looking at some pages I found, you line just doesn't look right.

[http://ubuntuforums.org/showthread.php?t=674446]("http://ubuntuforums.org/showthread.php?t=674446")

There is a tutorial for customizing the prompt.

---

### Post by moadeep on 2011-08-03
> **skatinjj said:**
> I don't mess with this, but after looking at some pages I found, you line just doesn't look right.

[http://ubuntuforums.org/showthread.php?t=674446](http://ubuntuforums.org/showthread.php?t=674446)

There is a tutorial for customizing the prompt.


You're a superstar. A much better tutorial than the one I previously used. Problem solved.

---

### Post by skatinjj on 2011-08-03
Just curious, can you post the correct line here?

---

### Post by moadeep on 2011-08-03
> **skatinjj said:**
> Just curious, can you post the correct line here?

Here are the changes I made. I'm not completely certain why it works though.

[PHP]PS1='\n\[\e[0;33m\][\u:\w]$ \[\e[0m\]'[/PHP]

---

