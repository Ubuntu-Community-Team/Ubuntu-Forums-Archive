---
title: "I really need help"
date: 2009-12-17
forum: New to Ubuntu
---

### Post by Sethdd on 2009-12-17
whenever i try to do anything that requires a password this message pops up.
"The underlying authorization mechanism (sudo) does not allow you to run this program. Please contact the system administrator."

---

### Post by jamieleshaw on 2009-12-17
Try this 'adduser your_username admin' in the terminal.

---

### Post by Sethdd on 2009-12-17
It says 
"Only root may add a user or group to the system."

---

### Post by jamieleshaw on 2009-12-17
Type 'su root' then type 'adduser your_username admin'

---

### Post by Sethdd on 2009-12-17
okay, now it says
"seth is not in the sudoers file.  This incident will be reported."
?

---

### Post by jamieleshaw on 2009-12-17
crap sorry again ummm, I'll let someone else help you wth this one.

---

### Post by HereInOz on 2009-12-17
Try this:

[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

Hope this helps.

Without sudo priviledges, you may need to boot using a Live CD, then mount the hard disk and make any changes that way.  It could be a fun time.

---

### Post by prshah on 2009-12-18
Boot into "Recovery Mode" (Select from the GRUB menu). If you get another menu, choose "Root terminal" (Or equivalent therof) to land up at a command prompt. Then give the adduser command as suggested earlier. No need to add "sudo". Then give the command ```
reboot
``` boot normally, and you should have sudo access.

---

### Post by jamieleshaw on 2009-12-18
> **prshah said:**
> Boot into "Recovery Mode" (Select from the GRUB menu). If you get another menu, choose "Root terminal" (Or equivalent therof) to land up at a command prompt. Then give the adduser command as suggested earlier. No need to add "sudo". Then give the command ```
reboot
``` boot normally, and you should have sudo access.
Why didn't I think of that?
:)

---

