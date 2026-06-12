---
title: "Shutting down Xwindows too install CUDA"
date: 2009-10-20
forum: New to Ubuntu
---

### Post by newport_j on 2009-10-20
I am installing the CUDA 2.3 drivers on Ubuntu 9.04, 64 bit. I need to shutdown Xwindows in order to continue the installation. What is the command for Ubuntu 9.04 64 bit operating system to shutdown Xwindows?

Respectfully,

Newport_j

---

### Post by Zoot7 on 2009-10-20
```
sudo /etc/init.d/gdm stop
```

That'll kill X for you and drop you back to the command line, then call the installer by:
```
sudo sh NVIDIA-Linux* (or whatever the name of the script is)
```

Accept all the options it prompts you and tell it to automatically set the xorg.conf file.


That's assuming you mean the standard nVidia driver.

---

### Post by kellemes on 2009-10-20
Is this thread helping?
[http://ubuntuforums.org/showthread.php?t=1267436]("http://ubuntuforums.org/showthread.php?t=1267436")

---

### Post by martrn on 2009-10-20
If you are running gnome desktop manager then the gnome display manager will be responsible for starting your x11 session.

Type:
```
sudo /etc/init.d/gdm stop
```

## List of stuff to install CUDA
## List of other stuff to do in a terminal

Then to start gdm again:
```
sudo /etc/init.d/gdm start
```

or replace with kdm if using kubuntu or kde.

---

### Post by newport_j on 2009-10-20
Yes that shuts it down alright. But it leaves you with a blinking cursor that seems frozen on the command line. Any further command line entry after that is impossible. 
All you have is a blinking horizontal line which represents the cursor.  How do you get to the point of actually entering additional data once xwindows is shut down?

Newport_j

---

### Post by kanikilu on 2009-10-20
I think you want to switch to a virtual console first. Press CTRL+ALT+F1, login, stop GDM, then proceed with the driver install.

I wish I had written down the exact steps I took, as I just recently installed the CUDA drivers and toolkit on our server connected to a 1U Nvidia Tesla at work. I eventually got everything working, but there were a few issues I had to work out one at a time. Post here if you have further questions and I'll see if I can help...

---

### Post by martrn on 2009-10-20
Ctrl + Alt + F1 ... to goto the first virtual terminal
Ctrl + Alt + F2 ...  to goto the second virtual terminal
Ctrl + Alt + F2 ...  to goto the third virtual terminal
Ctrl + Alt + F2 ...  to goto the fourth virtual terminal
Ctrl + Alt + F2 ...  to goto the fifth virtual terminal
Ctrl + Alt + F2 ...  to goto the sixth virtual terminal
Ctrl + Alt + F7 ...  to goto the terminal session with X (?flashing cursor?)

---

