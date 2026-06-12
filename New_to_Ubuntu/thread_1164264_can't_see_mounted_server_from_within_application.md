---
title: "can't see mounted server from within application"
date: 2009-05-19
forum: New to Ubuntu
---

### Post by Pedroparamo on 2009-05-19
I've installed a new app (LightZone) and I have it running.  When I use the GUI and try to open a file I can't see any of my files or a mounted server volume (and its contents.)   If I were using windows I would be looking for 'My Computer'...

I just see a directory / and sub directories such as bin, boot, cdrom, dev, etc, home...

How do I get to my computer to find my server files?

I'm using a terminal window to run the app and the only files I see in the app GUI are those located in the same directory from where the application is launched.  How do I fix this?

Thanks.

Pedro

---

### Post by Celauran on 2009-05-19
Your personal files are in /home/$yourusername

---

### Post by Pedroparamo on 2009-05-19
What about a mounted (sftp) server volume?  How can I see it from within the application GUI?

Pedro

---

### Post by Celauran on 2009-05-19
It should have its own entry in the menu tree, outside of filesystem. If not, you should be able to find it under /home/username/.gvfs

---

### Post by Pedroparamo on 2009-05-19
Nothing in the menu tree or in the /home/username/.gvfs--I don't have anything called .gvfs.???

Pedro

---

### Post by Pedroparamo on 2009-05-19
It's visible in other apps but not the one I'm trying to use.  I suspect it is because I am launching the app from terminal and I'm stuck inside of that directory.

I'm new to Ubuntu and this may sound like a crazy question but is there a way to launch an app and then change the directory while that app is still running in terminal?

thanks.

Peter

---

### Post by Celauran on 2009-05-19
You can append & to the launch command to make it run in the background. If it's currently running in the foreground, you can hit CTRL+Z to send it to the background.

---

### Post by Pedroparamo on 2009-05-19
Ctrl+Z (in terminal window) kills the app for me.  I managed to make an application icon from which I can launch LightZone, but my directory tree is not right.  I still can't see my server volume which is mounted on my desktop.

Any suggestions??

Pedro

---

