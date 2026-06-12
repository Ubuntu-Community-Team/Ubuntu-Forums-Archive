---
title: "Network printer asks for password each time I want to print"
date: 2010-05-18
forum: New to Ubuntu
---

### Post by Dangger on 2010-05-18
How can I avoid this? It's very annoying to have to type in my username and password every time I want to print something.

This is a shared printer through samba.

---

### Post by ScottinSoCal on 2010-05-18
> **Dangger said:**
> How can I avoid this? It's very annoying to have to type in my username and password every time I want to print something.

This is a shared printer through samba.

Is it a true networked printer (the network cable is plugged right into the printer?) or is it shared via a Windows box?

If it's a true networked printer, delete it, and set it up as just a networked printer. That's how I have my laser printer set up, and it works flawlessly. If it's shared through a Windows box, set up your .smbcredentials file and have your user ID and password in there. I do that at work, and it never asks me for my user ID and password.

---

### Post by Dangger on 2010-05-18
> **ScottinSoCal said:**
> Is it a true networked printer (the network cable is plugged right into the printer?) or is it shared via a Windows box?

If it's a true networked printer, delete it, and set it up as just a networked printer. That's how I have my laser printer set up, and it works flawlessly. If it's shared through a Windows box, set up your .smbcredentials file and have your user ID and password in there. I do that at work, and it never asks me for my user ID and password.


Hi ! :D it's a shared through a Windows box. Excuse my ignorance but how do I set up the .smbcredentials file? Never mind, I found a good article [here]("https://help.ubuntu.com/community/MountWindowsSharesPermanently").

---

