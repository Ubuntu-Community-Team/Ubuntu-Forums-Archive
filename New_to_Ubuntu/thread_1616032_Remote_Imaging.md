---
title: "Remote Imaging"
date: 2010-11-07
forum: New to Ubuntu
---

### Post by GaretJax on 2010-11-07
I am supporting a large Windows only client remotely.  I would like ideas on the best ways I can create and restore disk images of their workstations remotely.  Currently they are using Acronis 9, but I cannot connect to it remotely and I have to ask the users to locate the bootable CD and walk them through each screen.  This is difficult.

What I am planning on doing is sending them a USB drive with a persistent image of Ubuntu 10.10 on it. It will have the Remote Desktop enabled so that I can connect to it with VNC. I am hoping I can use this remotely to repair downed Windows machines. 

I thought about sending them a USB drive with Clonezilla. I learned how to enable SSH and logged into it remotely, but I only get the Clonezilla CLI.  Without the GUI I am lost.  I wish I could run Clonezilla in Ubuntu because I think that would solve my issue here and I wouldn't be writing this post if I could.

So with the current scenario presented (a persistent Ubuntu on USB with remote desktop enabled), what are some of the best ideas for backing up and restoring workstation images to a NAS?

---

### Post by TSJason on 2010-11-08
Garet,

Check out the fog project: [http://fogproject.org/](http://fogproject.org/)

You can use this to setup an automated remote cloning utility. All workstations will need to have the fog client installed and running in order to remotely kickoff the imaging. It works with PXE so no boot discs are needed.

---

### Post by GaretJax on 2010-11-30
Thanks for the tip.  I will check it out.  Do you know the product well enough if I have further questions?

> **TSJason said:**
> Garet,

Check out the fog project: [http://fogproject.org/](http://fogproject.org/)

You can use this to setup an automated remote cloning utility. All workstations will need to have the fog client installed and running in order to remotely kickoff the imaging. It works with PXE so no boot discs are needed.

---

