---
title: "I can only use sudo firefox"
date: 2010-03-27
forum: New to Ubuntu
---

### Post by scorpious on 2010-03-27
Since re-installing kubuntu (wanted to change my partition settings), Firefox only will open with Sudo. I've tried re-installing a few times but to no avail. I've also tried installing different versions.

Does anyone know how I could get firefox running without going through root?

cheers

---

### Post by aysiu on 2010-03-27
**Step 1**
Close all Firefox windows

**Step 2**
Paste this command into [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
sudo chown -R *username:username* /home/*username*/.mozilla
``` where *username* is your actual username

**Step 3**
Start Firefox normally

**Step 4**
Read the following so you never have this problem again:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by scorpious on 2010-03-27
I love ubuntuforums!

Thanks Aysiu

---

