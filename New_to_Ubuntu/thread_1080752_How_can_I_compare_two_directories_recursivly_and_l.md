---
title: "How can I compare two directories recursivly and list the files that are not in both?"
date: 2009-02-25
forum: New to Ubuntu
---

### Post by spacesearcher on 2009-02-25
I really would like to compare two folders of music that i have most of the files are identical but some differ. One of the folders is on my windows partition and one is on ubuntu they are all most identical but sometimes I forgot to put one file in the other to keep them the same. I should have just used the windows folder since Ubuntu can read my windows partition. Now I want to know if there is a way to look at file and see if there is an identical one in the other folder if it can't find one it then list the file. Any ideas of how to accomplish this task?

---

### Post by taurus on 2009-02-25
You mean something like

```
sudo diff -r first_directory second_directory
```

---

### Post by spacesearcher on 2009-02-25
This works very well thank you!!
still a lot to sort through but it reduced my work load a ton :)

---

