---
title: "How to run a file on system boot-up?"
date: 2011-07-02
forum: New to Ubuntu
---

### Post by HeavyDust on 2011-07-02
I would like to know if it's possible to automatically start up an .xls file? I know it's possible to run a program or a script on boot-up, but can you do the same with a file?

Thanks in advance!

---

### Post by abybaddi on 2011-07-02
What software do you use to open .xls files?

If you have open office.
Go to start-up preferences and add a new item.
Name it anything.
in command add this:
```

openoffice -calc -o "file path without the quotes"

```
Click ok...:)

Source: [Man Page for Open office.]("http://manpages.ubuntu.com/manpages/hardy/man1/openoffice.1.html")

---

### Post by HeavyDust on 2011-07-02
Yes, that did the trick! Thanks a lot!

---

