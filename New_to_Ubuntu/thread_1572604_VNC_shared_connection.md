---
title: "VNC shared connection"
date: 2010-09-11
forum: New to Ubuntu
---

### Post by jubby on 2010-09-11
On windows, I can connect to a remote windows machine and then ask a friend to connect as well and we can see each others actions.
When connecting from windows to the Ubuntu box we see a separate instance of the desktop.
Is there a way to connect and see the actual desktop AND each others actions?

thanks

---

### Post by cavh on 2010-09-11
I have no idea about how to do this on VNC, but I have read good reviews about [http://www.teamviewer.com]("http://www.teamviewer.com") on Ubuntu, and this may be worth a look?

---

### Post by anglican on 2010-09-13
> **jubby said:**
> On windows, I can connect to a remote windows machine and then ask a friend to connect as well and we can see each others actions.
When connecting from windows to the Ubuntu box we see a separate instance of the desktop.
Is there a way to connect and see the actual desktop AND each others actions?

thanks
The "x11vnc" program can be used to show your actual desktop on a remote computer. Using the "-shared" option enables this to be on more than one computer. A simple procedure is:

(1) On the first Windows computer connect to Ubuntu using the Putty ssh client. Set up an SSH tunnel to forward port 5900 to localhost:5900 (you should always tunnel vnc).

(2) Once connected to Ubuntu machine run:
```
x11vnc -ncache 10 -display :0 -usepw -shared -q
```
(this assumes you have a vncpassword on the Ubuntu machine set with the command "vncpasswd").

(3) On the first Windows computer open the vncviewer and connect to "localhost:0". This should show the actual desktop on the ubuntu machine.

(4) Repeat steps (1) and (3) (do not run the x11vnc command again) on the second Windows computer. This should also now show the Ubuntu desktop on the second Windows machine.

You can get "Putty" for Windows from:

[http://www.chiark.greenend.org.uk/~sgtatham/putty/](http://www.chiark.greenend.org.uk/~sgtatham/putty/)

H

---

