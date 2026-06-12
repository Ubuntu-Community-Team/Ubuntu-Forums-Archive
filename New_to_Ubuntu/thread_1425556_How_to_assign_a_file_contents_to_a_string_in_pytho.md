---
title: "How to assign a file contents to a string in python"
date: 2010-03-09
forum: New to Ubuntu
---

### Post by dharanitharan on 2010-03-09
Hi friends,
            I'm a python beginner. How can i assign the file content to a string in python language. i can use read function to read from a file. But i don't know how to assign read content to a string. Help me friends. I'm really need of it.



Thanks,
Dharanitharan.A

---

### Post by DaithiF on 2010-03-09
there are many ways, one example:
```

f = open('somefile', 'r')
contents = f.read()
f.close()

```

---

### Post by dharanitharan on 2010-03-09
thanks man :)

---

### Post by dharanitharan on 2010-03-09
Hi daithif,
             How to search a particular string in a list...

---

### Post by DaithiF on 2010-03-09
Hi, 
Have you read the python tutorial?  [http://docs.python.org/tutorial/index.html](http://docs.python.org/tutorial/index.html)

it will be a more efficient use of your time I think than posting individual questions here and waiting for a response each time.

having said that:
```
if 'b' in [ 'a', 'b', 'c' ]:

```

---

