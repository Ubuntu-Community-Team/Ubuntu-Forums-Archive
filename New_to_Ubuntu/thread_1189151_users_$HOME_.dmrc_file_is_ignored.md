---
title: "users $HOME .dmrc file is ignored"
date: 2009-06-16
forum: New to Ubuntu
---

### Post by hapkidoman on 2009-06-16
Hi everyone.  I'm using ubuntu 9.04 and have always had the users $HOME .dmrc file is being ignored pop up every time I logged on.  I wanted to fix that so I used this command from the terminal:

chmod 644 .dmrc
chmod 700 ~

I then got the message:  chmod: cannot access '.dmrc': no such file or directory

Now, I can't even log in to my account.  I have to fall back to the failsafe terminal.

Is there anyway that I can get my permissions back so that I can log back in?  I'm really hoping I can get this fixed as I have a lot of saved files I need access to.

---

### Post by nothingspecial on 2009-06-16
Try changing your home to 755

```
chmod -R 755 /home/your_username/
```

and if you were not in your home when you executed the 1st command it should have been
```

chmod 644 /home/your_username/.dmrc 
```

Does it give any errors when you try to log in?

And as long as you`ve not totaly borked your system, your files are recoverable.

---

### Post by Azrael3000 on 2009-06-16
does this file even exist?
i.e. if you try
```
ls -la .dmrc
```
does anything show up? See my output:
```
***@***:~$ ls -la .dmrc
-rw------- 1 *** *** 28 2009-06-16 18:49 .dmrc

```
The only thing that is written in there is:
```


[Desktop]
Session=default

```
And that's about it.

---

### Post by philinux on 2009-06-16
For furture reference.

[https://help.ubuntu.com/community/dmrcErrors](https://help.ubuntu.com/community/dmrcErrors)

I've got this bookmarked just in case.

---

### Post by hapkidoman on 2009-06-16
[QUOTE=nothingspecial;7467505]Try changing your home to 755

```
chmod -R 755 /home/your_username/
```

This worked beautifully and now I'm back to where I was before....with a working desktop and no 'users $HOME .dmrc.......' pop up!!!!

THANK YOU SOOO MUCH!!!!!  You just made my day!

---

### Post by hapkidoman on 2009-06-16
Now...How do I change this to 'resolved'?

---

### Post by nothingspecial on 2009-06-16
No problem.

In your thread choose

Edit > Go Advanced

And then you can change your thread title. Just put solved in bold before the original one.

Cheers

---

