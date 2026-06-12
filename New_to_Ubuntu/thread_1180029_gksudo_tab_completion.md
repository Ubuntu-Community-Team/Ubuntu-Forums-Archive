---
title: "gksudo tab completion"
date: 2009-06-06
forum: New to Ubuntu
---

### Post by bacardiandwatermelon on 2009-06-06
Hey,
When using tab completion it works for sudo but not gksudo. For instance.
```
sudo nau <tab>
``` Brings up sudo nautilus, but
```
gksudo nau <tab>
``` Brings up nothing. I guess it is something to do with bashrc but not too sure. Thanks in advance..

---

### Post by Didius Falco on 2009-06-06
Hi,

open up Synaptic and see what version of **bash-completion** you have, and see if it's upgradeable. Check and see if you have any available updates.

I found a bug report on it that says that this was fixed in version 1:1.0-2.

It's working fine in the Karmic Alpha...

Here is a link to the bug report, which also contains a patch for it:

[https://bugs.launchpad.net/ubuntu/+source/bash-completion/+bug/239080](https://bugs.launchpad.net/ubuntu/+source/bash-completion/+bug/239080)

Regards,

Didius

PS Next time I'm in my Jaunty install, I'll try to remember to check it there and report back...

---

### Post by Volt9000 on 2009-06-06
Where is the patch? All I see is the output of a diff command.

---

### Post by bacardiandwatermelon on 2009-06-06
Thanks for putting me in the right direction. It worked perfectly. I saved the patch below as patch.diff
```
diff -u /etc/bash_completion /tmp/buffer-content-66310Oi
--- /etc/bash_completion    2008-04-08 10:29:11.000000000 -0400
+++ /tmp/buffer-content-66310Oi    2008-06-10 14:39:20.000000000 -0400
@@ -3259,7 +3259,7 @@
 {
  PATH=$PATH:/sbin:/usr/sbin:/usr/local/sbin _command $1 $2 $3
 }
-complete -F _root_command $filenames sudo fakeroot really
+complete -F _root_command $filenames sudo fakeroot really gksudo
  # ant(1) completion
 #

```and then patched it by running
```
sudo patch -p0 < patch.diff
```Logged out and logged back in. Thanks again :-)

---

### Post by sisco311 on 2009-06-06
as a quick fix add
```
complete -cf gksu
complete -cf gksudo

```to the .bashrc file

EDIT: too late :)

---

### Post by Didius Falco on 2009-06-06
> **bacardiandwatermelon said:**
> Thanks for putting me in the right direction. It worked perfectly. I saved the patch below as patch.diff
<snip>
Logged out and logged back in. Thanks again :-)

My pleasure!

I just hope Volt9000 sees it - I just got back to the PC and saw his post.

Regards,

Didius

---

### Post by Volt9000 on 2009-06-06
Yes I saw it, thanks Didius! :)

---

