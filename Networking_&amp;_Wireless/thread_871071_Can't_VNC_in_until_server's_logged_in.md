---
title: "Can't VNC in until server's logged in"
date: 2008-07-26
forum: Networking &amp; Wireless
---

### Post by mattalexx on 2008-07-26
I have Ubuntu's native VNC working on my new Ubuntu server. I use Windows XP to log in using TightVNC. It's working great. 

The thing is, I can't use VNC until a user is logged into Gnome on that computer, so running a "shutdown -r now" at any point will restart the server and disable my VNC access until I plug a keyboard into it and log into Gnome.

My workaround at the moment is to automatically log my user in, but I don't like that very much at all.

Any ideas?

---

### Post by sg7791 on 2008-07-26
I use ssh to log into Ubuntu before I can start VNC.

Install OpenSSH with:
```
sudo apt-get install openssh-server
```

Then you should be able to log in remotely from [PuTTY]("http://www.chiark.greenend.org.uk/~sgtatham/putty/") on Windows.
```
ssh admin@192.168.x.x
```

---

### Post by mattalexx on 2008-08-13
Thank you for your response.

---

