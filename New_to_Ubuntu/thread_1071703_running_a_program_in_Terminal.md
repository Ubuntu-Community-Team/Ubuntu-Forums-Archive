---
title: "running a program in Terminal"
date: 2009-02-16
forum: New to Ubuntu
---

### Post by brandon82 on 2009-02-16
I have written a very simple program in C, and compiled it with gcc. What syntax do i need to use to run this program from the Terminal? I've tried "FILE <program_name>" with no luck, but when i drag the actual icon into terminal, it will work. It seems like a simple solution that I'm missing here....

---

### Post by SlalomMan on 2009-02-16
You should just be able to cd to the directory and run it by typing "myfile.cpp".

---

### Post by RomeReactor on 2009-02-16
Hi. If you didn't save the file to /bin, /usr/bin, or /opt, make sure you use the file's complete path; example:
```
/home/brandon/filename
```
Or, cd to the directory and:
```
./filename
```

---

