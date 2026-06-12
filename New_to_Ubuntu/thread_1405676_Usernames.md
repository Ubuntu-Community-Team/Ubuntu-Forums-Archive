---
title: "Usernames"
date: 2010-02-12
forum: New to Ubuntu
---

### Post by BryanAbel on 2010-02-12
Anybody know of a way to override the username and password when turning the system on? I had a coworker install the Linux Mint sysem on my computer, but she cannot remember the codes. I do not have any disk. I would like to login and change the codes. Please help.

---

### Post by jken146 on 2010-02-12
Restart the computer. When you see  GRUB loading, press escape. Choose Recovery Mode, and if it asks, choose "root prompt" or words to that effect.

When you get to the prompt, look in /home to see what the username is. ```
ls /home
```
Then change the password.
```
passwd USERNAME
```

---

