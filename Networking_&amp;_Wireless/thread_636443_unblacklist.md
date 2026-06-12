---
title: "unblacklist"
date: 2007-12-09
forum: Networking &amp; Wireless
---

### Post by mikev77 on 2007-12-09
How do i unblacklist something?

---

### Post by jflaker on 2007-12-09
please provide more information on what you are trying to unblacklist.

Thanks

---

### Post by mikev77 on 2007-12-09
A driver that i put in a ndiswrapper file. I'm something of a newbie, so I help that gives enough info.

---

### Post by mikev77 on 2007-12-09
I did something like: echo 'blacklist rt2500usb' | sudo tee -a ndiswrapper (something something)

---

### Post by Lostincyberspace on 2007-12-09
Did you try whitelisting it?

---

### Post by mikev77 on 2007-12-09
are you serious?

---

### Post by Aathos on 2007-12-09
That is going to depend on what kind of something you want to unblacklist.  If you mean how do you remove a kernel module from the blacklist: you comment the relevant line in etc/modprobe.d/blacklist.  That is, add a # to the beginning of the line.

---

### Post by mikev77 on 2007-12-09
This leads me to another question. When I try to open the file and save changes, I'm told that it was created by "root" and that I don't have permission to change anything. This goes for pretty much the entire system. Is that normal?

---

### Post by Lostincyberspace on 2007-12-09
Depeneds on what it is, if it is a system program or file crucial to the system running then yes, other wise no. If you are trying to fix some thing in a file then it would mostlikely need to be done as root.

---

