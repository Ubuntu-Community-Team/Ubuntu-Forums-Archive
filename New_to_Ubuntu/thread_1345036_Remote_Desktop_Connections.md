---
title: "Remote Desktop Connections?"
date: 2009-12-03
forum: New to Ubuntu
---

### Post by six30two on 2009-12-03
I could use some help here. I'm trying to get a remote desktop running so I can view my server with a GUI from my laptop outside of the network my server is on.

I'm running Ubuntu Desktop 9.10 on my laptop.
I'm running Ubuntu Server 9.10 with Xubuntu GUI running on my server.

I can only SSH in to command line.

Can anyone tell me how to install and start a remote desktop utility so I can access my server's GUI? I need step-by-step instructions - not just something like "Have you tried X-forwarding?" because I likely won't know what that is or where to start to get it running.

Please help =(

---

### Post by cariboo on 2009-12-03
I would suggest using vnc over an ssh tunnel. Improperly setup vnc is one of the major causes of cracked systems.

Have a look [here]("http:///ubuntu-tutorials.com/2007/06/12/vnc-over-ssh-securing-the-remote-desktop/") for a howto.

---

