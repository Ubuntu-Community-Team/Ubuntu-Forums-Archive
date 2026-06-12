---
title: "Trouble with sudoers in fedora"
date: 2010-08-14
forum: New to Ubuntu
---

### Post by bbuy2k on 2010-08-14
Hey guys,

I'm having a little trouble trying to add a user in the terminal with the sudoers command in fedora 13.  When I enter the command "sudo" it gives me the message "user is not in the sudoers file. This incident will be reported. How do I edit the sudoers file?"

please help

---

### Post by iMisspell on 2010-08-14
Never really used Fedora (only in a VM to see what it was like), but i would guess - you should log in as root and then add your current user to the "admin" group, then log out of root and back in as your current user and see if it works.

Just a guess.

_

---

### Post by bbuy2k on 2010-08-14
but i'm the only user, I've got one master passwd.  If i'm not root how do I login as root?

---

### Post by Dareth on 2010-08-14
```
su - root
```

---

### Post by -kg- on 2010-08-14
I wasn't able to pull this page up (timeout), but that might be my location and/or the path between me and the page.  Try this page:

[Sudoer HoW To]("http://www.wlug.org.nz/SudoHowto")

If that's down (the post containing it was relatively recent), then there were quite a few other references in Google.  My recommendation is the Fedora site, though I read it was a bit confusing.  The link above solved someone's problems nicely, so I assume it is a good guide.

---

### Post by bbuy2k on 2010-08-14
Thank you very much Dareth, your suggestion worked nicely thanks a bunch.

---

