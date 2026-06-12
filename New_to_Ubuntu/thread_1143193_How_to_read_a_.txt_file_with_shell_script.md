---
title: "How to read a .txt file with shell script?"
date: 2009-04-29
forum: New to Ubuntu
---

### Post by mahimahi42 on 2009-04-29
Hi! I have a simple question about shell scripting. I have the following code:

```

#!/bin/sh
clear
echo "Hello $USER"
echo "Today is \c ";date
exit 0

```

It is run from my desktop, and I want it to show the contents of another text file on my desktop called Todo.txt, which simply says:

```

Can you read this?
I hope so!

```

I'm trying to make a shell script that says the stuff it already does, and reports back a to-do list I'm starting.

And finally, is there a way to make a script that will start automatically when I try to log off that prompts an update to said to-do list?

Thanks for any help!

---

### Post by bodhi.zazen on 2009-04-29
such as ?

```
cat ToDo.txt
```

---

### Post by kerry_s on 2009-04-29
is this all in terminal or you need to get it to a gui?

for example just terminal:
cat ~/Desktop/Todo.txt

with xmessage:
cat ~/Desktop/Todo.txt | xmessage -file "-" -center

maybe you just want the top or bottom:
cat ~/Desktop/Todo.txt | grep head
cat ~/Desktop/Todo.txt | grep tail
or maybe you have dates:
cat ~/Desktop/Todo.txt | grep 4/29


i'm simple i use xpad for notes and osmo for tasks.

---

### Post by mahimahi42 on 2009-04-29
Thanks! Will try!

...After I finish shining my shoes...-_-

---

