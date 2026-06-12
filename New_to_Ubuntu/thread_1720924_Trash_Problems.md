---
title: "Trash Problems"
date: 2011-04-03
forum: New to Ubuntu
---

### Post by dieselglock on 2011-04-03
Hello,

I have read most of the posts and suggestions about trash problems but can not find the exact problem I have.

Not sure what i did but my trash icon when running gksu nautilus gives this error:

"The folder contents could not be displayed" and "Sorry, could not display all the contents of "trash": Operation not supported.

Although I don't think there is anything in the trash.

Running 10.04-2 LTS

Thanks

Len

---

### Post by dcsoldschool53 on 2011-04-03
**gksu nautilus is the root command, and it opens nautilus in root. User trash is located in /.local/share/Trash folder in /home. Now, I have 3 different computer running ubuntu 9.04, 9.10, and 10.10. They all say the same thing that you displayed on this thread. I think that is the way it is suppose to work when it's empty, or when it's not empty.**

---

### Post by dieselglock on 2011-04-03
Just never noticed this before. I guess if its normal then I must of missed it silly me.

---

### Post by 311005901 on 2011-04-03
In my experience, running "sudo nautilus" or "gksu nautilus" doesn't have Trash.
Since it is the superuser or administrator, you've got to be careful! There isn't an easy safety net if you need that file undeleted.

---

### Post by dieselglock on 2011-04-03
> **311005901 said:**
> In my experience, running "sudo nautilus" or "gksu nautilus" doesn't have Trash.
Since it is the superuser or administrator, you've got to be careful! There isn't an easy safety net if you need that file undeleted.

I understand. I just thought the error was strange. Thanks for the responses.

---

