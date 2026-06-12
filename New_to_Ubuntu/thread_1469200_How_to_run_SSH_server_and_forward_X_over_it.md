---
title: "How to run SSH server and forward X over it?"
date: 2010-05-02
forum: New to Ubuntu
---

### Post by ajk95 on 2010-05-02
OK, here's what I want to do: I have a Windows 7 laptop and an Ubuntu 10.04 desktop, and I've heard of SSH servers and forwarding X over them, but I don't know how to make it happen. I want to forward it from the Ubuntu box to the Windows laptop. How do I do this?

---

### Post by Seti on 2010-05-02
first you have to edit /etc/ssh/sshd_conf and make sure you have 

X11Forwarding yes

Now remember on your client you're going to have to have an xserver running (Cygwin?) I've never actually done this because I've never had to -  but that's the basics of how you would do it.
On the server side, don't forget to ```
sudo /etc/init.d/ssh restart
```

---

