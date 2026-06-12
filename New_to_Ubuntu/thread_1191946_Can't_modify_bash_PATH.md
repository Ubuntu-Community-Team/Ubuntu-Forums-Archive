---
title: "Can't modify bash PATH"
date: 2009-06-19
forum: New to Ubuntu
---

### Post by Leporello on 2009-06-19
I'm trying to add a scripts directory to my bash path. I added the following lines to the end of my .bashrc file:

```

PATH = $PATH:/home/djones/Scripts
export PATH

```

When I run source .bashrc in the terminal I get the following output:

```

source .bashrc
bash: PATH: command not found

```

So it looks like bash is trying to run the assignment for $PATH as a command. I've modified the path before and I could have sworn that this is exactly what I've done, so I'm mystified as to why it's not working now.

---

### Post by Idefix82 on 2009-06-19
Not sure but try removing the spaces from
```
PATH = ...
```

---

### Post by synapsys on 2009-06-19
[http://ubuntu-ky.ubuntuforums.org/showthread.php?p=7420772](http://ubuntu-ky.ubuntuforums.org/showthread.php?p=7420772)

---

### Post by adrianx on 2009-06-19
I normally use .bash_profile

Anyway, spaces matter. It should be:
```

PATH=$PATH:/home/djones/Scripts
export PATH

```

**Edit:** I was a bit slow, Idefix82 beat me to it.

---

### Post by Leporello on 2009-06-19
Ah, of course, the spaces! Thanks everyone.

---

### Post by bodhi.zazen on 2009-06-19
Which can be simplified to one line

```
export PATH=$PATH:/home/djones/Scripts
```And if you wish to go one setp further, simply use ~/bin rather then ~/Scripts

look at ~/.profile and you will see 

```
if [ -d "$HOME/bin" ] ; then
    PATH="$HOME/bin:$PATH"
fi
```

so it is all automagic if you use ~/bin rather then ~/Scripts (which you may or may not wish of course).

---

### Post by Brian Vaughan on 2009-06-19
I hope you'll forgive the tangent.

I was just looking at my $PATH, and noticed that it had my /home/myname/bin at the start of the path. I remembered being advised that that was a security hole. It appears to be set in my .profile:
> 
# set PATH so it includes user's private bin if it exists
if [ -d "$HOME/bin" ] ; then
    PATH="$HOME/bin:$PATH"
fi

And **Learning the bash Shell**, by Cameron Newham and Bill Rosenblatt, suggests instead:
> PATH=$PATH":/home/you/bin"

The book offers, as an example of this being a security hole, its exploitation in conjunction with a script with the suid bit set.

Since I didn't write .profile, I assume it's set up in the process of creating an account. I'm wondering if there's an easy way to change it for each account -- and also, whether it is in fact really worth worrying about.

---

### Post by bodhi.zazen on 2009-06-19
It is a (minor) security hole as the shell searches locations on your path in order.

So if ~/bin is first on the list, and the directory is world writable or somebody cracks your account, they can write a malignant script and place is in ~/bin (such as ~/bin/sudo).

When you sudo , ~/bin/sudo would be called (as it is first on the (PATH) list).

The "solution" is to make ~/bin private, make any scripts to be run as root owned by root, and use full paths to executable in scripts.

If you account is cracked, you are in deep doodo no matter what you do short of Apparmor or Selinux, and even then ...

These files (.bashrc , .profile) are copied from /etc/skel when you create a new user account. Edit those files if you wist to make system wide changes for new users. Existing users would be manual or scripted.

---

### Post by adrianx on 2009-06-19
I'm not qualified to comment, but I've just noticed it too. After creating a bin directory in my home and running source .profile!

I would hate for my "own little script" to take precedence over a script that already exists. :shock:

---

### Post by Rubicon_82 on 2009-06-19
> **adrianx said:**
> I'm not qualified to comment, but I've just noticed it too. After creating a bin directory in my home and running source .profile!

I would hate for my "own little script" to take precedence over a script that already exists. :shock:

One solution would be to append '~/bin' to the end of $PATH.  For example, in ~/.profile

Change
```

if [ -d ~/bin ] ; then
    PATH=~/bin:"${PATH}"
fi
```
to
```

if [ -d ~/bin ] ; then
    PATH="${PATH}":~/bin
fi
```
then logout and login again for the changes to take effect.

This will make any scripts in ~/bin have lower priority than anything else in $PATH.  For example, it ~/bin/test exists and is executable, and you try:
```

cd ~
test
```

You'll end up running /usr/bin/test instead.

---

