---
title: "SSH and Remote Desktop"
date: 2008-05-16
forum: Networking &amp; Wireless
---

### Post by snoguy986 on 2008-05-16
I am going to be installing Ubuntu 8.04 on a friend's computer and I want to be able to remote into it like I can with Windows.

I have used SSH and the like, but I want to have control of their desktop like you can with RDC in WinXP and UltraVNC.  SSH I've only heard of being able to remote into a machine and having command line access.

I have read several threads on this, however none of them address what a feature I need most.  Remote access no matter where I am or they are.

Is there anyone who knows how to do this or can point me in the right direction?  Thanks.

---

### Post by eldragon on 2008-05-16
> **snoguy986 said:**
> I am going to be installing Ubuntu 8.04 on a friend's computer and I want to be able to remote into it like I can with Windows.

I have used SSH and the like, but I want to have control of their desktop like you can with RDC in WinXP and UltraVNC.  SSH I've only heard of being able to remote into a machine and having command line access.

I have read several threads on this, however none of them address what a feature I need most.  Remote access no matter where I am or they are.

Is there anyone who knows how to do this or can point me in the right direction?  Thanks.

there is the vino vnc server there. i found it didnt work that well with my setup, so i used x11vnc which needs to be installed from the repos, and added to the autostart menues for gtk.

install openssh-server on your friends computer, from there if you are comfortable with the terminal, you will find you dont need anything else. you could setup x11vnc from there and even tunnel the connection through ssh. this would make your friends computer more secure, since you are only poking 1 hole in his router / firewall (the ssh port).


hope im clear enough.

---

