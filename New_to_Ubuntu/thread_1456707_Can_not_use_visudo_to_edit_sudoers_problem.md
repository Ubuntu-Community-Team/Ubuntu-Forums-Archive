---
title: "Can not use visudo to edit sudoers problem"
date: 2010-04-17
forum: New to Ubuntu
---

### Post by yeehi on 2010-04-17
I need to edit the sudoers file in /etc
I try to use visudo to edit it but I get lost - no text appears for me to edit.

I want to add the following line (somewhere - end/beginning?)

usernameALL=(ALL) NOPASSWD: ALL

How do I get the sudoers text up so I can edit it?
Thank you!

---

### Post by wojox on 2010-04-21
Open a terminal and type:

```
sudo visudo
```

[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

---

