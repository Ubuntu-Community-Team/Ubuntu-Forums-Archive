---
title: "How to Move File To $PATH"
date: 2009-01-31
forum: New to Ubuntu
---

### Post by RookieUbuntuUser58 on 2009-01-31
I'm gonna be honest I have no clue what $PATH is?:( Anyway I have a filed called conky_start that I would like to move to $PATH, what code would I use? Thanks in advance for answering a really stupid question, I would assume.

---

### Post by HotShotDJ on 2009-01-31
The best place for custom scripts or user binaries is /home/user/bin.
(obviously, change "user" to the proper user name)

After you create that directory, move the file there.  Next, log out and then log back in (no need to reboot).  /home/user/bin is automatically a part of $PATH (this is the variable that contains the directory tree that the OS will search for commands when you don't specify the full path).

---

### Post by taurus on 2009-01-31
First, make sure it has an executable permission so you can run it.  Then, you can move it to /usr/bin since that should be in your path.

```
sudo mv conky_start /usr/bin
```

---

### Post by taurus on 2009-01-31
> **HotShotDJ said:**
> The best place for custom scripts or user binaries is /home/user/bin.
(obviously, change "user" to the proper user name)

After you create that directory, move the file there.  Next, log out and then log back in (no need to reboot).  /home/user/bin is automatically a part of $PATH (this is the variable that contains the directory tree that the OS will search for commands when you don't specify the full path).

I don't think $HOME/bin is in the path.  You need to edit ~/.bashrc and add that in there.

```
PATH=$PATH:~/bin
export PATH
```

---

### Post by HotShotDJ on 2009-01-31
> **taurus said:**
> I don't think $HOME/bin is in the path.  You need to edit ~/.bashrc and add that in there.

```
PATH=$PATH:~/bin
export PATH
```
Yes.  If ~/bin exists for the user that is logged in, it will automatically be added to the path.  No additional configuration is necessary.  Try it yourself:```
echo $PATH
```
Run it twice... once before you add $HOME/bin and then after you add it and log out then back in (it is not added until the next login).

EDIT: Adding scripts/executables to the system's file system should only be done by experienced users who know exactly what they are doing and why they are doing it.  While there are sometimes very good reasons to place custom scripts and/or binary files in the system path, normally it is "best practice" to make use of $HOME/bin for them.

---

### Post by RookieUbuntuUser58 on 2009-01-31
Thanks for the help guys. 

Also, I did make the file executable using the code ```
chmod +x conky_start
```

---

### Post by handydan918 on 2009-01-31
> **HotShotDJ said:**
> Yes.  If ~/bin exists for the user that is logged in, it will automatically be added to the path.  No additional configuration is necessary.  Try it yourself:```
echo $PATH
```
Run it twice... once before you add $HOME/bin and then after you add it and log out then back in (it is not added until the next login).


Odd...this seems to be true on Ubu, but not on another debian-esque system I run. Wonder why?

---

