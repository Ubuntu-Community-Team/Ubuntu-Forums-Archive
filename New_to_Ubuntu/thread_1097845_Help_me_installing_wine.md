---
title: "Help me installing wine"
date: 2009-03-16
forum: New to Ubuntu
---

### Post by peopke on 2009-03-16
I just installed Ubuntu (with parallels) on my IMac.
i want to install wine but i dont know how to start with it. I never touched an ubuntu or other linux operating systems.
can someone say me how to do it  step-by-step. I dont know anything of linux :( so if u say install explain how to install it.
i have ubuntu 8.1.0

tnx anyway!

---

### Post by taurus on 2009-03-16
[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

---

### Post by mvalviar on 2009-03-16
Go to Application>Accesories>Terminal. Then type ```
sudo apt-get install wine
``` You will be prompted for you password type it in (you will not see any character as you type your password). Wait for the installation to finish. Once installed you should see a Wine sub-menu under Applications. To install windows programs you can simply double click the setup executable. 

Your virtual C:\ drive is under /home/yourusername/.wine. This folder is hidden. To show hidden folders hit Ctrl-H. An easier way to browse your virtual C:\ drive is to access it through the wine sub-menu.

---

### Post by peopke on 2009-03-16
can u please say it more detailed i still dont get it :(

---

### Post by Thelasko on 2009-03-16
[First read this.]("http://www.psychocats.net/ubuntu/installingsoftware")

[Then read this.]("http://www.psychocats.net/ubuntu/wine")

---

### Post by roger_1960 on 2009-03-16
Hi

First open a terminal and do what mvalvier said ie enter (or copy and paste from this post) 
> sudo apt-get install wine

Then enter your password.  Wait for it to get back to a prompt, then type:

> winecfg

This will create the folders which wine uses for windows apps.

Then copy the windows .exe file into an easy location on your PC eg the Desktop

In terminal, go to that directory by going
> 
cd /home/yourusername/Desktop

(note upper case in Desktop)

Then enter
> 
wine whatever.exe

This should install from "whatever.exe" and create GUI menu items under a Wine entry which you just created. (whatever.exe is the setup file for your windows program - often its called setup.exe)

I agree that you should read the Psychocats articles - its a great reference for Ubuntu

Hope this helps.

---

### Post by Thelasko on 2009-03-16
Don't become dependent on Wine as a replacement for Windows, it's not.  Native Ubuntu programs will run better than Windows programs running in Wine.

Wine is a very tempting crutch to new users.

---

