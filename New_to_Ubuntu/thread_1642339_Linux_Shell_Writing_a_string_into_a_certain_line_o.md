---
title: "Linux Shell: Writing a string into a certain line of a file"
date: 2010-12-10
forum: New to Ubuntu
---

### Post by Peter.Paul on 2010-12-10
Hello,

I would like to write something into another file. The file, where is written into already exists and for example looks like[INDENT]A
B
C
D
[/INDENT]Now I want to write "Hello" into line 3 of the file so that it will look like 
[INDENT]A
B
Hello
C
D

[/INDENT]How can I do this?

---

### Post by TeoBigusGeekus on 2010-12-10
```
sed -i "3i\Hello" filename.ext
```

---

### Post by Peter.Paul on 2010-12-10
thanks. This works but I think I need sth. different. Instead of writing it into a separate line, I now like to write it in the existing line.
Like

A
B
C Hello
D

Do you know, how to do this?

---

### Post by TeoBigusGeekus on 2010-12-10
```
sed -i '3cC Hello' filename.ext
```

---

