---
title: "Minor problems (absolute beginner)"
date: 2009-07-28
forum: New to Ubuntu
---

### Post by hihihi100 on 2009-07-28
Hi there:    In totally new on this: I started using Ubuntu 8.10 a week ago, but it seems there are some things I still cannot control.    I dont know if this may have some kind of relationship with the problems the OS shows:  I have an AHTEC laptop, that gave me the option of choosing between 3 different OS: 2 windows based and “other”, the one I chose to install Ubuntu. Should I download anything from any site “bypassing” Ubuntu?   The drivers CD I found enclosed includes a detailed explanation of those (the Drivers)... just for Windows Vista... Is there any site from which I can download any needed Driver?    Cannot change the password. When I authenticate my current password, the menu just shows the “clock” icon, for an unlimited period of time, until I close the window. The rest of the system can work.    Cannot use the “terminal” either. I can copy commands into it, but then, the system ask for my password, Ubuntu wont let me write absolutely anything... It blocks itself (just this application, I can use the rest of the system, use Internet, open office...)    Cannot use Pidgin Internet messenger either... it seems I’m “unable to authenticate”    Cannot change the visual effects to a superior level. “desktop effects cannot be enabled”    About the hardware I use: is there any way Ubuntu can tell me what is my graphics card model? I know its a NVIDIA...Is there any application that lets the user know everything (both software and hardware)  installed in the laptop/computer?    Thanks in advance.

---

### Post by sandyd on 2009-07-28
if you got ubuntu preinstalled, you should simply download 9.10 from ubuntu.com. 8.10 is kindof out of date. when you type your password in the terminal, it won't show an entry. this is for security reasons. however, rest assured that your password is being entered properly. to change your password, you can enter ```
sudo passwd <username>
``` replace <username> with your username. the easy way to install nvidia drivers is to type this in. ```
sudo apt-get install envyng-core
``` then ```
sudo envyng -t
```. that will automatically detect your video card. you can also install from the nvidia site, but that requires your video card model. to find that, run ```
lspci
```. that will list all your computers hardware

---

