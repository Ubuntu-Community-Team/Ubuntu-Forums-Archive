---
title: "Command Line Permissions question"
date: 2009-07-17
forum: New to Ubuntu
---

### Post by anon642 on 2009-07-17
I was moving some backed up email from one user to another to restore.  After I moved the file to where I wanted it I changed ownership of the directory using:
```
sudo chown User2 Mail.sbd
```

And while that let the other user access that directory the files inside of it were still owned by the previous user.

So my question is: Is there a command for me to change ownership/permission to a directory and all of it's subdirectories/files all at once or do I have to set permissions on each file individually?

---

### Post by UltraMathMan on 2009-07-17
```
sudo chown -R User2 Directory
``` will operate on Directory and subfiles and subdirectories. For more options/info see ```
man chown
```

Hope this helps :)

---

### Post by scorp123 on 2009-07-17
> **anon642 said:**
> Is there a command for me to change ownership/permission to a directory and all of it's subdirectories/files all at once ? you mean like **chown -R** ? :D

Try reading the manual in the future, yes?
```
man chown
```

---

### Post by windows-killer on 2009-07-17
> **anon642 said:**
> I was moving some backed up email from one user to another to restore.  After I moved the file to where I wanted it I changed ownership of the directory using:
```
sudo chown User2 Mail.sbd
```

And while that let the other user access that directory the files inside of it were still owned by the previous user.

So my question is: Is there a command for me to change ownership/permission to a directory and all of it's subdirectories/files all at once or do I have to set permissions on each file individually?

Why do you use the command line? is it necessary? or you just like to use it?

---

### Post by anon642 on 2009-07-17
> **UltraMathMan said:**
> ```
sudo chown -R User2 Directory
``` will operate on Directory and subfiles and subdirectories. For more options/info see ```
man chown
```

Hope this helps :)


Thanks that was exactly what I was looking for!:D

---

### Post by anon642 on 2009-07-17
> **scorp123 said:**
> you mean like **chown -R** ? :D

Try reading the manual in the future, yes?
```
man chown
```

At least you didn't say RTFM. :D It was a quick question and I didn't see chown -R mentioned in the ubuntupocketguide.

---

### Post by anon642 on 2009-07-17
> **windows-killer said:**
> Why do you use the command line? is it necessary? or you just like to use it?

*Shrugs* I like the command line better.  And as a newbie I tend to find the command line gets things done faster. A number of things I know how to do on the command line but the GUI frustrates me on some administrative tasks.

---

