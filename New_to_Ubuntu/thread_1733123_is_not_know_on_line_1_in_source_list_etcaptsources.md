---
title: "is not know on line 1 in source list /etc/apt/sources.list.d/medibuntu.list"
date: 2011-04-18
forum: New to Ubuntu
---

### Post by BMBlues on 2011-04-18
Hi, i'm too new here, i've been using ubuntu for while, anyway today i got this error everytime i try to update, open the software center or doing any system task
i checked the similar topics with the same problem but they talk about check the list delete the line and update. There's nothing in my line.
Well... help.

---

### Post by wojox on 2011-04-18
What does the file look like:

```
cat /etc/apt/sources.list.d/medibuntu.list
```

---

### Post by BMBlues on 2011-04-19
Nothing happened, i pasted it two times but nothing seems to appear

---

### Post by plucky on 2011-04-19
> **BMBlues said:**
> Nothing happened, i pasted it two times but nothing seems to appear

Post output of ```
ls -l /etc/apt/sources.list.d/
```

---

### Post by 3rdalbum on 2011-04-19
1. In the terminal, go to Edit > Copy, don't use Control-C.

2. Don't close the terminal before pasting into the forum.

Delete the file "/etc/apt/sources.list.d/medibuntu.list" by putting this into the terminal:

```
sudo rm etc/apt/sources.list.d/medibuntu.list
```

and try adding the Medibuntu repository again by using the instructions on their website.

---

### Post by plucky on 2011-04-19
> sudo rm etc/apt/sources.list.d/medibuntu.list

Will result in > rm: cannot remove `etc/apt/sources.list.d/medibuntu.list': No such file or directory

That is because it should be ```
sudo rm /etc/apt/sources.list.d/medibuntu.list
```

Good Luck

---

### Post by BMBlues on 2011-04-19
> **plucky said:**
> Post output of ```
ls -l /etc/apt/sources.list.d/
```
  this came out
```
total 4
-rw-r--r-- 1 root root 203 2011-04-18 22:30 mediubuntu.list
```and this showed me up when i pasted the another code (by plucky)

```
rm: cannot remove `/etc/apt/sources.list.d/medibuntu.list': No such file or directory
```

anyway the problem is still there, that is bad right?

---

### Post by coffeecat on 2011-04-19
> **plucky said:**
> Post output of ```
ls -l /etc/apt/sources.list.d/
```

> **BMBlues said:**
> this came out
```
total 4
-rw-r--r-- 1 root root 203 2011-04-18 22:30 mediubuntu.list
```

Did you copy and paste that output? If so, it explains why you can't 'rm' medibuntu.list, why wojox's command "cat /etc/apt/sources.list.d/medibuntu.list" didn't work, and why possibly you are getting the error in the first place.

Your *.list file is mediubuntu.list which is wrong, not medibuntu.list. It should be medibuntu.list.

Try this:

```
sudo mv /etc/apt/sources.list.d/mediubuntu.list /etc/apt/sources.list.d/medibuntu.list 
```And then try updating the system.

---

### Post by BMBlues on 2011-04-19
I tried the code, but nothing.
I went to the file directly, coffeecat was right

```
--2011-04-18 22:30:36--  http://www.mediubuntu.org/sources.list.d/hardly.list
Resolving www.mediubuntu.org... failed: Name or service not known.
wget: unable to resolve host address `www.mediubuntu.org'
```I tried to edit it but told me bout have permissions to do it, is just by terminal right?

Nevermind, i edited, now is working
Thanks to all, you're really helpful.

---

