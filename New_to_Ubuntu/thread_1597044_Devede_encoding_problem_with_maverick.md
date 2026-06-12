---
title: "Devede encoding problem with maverick"
date: 2010-10-14
forum: New to Ubuntu
---

### Post by steigerjb on 2010-10-14
I am trying to convert a recordmydesktop recording with Devede. I keep getting a mencoder error. How do I resolve this? I need to make the video 1280x720 so I can upload it to youtube. Thanks

---

### Post by hekastos on 2010-10-14
I'm not sure if this is the right forum for this, but anyway I will try, did you try mencoder without any other program is it installed correctly and working properly? (its part of mplayer...)
What error do you get?
for more on mencoder see mplayerhq.hu

---

### Post by steigerjb on 2010-10-15
> **hekastos said:**
> I'm not sure if this is the right forum for this, but anyway I will try, did you try mencoder without any other program is it installed correctly and working properly? (its part of mplayer...)
What error do you get?
for more on mencoder see mplayerhq.hu

yes, I have mencoder. I got the attached error. Its not very helpful.

---

### Post by hekastos on 2010-10-15
try starting mencoder from bash like described in mplayerhq.hu or here
[http://web.njit.edu/all_topics/Prog_Lang_Docs/html/mplayer/encoding.html](http://web.njit.edu/all_topics/Prog_Lang_Docs/html/mplayer/encoding.html)
give him any sample file and encode it to anything else, I would suspect something went wrong with mencoder and if you see his real output in a shell you get a clue what went wrong...
if he works with a sample file, you have to find out the line your program passes to mencoder give it to him in a shell and analyse the output...
gl ;)

---

### Post by steigerjb on 2010-10-15
> **hekastos said:**
> try starting mencoder from bash like described in mplayerhq.hu or here
[http://web.njit.edu/all_topics/Prog_Lang_Docs/html/mplayer/encoding.html](http://web.njit.edu/all_topics/Prog_Lang_Docs/html/mplayer/encoding.html)
give him any sample file and encode it to anything else, I would suspect something went wrong with mencoder and if you see his real output in a shell you get a clue what went wrong...
if he works with a sample file, you have to find out the line your program passes to mencoder give it to him in a shell and analyse the output...
gl ;)

I'm not going to worry about it. I found out kdenlive can stretch the video to 1280x720. I have to edit it anyway, might as well have kdenlive change the size while I'm at it. :tongue:

---

