---
title: "Compiling kernel... Permission problems."
date: 2011-02-03
forum: New to Ubuntu
---

### Post by newn on 2011-02-03
Hi everybody. I'm having trouble compiling ZEN kernel. I've taken right versions, etc., but I'm getting some strange error:

sudo lzcat ../2.6.36-zen2.patch.lzma | patch -p1 
 I'm getting this message: 
 patching file Documentation/ABI/testing/debugfs-aufs 
 patch: **** Can't rename file /tmp/pouQiBVW to Documentation/ABI/ 
 testing/debugfs-aufs : Permission denied 

Asked in ZEN forums, and somebody said, that it's not exactly their problem, this is some kind of permission problem.
How can I make it work? Using x64 9 Ubuntu.

Thanks.

---

### Post by JKyleOKC on 2011-02-03
> **newn said:**
> Hi everybody. I'm having trouble compiling ZEN kernel. I've taken right versions, etc., but I'm getting some strange error:

sudo lzcat ../2.6.36-zen2.patch.lzma | patch -p1 
 I'm getting this message: 
 patching file Documentation/ABI/testing/debugfs-aufs 
 patch: **** Can't rename file /tmp/pouQiBVW to Documentation/ABI/ 
 testing/debugfs-aufs : Permission denied 

Asked in ZEN forums, and somebody said, that it's not exactly their problem, this is some kind of permission problem.
How can I make it work? Using x64 9 Ubuntu.

Thanks.The permission granted by "sudo" does NOT persist through the pipe symbol. There's a workaround using the "tee" command but I don't think it will work in this situation. You really need to open a root shell to do this sort of thing; that can be done via "sudo -i" which will give you the permission needed but will also make it **easy** to accidentally destroy your system. The prompt's last character will change from $ to # to indicate the root shell; when you finish the compilation, type "exit" to end the root shell and return to your normal prompt.

---

### Post by newn on 2011-02-03
Thanks, it's working!

---

