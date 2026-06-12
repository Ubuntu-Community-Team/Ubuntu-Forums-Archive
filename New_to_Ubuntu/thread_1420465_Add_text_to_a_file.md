---
title: "Add text to a file"
date: 2010-03-03
forum: New to Ubuntu
---

### Post by iggy pop on 2010-03-03
I am still trying to get to grips with the command line and would like to know how i could add text/data to a file.

For example, if i wanted to add more information to a certain file without deleting any data which the file may already contain.

Thanks all

---

### Post by r-senior on 2010-03-03
You can use shell redirection to append to a file. e.g.

$ ls >> temp.txt

---

### Post by muteXe on 2010-03-03
[http://www.redhat.com/docs/manuals/linux/RHL-7.1-Manual/getting-started-guide/s1-navigating-usingcat.html](http://www.redhat.com/docs/manuals/linux/RHL-7.1-Manual/getting-started-guide/s1-navigating-usingcat.html)

check out the bit at the bottom: "Appending Standard Output"

---

### Post by leg on 2010-03-03
You could also use a terminal text editor like nano.

---

### Post by iggy pop on 2010-03-03
Have been using: echo 'text here!' >> <filename>
Thanks for the help everyone

---

