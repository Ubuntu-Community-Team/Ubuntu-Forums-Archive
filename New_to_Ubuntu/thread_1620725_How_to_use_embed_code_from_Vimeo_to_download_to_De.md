---
title: "How to use embed code from Vimeo to download to Desktop?"
date: 2010-11-13
forum: New to Ubuntu
---

### Post by LearningPerson on 2010-11-13
Hello,  I'm using Karmic 9.10 and have an embed code I want to use to download a Vimeo video to my Desktop.  I have tried using the terminal but evidently don't have the correct language.  A program might be better.

I wrote     dl   and the full code.  The error came back:  bash: syntax error near unexpected token `<'

Please help.  Thanks.

Sharon

---

### Post by LearningPerson on 2010-11-13
Hi,

I think I am not supposed to download a Vimeo video to my Desktop so I'll withdraw this question.  

Sharon

---

### Post by chaanakya_chiraag on 2010-11-13
Well the error occurred because bash (the shell) tried to interpret the symbol "<", which is not what you want...the same thing occurs with > and other symbols like $.

---

