---
title: "I installed Ubuntu 10.10 on my brother's computer and I need to know a few things."
date: 2011-01-08
forum: New to Ubuntu
---

### Post by maxin11p on 2011-01-08
What do you need to do to get a desktop?? I know you need to use GNOME or something, but I have no idea how it works.

And I've tried commands to get a desktop, and I did the sudo thing, and when I do it it asks me for my password, and when I put it in it says that I'm not in the sudoers folder, and the incident has been reported. Is this some sort of error, or am I just not getting it?

Please help...

---

### Post by mikewhatever on 2011-01-08
Normally, all you need to do to get to the desktop is press the power button and wait. Can you post the hardware specs of that computer.

---

### Post by maxin11p on 2011-01-08
I don't really know them. Sorry...
All I know is that it's an Acer desktop that had Windows Vista Home on it...

Can you give me information on how to use sudo, and how it works, though? I've read a lot of things that tell me that if I can use commands to install a desktop, and they all involve sudo commands. And as I said above, when I use sudo it asks me for my sudo password. And when I put it in, it say's I'm not in the sudoers folder and it reported the incident.

---

### Post by Tiler on 2011-01-08
> **maxin11p said:**
> I don't really know them. Sorry...
All I know is that it's an Acer desktop that had Windows Vista Home on it...

Can you give me information on how to use sudo, and how it works, though? I've read a lot of things that tell me that if I can use commands to install a desktop, and they all involve sudo commands. And as I said above, when I use sudo it asks me for my sudo password. And when I put it in, it say's I'm not in the sudoers folder and it reported the incident.

Describe a little bit about how you installed it and how you know it was 10.10.

---

### Post by holiday on 2011-01-08
It sounds like you do not have the Desktop edition. In the Desktop edition, Gnome is automatically installed.

Try downloading the iso again, this time making sure you get the Desktop edition. 

And make a note of the username and password you enter during the install. Your username and password are automatically entered to the sudoers file.

---

### Post by maxin11p on 2011-01-08
> **holiday said:**
> It sounds like you do not have the Desktop edition. In the Desktop edition, Gnome is automatically installed.

Try downloading the iso again, this time making sure you get the Desktop edition. 

And make a note of the username and password you enter during the install. Your username and password are automatically entered to the sudoers file.
Oh, okay. Thank you. I'll try downloading the Desktop edition.

And I used the same username and password I put in when it asked me when I was installing it. It just wouldn't work...error?

---

### Post by mikewhatever on 2011-01-08
> **maxin11p said:**
> ...

Can you give me information on how to use sudo, and how it works, though? I've read a lot of things that tell me that if I can use commands to install a desktop, and they all involve sudo commands. And as I said above, when I use sudo it asks me for my sudo password. And when I put it in, it say's I'm not in the sudoers folder and it reported the incident.

If you aren't in the sudoers file, you can't use sudo. You shouldn't need to install the desktop separately, as Ubuntu images include it by default.

---

