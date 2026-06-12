---
title: "how can i find out what &quot;group&quot; a program is in?"
date: 2009-11-03
forum: New to Ubuntu
---

### Post by hanzj on 2009-11-03
Hello,

How can I figure out what "group" a program is in?

For example, the program wicd is related to the group "netdev".

Thank you.

---

### Post by LarsW_Tierp on 2009-11-03
If you know in what folder the file is in it is easy:

type: la -al and the file name.

If you don't know where it is you have to find it like:
Example who owns firefox:

lars@lars-desktop:/$ sudo find -name "firefox"
./usr/share/firefox
./usr/share/doc/firefox
./usr/bin/firefox
./usr/lib/firefox-3.5.4/firefox
./usr/lib/firefox
./home/lars/.mozilla/firefox
lars@lars-desktop:/$ ls -al /usr/bin/firefox
lrwxrwxrwx 1 root ***root*** 11 2009-10-31 09:35 /usr/bin/firefox -> firefox-3.5
lars@lars-desktop:/$ 

The highlighted root are the group.

---

### Post by LarsW_Tierp on 2009-11-04
Maybe a bad example, firefox is only a link to something else, but the procedure is the same, so it should have no difference for you problem.

---

### Post by Hazey on 2009-11-04
Hi,

whith lars' method, you only can scan one program. For scanning many programs print the $PATH Variable

echo $PATH

You will find folders where programs are stored. Go to these folders and execute

ls -la | grep fire*

"grep fire*" means that all programs will be listed that start with fire.

Hazey

---

