---
title: "Xchat scripts :S"
date: 2009-05-03
forum: New to Ubuntu
---

### Post by hammad1337 on 2009-05-03
I recently decided to trash mIRC and use XChat.
The problem is, i want to write a simple trigger-based script for xchat and I can't find any decent place to start looking for help and don't have much time either, my exams coming up...
So, anyone would be kind enough to write me a script in python that does the following: (I'll learn how to code in python after my exams are over, promise :) )

> 
#script needs to do this:

on sensing a text trigger (!greet) in (#chan),
  if ( times == 1)
     send private msg to nick (xyz) (hello)
  else if (times == 2)
     send private message to xyz (bye)
  else
     set times = 0
end

#hope you understand what m trying to do/say


---

### Post by hammad1337 on 2009-05-03
bump -_-

---

### Post by ibuclaw on 2009-05-03
The xchat API is here: [http://www.xchat.org/docs/plugin20.html](http://www.xchat.org/docs/plugin20.html)

What language are you wanting to use?

edit:
Python's API is here: [http://labix.org/xchat-python](http://labix.org/xchat-python)

Regards
Iain

---

### Post by kostkon on 2009-05-03
For Python check [here]("http://xchat.org/docs/xchatpython.html").

EDIT: whoops, *tinivole*, I didn't see your edit.

---

### Post by ibuclaw on 2009-05-03
> **kostkon said:**
> For Python check [here]("http://xchat.org/docs/xchatpython.html").

EDIT: whoops, *tinivole*, I didn't see your edit.

There is more than one way to skin a cat ;)

---

### Post by hammad1337 on 2009-05-03
Thank you all. I ll definitely see into these docs.
But right now, I urgently need a pre-made script which I can modify to suit my needs. Believe me, m not a "script kiddie" but right now, m hard pressed for time.
Thanks for those links again. :D

---

