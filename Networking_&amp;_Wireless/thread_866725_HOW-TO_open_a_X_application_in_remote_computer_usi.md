---
title: "HOW-TO open a X application in remote computer using ssh"
date: 2008-07-22
forum: Networking &amp; Wireless
---

### Post by lazertek on 2008-07-22
How can you open an applications such as rythmbox for example in the remote computer. When you login using ssh -l it will only open it in the terminal...

using ssh -X rythmbox will open in the computer you are trying to access to the remote from. but how to you make it open in the remote computer?

---

### Post by McNils on 2008-07-22
Whell you can log in with **ssh -X -l** and then start the application from the command line.

---

### Post by kunixos on 2008-07-22
If the remote server is Windows there's an X emulator that will allow you to open X apps in windows. Just check the "Open X Apps" if you're using Putty (only one I've any experience with) and then you should be able to launch like normal.

However, you have to make sure that in /etc/ssh/ssh_config the line ```
ForwardX11 yes
```says 'yes' instead of 'no' and is uncommented.

Hope this helps!

---

### Post by lazertek on 2008-07-25
The remote server is ubuntu and so is the client... What I want to do exactly is open type in the command for rhythmbox for example and rhythmbox opens in the remote server

---

### Post by juk_de on 2008-07-25
Allow TCP connections for GDM (by default turned off) and export DISPLAY=localhost:0.0
That's all.

---

