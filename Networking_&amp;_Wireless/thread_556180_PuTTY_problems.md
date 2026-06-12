---
title: "PuTTY problems"
date: 2007-09-21
forum: Networking &amp; Wireless
---

### Post by starfleetcaptainrob on 2007-09-21
I'm having some problems with trying to get files off an Ubuntu box remotely via putty onto my windows laptop.  I'm able to log into putty fine but when I try to get the file I need I string this sort of command:

```
pscp user@ubuntubox:/home/user/file.txt G:\
```

and it asks for the password no problem and it does go through it's little transfer thing telling me the transfer rate, percentage left, how many kb it's transfered, etc.  However when I go to G:\ the file is not there.  It's as if it never happened.  Has anyone else had this problem?  I'm using freeSSHd on my windows laptop as the windows SSH server if that helps any.

---

### Post by kevdog on 2007-09-21
Only used WinSCP for this purpose.  So Im not sure

---

### Post by noob12 on 2007-09-21
Perhaps the ":" in the path is confusing it.  Try

```

cd /d g:\
pscp user@ubuntubox:/home/user/file.txt file.txt

```

---

### Post by starfleetcaptainrob on 2007-09-23
I still don't get anything that way...it's weird.  I looks like it's transferring, but the file is nowhere to be found...

---

