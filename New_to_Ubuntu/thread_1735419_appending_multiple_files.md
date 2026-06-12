---
title: "appending multiple files"
date: 2011-04-21
forum: New to Ubuntu
---

### Post by Dr.Joker on 2011-04-21
Hi guys,

I have a very noobish question. Let's say I have two files, file1.txt and file2.txt and I want to append them to the end of final.txt. If I had just one file I would do

cat file1.txt >> final.txt

But if I have two files I tried

cat file1.txt | cat file2.txt >> final.txt

and this only appends file2.txt. I don't want to have to write two commands like

cat file1.txt >> final.txt
cat file2.txt >> final.txt

Any help? This should be very easy to do. Thanks.

---

### Post by seawolf167 on 2011-04-21
Something like this?

```
cat file1.txt >> final.txt && cat file2.txt >> final.txt
```

---

### Post by Dr.Joker on 2011-04-21
Thanks seawolf, that would work, but that's the same as just writing the two commands separately. Actually I found the answer, it is very easy, I was such a noob :) I can just write

cat file1.txt file2.txt >> final.txt

Haha, this was embarassing :)

---

