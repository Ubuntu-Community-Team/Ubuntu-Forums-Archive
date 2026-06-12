---
title: "Sharing files networked Ubuntu desktop to Ubuntu laptop"
date: 2007-05-28
forum: Networking &amp; Wireless
---

### Post by helliewm on 2007-05-28
I have a networked system with a 2 single boots of Ubuntu on my Laptop and Desktop, The Laptop is Wireless and the Desktop is Wired. I want to able to share files OOo documents etc between the Laptop and Desktop. It would also be good if I could print from my Wireless Laptop.

Security is not an issue its only me that uses the Laptop and Desktop.

What is the best option? I am confused is Samba an option, for example???   

Helen

---

### Post by scrooge_74 on 2007-05-28
For printing use CUPS, which comes already installed.  Just tell the system with the printer to share it, in a little while the other PC will see it.

For sharing files you can use nfs, check the ubuntu guide for further info.  Once you have nfs-server going you can easily set up which directories to share and setup security.

Forget about SAMBA that is for networking with XPs systems

---

