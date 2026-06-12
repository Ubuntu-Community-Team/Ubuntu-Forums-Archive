---
title: "Help! Can't boot after advice..."
date: 2009-07-21
forum: New to Ubuntu
---

### Post by OllieGab on 2009-07-21
Some time ago a message box about ownership of the home folder came up during booting (I was then using Ubuntu 8.10, now using 9.4), which just needed 'OK-ing'.
To get rid of this I was advised in the forum to do the following:

sudo chmod 700 /home/ubuntu
password:
sudo chmod 644 /home/ubuntu/.dmrc

This worked fine and the problem disappeared.
The same problem turned up again some time ago and I did exactly the same.
However, now my machine doesn't boot at all, stops at the first brown screen.
I get several error messages:
- ICE auth. file has not been updated
- problem with configuration file...
- Nautilus cannot create /home/user/.....

What to do? Anyway to undo what I did?

---

### Post by eljalill on 2009-07-21
You should be able to undo anything you did using the live CD. For this, make sure that the boot order in your bios is set to boot from CD first (but it often already is, so you could just try putting an ubuntu CD and then boot).

But I am not sure, what exactly you were doing in changing the mode, but I am also not sure what the original problem was... it would be useful if you could post a link to the thread in which you got that advice. That makes it easier to understand which problem you were trying to fix in the first place.

---

### Post by nothingspecial on 2009-07-21
Try
```

chmod 644 /home/*username*/.ICEauthority
```

```
chown -R *username:username* /home/*username*
```

---

### Post by OllieGab on 2009-07-21
The original problem was actually raised by myself:

[URL="http://ubuntuforums.org/showthread.php?t=1062651"]http://ubuntuforums.org/showthread.php?t=1062651
[/URL]

So should I try the above while in CD live mode? 
As I can't get booted up now....

---

### Post by bacil on 2009-07-21
You should be able to boot to console.

eg. boot your computer then while i guess you have black scree press Alt+F1 or any other Function except F7 (thats generally graphical interface) 

then you should be able to login in cosole mode and do changes sugested above

---

### Post by OllieGab on 2009-07-21
Unfortunately I just get a message saying "there is no such file or directory"...
It seems I can't get into it at all!

There must be something I can do!:confused:

---

### Post by bacil on 2009-07-21
can you boot livecd and have look for missing file ?

---

### Post by nothingspecial on 2009-07-21
Does the grub dialogue appear when you turn the computer on. If it does press escape as soon as you see it then log into the failsafe terminal or whatever it`s called.

---

### Post by OllieGab on 2009-07-21
I am now getting bit desperate!#-o
I have managed to start up a console and I have tried the 'chmod 644... and 'chown -R....' but unfortunately without any success.
The question is; what do I actually do when I "get in there"?
My computer doesn't boot up but stops at a default wallpaper without any icons whatsoever. There are some error messages (see previous posts) indicating that there is a problem with the .IECauthority file, or some sort of problem with the ownership of my computer.
I can 'ls' my user folder to confirm that all my own directories and files are there but I can't actually access (change to that directory)as it says 'access denied'.
So where do I start? What could be the problem?

---

### Post by jeppewinther on 2009-07-21
It appears you, as a user, have lost ownership and privileges over your home directory somehow. Note that  you can still access everything as long as you stick a sudo infront of the command.
```
sudo cd <folder>]

To troubleshoot,
[CODE]ls -l
```
should give you some clues. 

What you're looking for is the first set of seemingly random letters, and the two lines telling you which user and group owns the files/folders in question.

A "healthy" folder and file will look somewhat like this. random is my Username and Group.
```
drwxrwxr-x   8 random random     4096 2009-07-21 05:42 stuff
-rw-rw-r--   1 random random      243 2009-07-21 05:42 Text File

```
d means directory, r is read, w is write, x is execute. First three letters is owner, next is group, then guest/everyone.

---

### Post by nothingspecial on 2009-07-21
Ok, it seems you are going to have to login as root.

I can`t tell you how to do that - you`ll have to use google.

when you have (substitute [COLOR="Red"]yourusername[/COLOR] for your actual username)```


chown -R [COLOR="Red"]yourusername[/COLOR]:[COLOR="Red"]yourusername[/COLOR] /home/[COLOR="Red"]yourusername[/COLOR]
```

```
chmod 644 /home/[COLOR="Red"]yourusername[/COLOR]/.ICEauthority
``````


chmod 644 /home/[COLOR="Red"]yourusername[/COLOR]/.dmrc
```

If that doesn`t work, don`t worry, this is still fixable.

---

### Post by OllieGab on 2009-07-21
By using ls -l I get a long list of directories and files, in the format you explained. They all say root, root for owner and user.

So from here?

I get a permission denied message when I try to access my /home/username folder and it seems that in there is the file .IECauthority that causes me the problem. Or so I guess anyway.
The home directory says 'drwxrwx'

---

### Post by OllieGab on 2009-07-21
I think I've managed it myself now......
I used:
user@host:/home/user$ sudo chmod 777 -R /home/

which did the trick. The initial error message box still comes up when I'm booting but I think I won't bother.
It's a small price to pay; clicking the OK button!!

Thanks for all the input:P

---

