---
title: "ls"
date: 2009-07-06
forum: New to Ubuntu
---

### Post by Wyvernoid on 2009-07-06
Is there a ls counterpart of the dos command switch dir /p? If there are too many things to display, let the output pause at a full page.

Or, is there a way to direct the output of ls into a text file?

Sorry for the extremely rookish questions.

---

### Post by derekeverett on 2009-07-06
```
ls > whatever/path/you/like/textfile.txt
```

or 
```
ls | more
```

---

### Post by Wyvernoid on 2009-07-06
What exactly do > and | do, may I ask?

---

### Post by derekeverett on 2009-07-06
> redirects the output of any command to a text file

| pipes the output of a command to another command

more displays one page at a time. you continue by pressing enter to go one line at a time or the space bar for 1 page at a time

---

### Post by diablo75 on 2009-07-06
You might check out this blog I did a while back:

[http://davestechsupport.com/blog/2008/06/14/the-linux-terminal-for-beginners/](http://davestechsupport.com/blog/2008/06/14/the-linux-terminal-for-beginners/)

---

### Post by s.fox on 2009-07-06
Hi,

[This ]("https://help.ubuntu.com/8.04/basic-commands/C/files-directories-commands.html")may be of some use to you.

-Silver Fox

---

### Post by Wyvernoid on 2009-07-06
Okay, thanks all.

---

### Post by derekeverett on 2009-07-06
diablo75,

I just checked out your blog.. good work there man that was nice.

Liked your list of 10 things to do after installing Ubuntu too!

---

### Post by Paddy Landau on 2009-07-06
You can also use
```
ls | less
```This allows you to scroll back as well as forward.

(No spaces are necessary; so, 'ls | more' is the same as 'ls|more'.)

---

### Post by diablo75 on 2009-07-06
> **derekeverett said:**
> diablo75,

I just checked out your blog.. good work there man that was nice.

Liked your list of 10 things to do after installing Ubuntu too!

Hey thanks!
:guitar:

---

