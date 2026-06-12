---
title: "SSH Keys"
date: 2010-09-05
forum: New to Ubuntu
---

### Post by adamjkok on 2010-09-05
Okay, so previously, I thought I should use a password to sign on to my SSH server, but I'm starting to realize that an SSH key is a better idea.

I want to lock down my server and require an SSH key to get on. Here's where this gets complicated: the client (my laptop) runs Windows 7, and no, I'm not switching back to Ubuntu on this laptop.

---

### Post by Brandon Williams on 2010-09-06
Are you asking how to do this?

If so, it will depend on the ssh client that you run on Windows. I suggest that you use putty, because I know that it works well. You can create a key puttygen on windows and then convert the public half to openssh format for inclusion in your .ssh/authorized-keys file on the server. Alternatively, you can generate the key with ssh-keygen on the server and then convert it into a putty key for use on the client.

[Here](http://linux-sxs.org/networking/openssh.putty.html) is a simple tutorial that goes step-by-step through method 2.

---

