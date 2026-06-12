---
title: "ubuntu 10.4 server recovery mode fails"
date: 2011-08-09
forum: New to Ubuntu
---

### Post by nimy on 2011-08-09
I was editing .ssh authorized hosts and /etc/sudoers on my server and forgot to chmod the sudoers file before exiting. Now I can't su to root (root password was never set) to fix the problem, and I'm locked out of sudoers. I tried booting in recovery mode (FYI Ubuntu 10.04.3 LTS, kernel 2.6.32-23-generic-pae recovery mode). However selecting the root prompt options (with or without networking) takes me to this prompt: 
"Give root password for maintenance or type Control-D to continue"
There's no root password and Control-D sends me back to the menu. I can't find the installation disk so I'm stuck.

---

### Post by nimy on 2011-08-10
Found the answer at [https://help.ubuntu.com/community/LostPassword](https://help.ubuntu.com/community/LostPassword), thanks

---

