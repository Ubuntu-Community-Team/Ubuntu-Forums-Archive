---
title: "Getting some strange results changing directories"
date: 2009-01-19
forum: New to Ubuntu
---

### Post by Lostin60's on 2009-01-19
I am new to ubuntu, and have been doing a lot of looking and changing and installing. Lots of "cd". I have been doing just fine until tonight. Now I don't see how any of this is connected, but it seems to be. While trying to install a program I lost my desktop panels (got em back), my double tab complete, and the following.
```
daniel@GLENDA:~$ ls
Desktop  Documents  Examples  Music  Photos  Pictures  Public  Templates
daniel@GLENDA:~$ cd documents
bash: cd: documents: No such file or directory
daniel@GLENDA:~$ cd /documents
bash: cd: /documents: No such file or directory
daniel@GLENDA:~$ cd /
daniel@GLENDA:/$ cd home
daniel@GLENDA:/home$ cd daniel
daniel@GLENDA:~$ cd documents
bash: cd: documents: No such file or directory
daniel@GLENDA:~$ 

```
```
daniel@GLENDA:/$ cd ~/documents
bash: cd: /home/daniel/documents: No such file or directory
daniel@GLENDA:/$ 
```
So, I know the folder is there, but I can't "cd" into it. As you see, I tried it from /home/daniel and I tried it from /.  Any ideas? Any and all help will be appreciated.
[COLOR="White"]aa[/COLOR]

---

### Post by emarkd on 2009-01-19
Linux is case sensitive.  Try:

```
cd Documents
```

---

### Post by Lostin60's on 2009-01-19
> **emarkd said:**
> Linux is case sensitive.  Try:

```
cd Documents
```

Well.....DUH! Thanks, wonder why I never noticed that. Evidently, though, it's only case sensitive when it feels like it. *lshw -C*
and
*lshw -c*
both give the same return....ain't computers grand? LOL
[COLOR="White"]aa[/COLOR]

---

### Post by Lostin60's on 2009-01-19
Almost forgot. I still have lost the tab complete thing in my terminal. Any suggestions 
[color=white]aa[/color]

---

### Post by Terl on 2009-01-19
> **Lostin60's said:**
> Well.....DUH! Thanks, wonder why I never noticed that. Evidently, though, it's only case sensitive when it feels like it. *lshw -C*
and
*lshw -c*
both give the same return....ain't computers grand? LOL
[COLOR="White"]aa[/COLOR]

Not true.  In the case you are describing it works because the little c is the class and the capital C is the alias.  This does not happen often.

By "tab thing" do you mean tab completion?  If you have set up aliases this can affect the tab completion.  Also, in the example you gave if you entered ```
ls d
``` and hit tab it would not have worked, whereas if you had hit ```
ls D
``` and then tab it would have worked.

---

### Post by Lostin60's on 2009-01-19
> **Terl said:**
> Not true.  In the case you are describing it works because the little c is the class and the capital C is the alias.  This does not happen often.

By "tab thing" do you mean tab completion?  If you have set up aliases this can affect the tab completion.  Also, in the example you gave if you entered ```
ls d
``` and hit tab it would not have worked, whereas if you had hit ```
ls D
``` and then tab it would have worked.

Ahhhh. Great info. That explanation would never have occurred to me. Tab completion is, I think, what I mean. The person I learned about it from called it tab tap. And it was working till I tried installing Zimbra. And, no, I have set up no aliases.

I have another question you might be able to answer. There is a longstanding post about how to get Evolution to work with Yahoo. One set of commands gave me this:
```
daniel@GLENDA:~/src/email/ypops/install$ sudo su
[sudo] password for daniel: 
root@GLENDA:/home/daniel/src/email/ypops/install# cat >>/etc/apt/sources.list<<"EOF"
> 

```
I have ocasionaly run into entering a command and getting just a cursor, and usually if I type "daniel@GLENDA" behind the cursor and hit enter, the command will execute. What causes this to happen? I am new to Ubuntu, and much like Scarlett, I am forced to rely on the kindness of strangers...lol.
[COLOR="White"]aa[/COLOR]

---

### Post by snova on 2009-01-19
> **Lostin60's said:**
> I have ocasionaly run into entering a command and getting just a cursor, and usually if I type "daniel@GLENDA" behind the cursor and hit enter, the command will execute. What causes this to happen?

The cat command is waiting for input. In this case, what you type will be appended to the file /etc/apt/sources.list.

When you're done, press Ctrl-D, which will cause it to assume there is no furthur input, and terminate.

---

