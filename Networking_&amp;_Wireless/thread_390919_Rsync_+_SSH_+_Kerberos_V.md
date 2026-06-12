---
title: "Rsync + SSH + Kerberos V"
date: 2007-03-22
forum: Networking &amp; Wireless
---

### Post by mahlib on 2007-03-22
Hello again everyone.

I've searched the web for a HOWTO or a Wiki on creating the following setup:

Terms used:
**Windows Domain Controller**: Runs Windows Server 2003, Microsoft's implementation of a Kerberos Domain Controller, and in the Windows context (on Windows clients) is used for authentication
**Linux Server**: A Linux server that houses, on a per-user basis, configuration files located in a user's home directory (i.e. .vimrc)
**Linux Client(s)**: A Linux client that authenticates via Winbind to the Windows Domain Controller.

From the Linux clients, I want to be able to run rsync -avze ssh $USER@$SERVER:$PROFILE_DIR $HOME without requiring that users enter their passwords in. Since the Windows Domain Controller already runs a Kerberos Domain Controller (KDC), I can simply authenticate with the Windows Domain Controller and present the forwardable ticket granted by the Windows Domain Controller to the Linux Server.

What I have access over:
No administrative access over the Windows Domain Controller, only user access (that too only student access)
Full access over the Linux server
Full access over the Linux clients

All constructive advice is appreciated.

Regards.

---

