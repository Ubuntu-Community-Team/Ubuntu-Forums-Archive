---
title: "Launching Processes on Host of SSH"
date: 2011-01-17
forum: New to Ubuntu
---

### Post by Lazy-buntu on 2011-01-17
I've got a computer w/ SSH server running, which I can connect to. I want to launch VirtualBox on it via SSH without seeing it on the SSH client.

In other words, I don't want to do ssh -X and see VirtualBox on the client computer. I want to run VirtualBox on the server, and connect to it through different means (which I have no problem with).

Basically, how can I launch a program on the server from the client?

---

### Post by ggarron on 2011-01-17
I do not know if I fully understand you.

But if you want to start a virtual machine, installed on that remote server, that you have ssh access.

Run something like this:

    VBoxManage startvm "name of virtual machine"

Hope it helps.

---

