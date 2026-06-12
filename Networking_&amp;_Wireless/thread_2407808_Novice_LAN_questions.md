---
title: "Novice LAN questions"
date: 2018-12-09
forum: Networking &amp; Wireless
---

### Post by ra7411 on 2018-12-09
I've got 2 desktop machines that I sometimes transfer files between. They are less than a foot apart and use the same DSL modem (a c1000a VDSL2 modem router).

1) is it possible to use this modem/router get these 2 machines connected? Could Reminna be used for this?

2) if 1) won't work, could directly connecting them w/ an ethernet cable work? Could Reminna be used for this?

If 1) and 2) are no goes, what will work, preferably something with a GUI interface?

Thanks

---

### Post by Dennis N on 2018-12-10
To connect Linux machines on my LAN (it has no Windows machines) I installed **openssh-server** and **gigolo** on them. gigolo is a GUI application that manages the connection and is easy to use.

---

### Post by CatKiller on 2018-12-10
> **ra7411 said:**
> I've got 2 desktop machines that I sometimes transfer files between. They are less than a foot apart and use the same DSL modem (a c1000a VDSL2 modem router).

If they're both plugged into the same router, they're already connected.
(They're on the same network)

The most sensible way to do things from one computer to another is SSH, which stands for Secure SHell. The implementation of SSH that Ubuntu uses is OpenSSH.

The SSH client is installed by default, meaning that you can use SSH to connect to another computer right away. However, the SSH server *isn't* installed by default, so that your computer isn't accessible from the outside unless you choose it to be.

As Dennis N says, you'll want to install the **openssh-server** package on at least one of the computers. Once a computer has the server package installed, you can use the other to connect to it, run commands and transfer files.

SSH integrates with the file manager, so you don't *need* to install anything else after that. You can use Places &#8594; Connect to Server, or use an address like **fish://user@ip.adress** in the location bar to move files around. There are plenty of applications that can use that connection if you want.

---

