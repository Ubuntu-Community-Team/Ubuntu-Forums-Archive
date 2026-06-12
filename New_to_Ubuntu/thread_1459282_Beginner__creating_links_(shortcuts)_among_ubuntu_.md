---
title: "Beginner : creating links (shortcuts) among ubuntu &amp; windows XP"
date: 2010-04-21
forum: New to Ubuntu
---

### Post by goodsun on 2010-04-21
Hello Everyone
I am a cyber cafe owner with some computers having windows XP & some having ubuntu & having problem with ubuntu
I can able to make shortcut from windows to linux (file/folder) but when i make a shortcut from linux to windows XP , its says "error while making link to ---, the target doesn't support symbolic link"
plz help me with this error

FOR TO BE MORE CLEAR
-------------------------------------
I am expert in windows XP but beginner in ubuntu
I am getting this error while i am in linux & creating a shortcut of windows file/folder

thanks
plz reply me soon

---

### Post by jpaugh64 on 2010-04-21
There are two problems with doing this, both of which are lamentable.

* Windows uses filesystems that do not support symlinks. Windows shortcuts are very different from linux symlinks in design, but serve a similar purpose.

* Windows cannot access the default Linux filesystem (ext).

There is a partial way around both of these. Basically, keep all of the files that you want to share on a filesystem Windows is agreeable to (such as vFAT), and make your Windows shortcut using Windows. (Of course, you would also want a symlink to that in a convenient place in the Linux system.)

It may instead suffice to make a symlink to the Windows default user's home directory?

---

