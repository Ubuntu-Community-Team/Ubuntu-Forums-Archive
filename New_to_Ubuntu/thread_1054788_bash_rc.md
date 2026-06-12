---
title: "bash rc"
date: 2009-01-30
forum: New to Ubuntu
---

### Post by abhaypd on 2009-01-30
Hello,
I modified bash rc and included a directory. i checked it in the path using echo command. By mistake i ran source twice and so i have two entries in path.
How do i delete the additional entry ?

---

### Post by blueridgedog on 2009-01-30
Can you post your bash_rc file?

---

### Post by binbash on 2009-01-31
bash post your bash_rc so we can fix it

---

### Post by PirateChef on 2009-01-31
You can edit your .bashrc in any text editor, but in order to save your changes you'll have to be root.

Try
```
sudo pico ~/.bashrc
```

Enter your password, then edit away. Save with CTRL-X.

---

### Post by Nepherte on 2009-01-31
.bashrc is a user owned file, no need for admin privileges at all. You can drop the sudo prefix.

---

