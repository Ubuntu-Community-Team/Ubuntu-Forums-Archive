---
title: "Samba shares shown but cant authenticate"
date: 2007-03-20
forum: Networking &amp; Wireless
---

### Post by Ephilei on 2007-03-20
I have a single Samba shared directory on Ubuntu. An OSX and XP machine both see the machine but can't complete authentication (yes, I'm positive I'm not entering the login incorrectly). OSX can even give me a list of the shares on Ubuntu. 

Secondly, is it possible for network users to connect anonymously without being prompted at all?

---

### Post by scxtt on 2007-03-20
on ubuntu:

sudo smbpasswd -a $USERNAME

enter a password, and use that w/ the value you used for $USERNAME to connect to the share ... and yes, anonymous shares are possible ...

---

### Post by Ephilei on 2007-03-20
Thanks! Perfect. How did you know that?

---

### Post by scxtt on 2007-03-20
let's just say i've been in that boat myself ;) ... i think i've solved that problem for at least a dozen people :)

---

