---
title: "Need partion help..."
date: 2011-03-12
forum: New to Ubuntu
---

### Post by cwjdog57 on 2011-03-12
Hello, Ubuntu community,

Recently, I gave up windows and moved to Ubuntu 10.10 x64. I used the WUBI installer for simplicity. Now, after formatting my primary hard drive, I'd like to change the directory that I installed to.

I realise that this is a stupid question, and I'll clarify a few things:

1.I've used Ubuntu before, so if this requires terminal, I don't care
2.I have 2 hard drives, I installed to the 2nd one, and I'd like to move my install to the primary
3.I want to keep a small 20 gb partition for windows (for gaming and such)

Thanks for your time and help,
Jason

---

### Post by vanadium on 2011-03-12
Make it easy to yourself, and reinstall, this time with a dedicated partition for Ubuntu. From within the Ubuntu installation program, you can shrink the Windows partition. The installation program will then partition the remaining space automatically. After installation, you will be able to choose whether to load Windows or Ubuntu.

Before installation, defrag your drive in Windows and do a file system check.

You can move your existing Wubi installation to a dedicated partition. This requires some experience with linux systems though.

---

### Post by bcbc on 2011-03-12
[HOWTO: migrate wubi install to partition]("http://ubuntuforums.org/showthread.php?t=1519354")

---

