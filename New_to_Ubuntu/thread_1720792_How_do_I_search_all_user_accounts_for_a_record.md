---
title: "How do I search all user accounts for a record?"
date: 2011-04-03
forum: New to Ubuntu
---

### Post by ekuemoah on 2011-04-03
I am working with ubuntu.  I have several user accounts on the network.  I am signed in as the administrator and need to search all the user accounts for a document. I know the word in the document and need to see which user accounts contain the document.  How would I do this? Can I as the root or administrator search all the accounts even if they are password protected.

What is the command I write from the terminal to do this? I think part of it is 

            ls -l|grep "w*rd"

which directory do I need to be in or set to in order to search all the user accounts on my server or network?

If I am on a unix or linux network, will the commands used by the same?

Thank You

---

### Post by TeoBigusGeekus on 2011-04-03
```
find / -iname "putregularexpressionhere" 2>/dev/null
```
I don't know whether it will go through all user accounts though.
Give it a shot...

---

