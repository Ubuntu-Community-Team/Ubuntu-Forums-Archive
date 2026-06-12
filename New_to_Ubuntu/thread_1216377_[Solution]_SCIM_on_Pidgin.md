---
title: "[Solution] SCIM on Pidgin"
date: 2009-07-18
forum: New to Ubuntu
---

### Post by in_flu_ence on 2009-07-18
SCIM might work for many applications (e.g. firefox, songbird, etc). However, many people found that it doesn't integrate well with Pidgin.

Here are two solutions that I found on a website

Temporary Solution:
Whenever you are in the conversation window in Pidgin,
1) Right click at the message input box.
2) Select "Input Method"
3) Click on "System (SCIM Bridge Input Method)" once again even though it has been chosen by default.
4) Done.

Permanent Solution:
1) vim /etc/scim/config
2) Set /FrontEnd/X11/Dynamic as True
3) Reset SCIM & Pidgin
4) Done.

Hope this helps.

---

### Post by khc on 2009-07-19
> **in_flu_ence said:**
> SCIM might work for many applications (e.g. firefox, songbird, etc). However, many people found that it doesn't integrate well with Pidgin.

How does it not work well with Pidgin?

---

### Post by in_flu_ence on 2009-07-20
Personal experience actually. SCIM works without tweaking for all the applications (Firefox, text, openoffice, etc). So I tried to search for a solution for myself and found that there were quite a number of threads on similar issue.

At the end, I found a solution in one of the websites and i just write it here so someone else might need it.

---

### Post by fatigue on 2009-08-14
2) Set /FrontEnd/X11/Dynamic as True


This method didnt work for me. 

But i noticed that if you upgrade from 8.10, SCIM works in pidgin. If you install 9.04, most likely SCIM doesn't work in pidgin. If you want to use Japanese/Chinese input, I wouldn't recommend to use 9.04.
Let's hope they fix in next ubuntu.

---

### Post by executorvs on 2009-09-15
any fix for this found for Jaunty? I can't get either of the listed to work.

---

### Post by dwhan8608 on 2009-12-05
Actually, this solution worked for me.
Now I can change the input method using Ctrl+Space as usual.
I'm using Karmic.

---

### Post by dwhan8608 on 2009-12-05
Sorry, double post...

---

