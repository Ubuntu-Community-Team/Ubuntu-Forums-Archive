---
title: "Jaunty Terminal defaults to root directory?"
date: 2009-05-04
forum: New to Ubuntu
---

### Post by beastrace91 on 2009-05-04
My terminal in Jaunty is defaulting to my root "/" directory instead of my home directory "~/" is there a setting I can change so it defaults to my home directory like I am used to?

~Jeff

---

### Post by michy99 on 2009-05-04
In the file /etc/passwd there should be a line (probably the last one) that starts with your username and looks like

```
username:x:1000:1000:Real Name,,,:/home/username:/bin/bash
```

where 'username' is your user name. The '/home/username' tells the terminal where to start.

---

### Post by Dr Small on 2009-05-04
> **michy99 said:**
> In the file /etc/passwd there should be a line (probably the last one) that starts with your username and looks like

```
username:x:1000:1000:Real Name,,,:/home/username:/bin/bash
```

where 'username' is your user name. The '/home/username' tells the terminal where to start.
Actually, that tells the system where the user's home directory is, not the current working directory when the terminal is opened.

---

### Post by michy99 on 2009-05-04
You are correct. Brain's working a little fuzzy today.

---

### Post by Dr Small on 2009-05-04
> **michy99 said:**
> You are correct. Brain's working a little fuzzy today.
No problem. We all have our moments ;)

---

### Post by neopsalmist on 2009-05-04
in bash, type HOME=/home/yourname and it will fix it for that session. I am not sure whether that change will stick though

---

### Post by ibuclaw on 2009-05-04
I think I had this problem for a day or two...

I may have reinstalled bash to fix it, but my memory isn't what it used to be ;)

```
sudo apt-get --reinstall install bash
```

Regards
Iain

---

### Post by beastrace91 on 2009-05-05
Hrm, reinstalling bash didn't do the trick, any other ideas?

~Jeff

---

### Post by decoherence on 2009-05-05
I can reproduce this behavior by putting

cd /

in my ~/.bashrc or /etc/bash.bashrc. you might want to check for something similar

---

### Post by akaihola on 2009-06-02
I have the same issue, and I've double-checked .bashrc and /etc/bash.bashrc. Continuing to hunt down the cause...

**Update:** This happens only when I launch Gnome-terminal with a shortcut key I've defined in GNOME. Using the application menu or the Run dialog (Alt-F2) sets the working directory correctly.

So apparently the working directory is set to the home directory after GNOME (or at least its shortcut key handler component) is loaded.

---

