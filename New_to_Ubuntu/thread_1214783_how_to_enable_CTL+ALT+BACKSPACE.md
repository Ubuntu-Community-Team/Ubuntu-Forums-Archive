---
title: "how to enable CTL+ALT+BACKSPACE"
date: 2009-07-16
forum: New to Ubuntu
---

### Post by ubudog on 2009-07-16
I noticed that in 9.04 CTL+ALT+BACKSPACE was disabled.  How do I enable it?

---

### Post by Elfy on 2009-07-16
install dontzap

```
sudo apt-get install dontzap
```

Then run 

```
sudo dontzap --disable
```

Where &#8220;disable&#8221; means that Ctrl+Alt+Backspace restarts the xserver while &#8220;enable&#8221; means that it won&#8217;t.


To reneable - use --enable

From tseliots blog page.

---

### Post by binbash on 2009-07-16
[http://www.ubuntu-inside.me/2009/05/howto-enable-ctrlaltbackspace-on-ubuntu.html](http://www.ubuntu-inside.me/2009/05/howto-enable-ctrlaltbackspace-on-ubuntu.html)

---

### Post by ubudog on 2009-07-16
Thanks

---

### Post by ubudog on 2009-07-16
> **forestpixie said:**
> install dontzap

```
sudo apt-get install dontzap
```

Then run 

```
sudo dontzap --disable
```

Where “disable” means that Ctrl+Alt+Backspace restarts the xserver while “enable” means that it won’t.


To reneable - use --enable

From tseliots blog page.

Thanks that worked.

---

### Post by Elfy on 2009-07-16
I know - I recently reinstalled and forgot to do it - you reminded me :D

---

