---
title: "Remote Desktop/Folder Access...via the Web???"
date: 2008-05-07
forum: Networking &amp; Wireless
---

### Post by petrafan007 on 2008-05-07
Anyone ever hear of SoonR or Avvenu? Both let you install a program that runs in the background/system tray that allows you to link folders to it so I can sign in from their website and access those folders. Those were neat programs for Windows, but I can find nothing that will let me do that for Ubuntu. Does anyone know of a program or a workaround that I can get something similar set up in Ubuntu? Web access is a must.

Thanks!!! :)

:popcorn:

---

### Post by tamoneya on 2008-05-07
just install an ssh server on the computer you want to access and then install putty or another ssh client on the computer you want to access them from.

---

### Post by petrafan007 on 2008-05-07
I am aware of this option but what I need is a way to access a file or folder over the web. Example: at work, where I can't install anything on the machine.

---

### Post by tamoneya on 2008-05-07
ssh allows you to do this.  Its called scp and it is installed along with ssh.  If by "over the web" you mean through firefox that is different.  I personally prefer using an ssh client so I am not familar with broswer based remote clients.

---

### Post by superprash2003 on 2008-05-07
how about ftp? .. and for remote desktop access you can use the remote desktop feature itself(System->preferences->remote desktop).. you might have to open port 3389 or 5900 ..

---

### Post by johnhunsley on 2008-06-05
This is exactly what you are looking for -

[https://www.browsershell.com](https://www.browsershell.com)

Uses SSL to SSH and they don't store anything about your server so so perfectly secure.

Enjoy.

John.

---

