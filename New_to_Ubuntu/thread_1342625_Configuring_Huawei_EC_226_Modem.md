---
title: "Configuring Huawei EC 226 Modem"
date: 2009-12-01
forum: New to Ubuntu
---

### Post by toxicblogger on 2009-12-01
Can anyone help me with a step by step instruction?


Thank you in advance.

---

### Post by cairnzi on 2009-12-01
Try this post?

_[http://ubuntuforums.org/showthread.php?t=1090119](http://ubuntuforums.org/showthread.php?t=1090119)_

---

### Post by toxicblogger on 2009-12-01
hi and thanks for the response. Yeah i had done before i made this thread and i believe i fell into a spot of bother. Let me quote the error message:


> E325: ATTENTION
Found a swap file by the name "/etc/.wvdial.conf.swp"
          owned by: root   dated: Tue Dec  1 08:02:51 2009
         file name: /etc/wvdial.conf
          modified: YES
         user name: root   host name: mohamed-laptop
        process ID: 4449
While opening file "/etc/wvdial.conf"
             dated: Tue Dec  1 08:07:06 2009
      NEWER than swap file!

(1) Another program may be editing the same file.
    If this is the case, be careful not to end up with two
    different instances of the same file when making changes.
    Quit, or continue with caution.

(2) An edit session for this file crashed.
    If this is the case, use ":recover" or "vim -r /etc/wvdial.conf"
    to recover the changes (see ":help recovery").
    If you did this already, delete the swap file "/etc/.wvdial.conf.swp"
    to avoid this message.
"/etc/wvdial.conf" 22 lines, 448 characters
E325: ATTENTION
Found a swap file by the name "/etc/.wvdial.conf.swp"
          owned by: root   dated: Tue Dec  1 08:02:51 2009
         file name: /etc/wvdial.conf
          modified: YES
         user name: root   host name: mohamed-laptop
        process ID: 4449
While opening file "/etc/wvdial.conf"
             dated: Tue Dec  1 08:07:06 2009
      NEWER than swap file!

(1) Another program may be editing the same file.
    If this is the case, be careful not to end up with two
    different instances of the same file when making changes.
    Quit, or continue with caution.

(2) An edit session for this file crashed.
    If this is the case, use ":recover" or "vim -r /etc/wvdial.conf"
    to recover the changes (see ":help recovery").
    If you did this already, delete the swap file "/etc/.wvdial.conf.swp"
    to avoid this message.
"/etc/wvdial.conf" 22 lines, 448 characters



Now what should i do? Greatly appreciate the assistance.

---

### Post by toxicblogger on 2009-12-02
Thanks Cairn, A friend of mine used that link to help me solve the issue.


Cheers.

---

