---
title: "shell script and xboxdrv driver"
date: 2010-07-30
forum: New to Ubuntu
---

### Post by skript_teaze on 2010-07-30
After a long time installing xboxdrv I finally have it working. The driver runs in the userspace in a terminal window. I have created a shell script so that all I have to do is click the icon and the driver will load. Is there a way of getting the shell script to automatically start in terminal without asking me and can I automate it so that it runs at start-up. I would like it to run in the background but i'm not sure if that's possible.

Here is my the content of my shell script file so far...

#! /bin/bash
sudo ~/tmp/xboxdrv-linux-0.4.10/xboxdrv

---

### Post by Grumbel on 2010-08-01
System->Preference->Startup Applications, add your script there. To get a terminal window you might try something like:

gnome-terminal --title "Xboxdrv" -e "/your/xboxdrv/start/script"

---

### Post by skript_teaze on 2010-08-05
> **Grumbel said:**
> System->Preference->Startup Applications, add your script there. To get a terminal window you might try something like:

gnome-terminal --title "Xboxdrv" -e "/your/xboxdrv/start/script"

Thanks for all the help I've got it setup how I want it now. I hope I haven't annoyed you too much with my endless questions. I'm pretty new to linux/Ubuntu if you hadn't guessed... I really appreciate the support.

Matt

---

