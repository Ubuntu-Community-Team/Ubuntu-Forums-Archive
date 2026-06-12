---
title: "Using sed to transform text"
date: 2011-01-01
forum: New to Ubuntu
---

### Post by Ellume on 2011-01-01
I'm using ubuntu 10.10. In an effort to learn some basics I decided I would try to transform a text file using sed. I want to have it so it only keeps the capital letters in the text file. I've glanced at the man page and a bit on the net, and finding it kinda confusing. Could someone show me what the command would be? And if possible explain it briefly? Or is there another command that would work better?

---

### Post by wojox on 2011-01-01
Would you rather me show you? Or would you rather learn SED with Regular Expression's yourself (hint, hint)?

---

### Post by Ellume on 2011-01-01
I've more or less jumped headfirst into the water with this and am kinda flailing around. I had to look up 'Regular Expression' to even understand what you were saying. I am learning a fair bit and think I'm starting to get the basics of what I need as well. I'm thinking I need to do something like ```
sed 's/[a-z]/'
```which I understand as if the character is a-z then it is replaced with nothing. Not sure if that will work though. And I think I need to pipe it with another command to access the text file.

EDIT: Now that I'm looking over regular expressions things are making a lot more sense. Thanks just for asking your question. I found tutorials going over both regular expressions and the sed command :D

---

