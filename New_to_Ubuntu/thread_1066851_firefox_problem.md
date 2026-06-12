---
title: "firefox problem"
date: 2009-02-11
forum: New to Ubuntu
---

### Post by cosine352 on 2009-02-11
Hi friend,
I have just updated my Ubuntu8.10 today and can not run firefox anymore. Now I am using SeaMonkey. Look at the attachment. Now the firefox looks like this.

I have tried 
> sudo apt-get reinstall firefox
sudo apt-get remove firefox
sudo apt-get install firefox
sudo apt-get install firefox build-essential

no luck

---

### Post by fooman on 2009-02-11
try deleting the firefox config file...see if that helps.  firefox will recreate the file when you start it again.

close firefox if it is open.  then open a terminal and type or copy/paste the following:

```
rm -rf ~/.mozilla
```then restart firefox.

hope that helps.

---

### Post by cosine352 on 2009-02-11
Do not worry guys. I have found the problem. The thing is firefox was running in the background and was the cause of this problem. I have to kill firefox and restarted it. Now it is working fine.

---

### Post by lykwydchykyn on 2009-02-11
> **fooman said:**
> try deleting the firefox config file...see if that helps.  firefox will recreate the file when you start it again.

close firefox if it is open.  then open a terminal and type or copy/paste the following:

```
rm -rf ~/.mozilla
```then restart firefox.

hope that helps.

Uh.... do that only if you want to lose all your bookmarks, extensions, theme settings, saved passwords, and anything else you've done to customize firefox.

You might want to try launching firefox in safe mode first to see if that helps.  That will at least tell you if it's something in your profile.

```

firefox -safe-mode

```

---

