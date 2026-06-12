---
title: "Bash error in terminal"
date: 2011-04-12
forum: New to Ubuntu
---

### Post by idle1 on 2011-04-12
I've started getting the following error on opening the terminal...

bash: /etc/bash_completion.d/lvm: line 275: unexpected EOF while looking for matching `''
bash: /etc/bash_completion.d/lvm: line 277: syntax error: unexpected end of file

I haven't been able to open lvm to try to remedy the error.

This doesn't seem to be causing any real problems - but I feel I should get it fixed...

---

### Post by spikoley on 2011-04-12
This [thread]("http://ubuntuforums.org/showthread.php?p=10267675") has a solution to a similar issue.  It looks like you need a clean copy of /etc/bash_completion.d/lvm to fix it.

---

### Post by idle1 on 2011-04-12
Excellent - that worked a treat!

many thanks for the link

---

