---
title: "How can I kill pts/1"
date: 2009-07-29
forum: New to Ubuntu
---

### Post by rovinsan on 2009-07-29
user1    tty7         2009-07-29 10:38 (:0)
user1    pts/0        2009-07-29 10:40 (:0.0)
user1    pts/1        2009-07-29 11:23 (:0.0)

Some times my machine is not responding. Except Terminal ,numlock key and Restart key. I can use new terminal, but rest of all windows are hanged.

How can I kill pts/1? 
When I took new terminal type who, then I can see the last pts with time, which cause my machine's problem. But I don't know how to kill that pts.

---

### Post by McNils on 2009-07-29
i dont know is there is a simpler way but this is how I do it.
ps -t pts/1 | awk '/[0-9]/ {print $1}' | xargs sudo kill 
ps -t pts/1 | awk '/[0-9]/ {print $1}' | xargs sudo kill -9

---

### Post by escom.alex on 2009-12-04
Howdy!

I use :

**sudo  kill  -9  [PID]**

example:

9749     ?           00:00:16 konsole         
9751     pts/2     00:00:01 bash            
_19262   pts/2     00:00:00 gift-setup_

*$ sudo kill -9 19262*
[1]+  Killed                  gift-setup  (wd: ~)


And work well for pts/1 and pts/2. I hope to be help you with this

---

