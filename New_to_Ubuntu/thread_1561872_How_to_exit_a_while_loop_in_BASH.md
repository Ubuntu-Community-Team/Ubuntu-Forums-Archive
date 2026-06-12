---
title: "How to exit a while loop in BASH?"
date: 2010-08-26
forum: New to Ubuntu
---

### Post by outleradam on 2010-08-26
I have a loop in a bash script.

```

....script....
while read line
do
  ....stuff.....
  if [ $line = "foo" ]
    EXIT THE LOOP
  fi
done < myfile.txt
....script....

```How can I get the loop to exit if [ $line = "foo" ]????

---

### Post by Apollo87 on 2010-08-26
Hello,

You're looking for the 'break' command

```
while read line
do
  ....stuff.....
  if [ $line = "foo" ]
  then
    break
  fi
done < myfile.txt
```

---

### Post by outleradam on 2010-08-26
thank you!  I knew break worked on some statements.  It's really cool that it works on while!   I must do more research to find out where else break can be used.

---

