---
title: "Command to keep only part of a path"
date: 2009-03-16
forum: New to Ubuntu
---

### Post by runder on 2009-03-16
Hi everyone, I'd like to be able to be able to keep part of a string from the 'pwd' command.  

suppose my pwd gives:
/first/second/third/fourth/fifth
and I'd like to keep anything starting at /third/

Technically, i'd like to be able to do
$ pwd | <something>
so that in the end, it echoes
/third/fourth/fifth

Thanks in advance for your feedback.

---

### Post by lloyd_b on 2009-03-16
```
pwd | grep -o "/third.*"
```will print everything from the first occurrence of "/third" in "pwd" up to the end of the line.

Lloyd B.

---

### Post by runder on 2009-03-16
Thank you :)

---

