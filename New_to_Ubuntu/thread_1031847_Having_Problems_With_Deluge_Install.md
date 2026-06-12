---
title: "Having Problems With Deluge Install"
date: 2009-01-05
forum: New to Ubuntu
---

### Post by Monrizzy on 2009-01-05
I'm having problems when I attempt to install anything.  I just had the same problem with installing Flash for Firefox yesterday and was able to resolve by opening a terminal and using the following command.

```
sudo dpkg --configure -a
```

The command is not working now I'm getting this message.

> **Only one software management tool is allowed to run at the same time**

Please close the other application e.g. 'Update Manager','aptitude' or 'Synaptic' first. 

If anybody has any idea what I'm doing wrong please help.  I'm a complete noob and having a hard time wrapping my brain around Linux.....

---

### Post by mick316 on 2009-01-05
Firstly, do what it says and close Synaptic or update window.

Maybe best if you logged out and back in again.

Then in terminal type "sudo apt-get install deluge" without the quotes (or search for it in Synaptic).
Cheers.

---

