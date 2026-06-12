---
title: "GRUB sometimes boots to OS sometimes it doesn't"
date: 2010-08-31
forum: New to Ubuntu
---

### Post by isaac_moller on 2010-08-31
My computer is relatively new it is an HP Slimline s5310y it has an AMD processor, and I run 4 GB of RAM with Windows 7. My installation of x64 Ubuntu (10.04.1) went as planned, and no hiccups of any sort.
 
The only problem I am having with Ubuntu is my GRUB. I can smoothly boot to Windows 7 by selecting the Windows 7 option, but when I try to boot to Ubuntu it works on an off. When it doesn't boot to the OS it takes me to a black screen that reads: 
Ubuntu 10.4.1 LTS moller-desktop TY1
moller-Desktop Login
and when I punch in my login info I don't get a graphic interface I can browse my folders as if I was using the Terminal. So I have to Ctrl+Alt+Del, it reboots my computer and then back to the GRUB screen, and this time it will boot.

I have run all the updates, don't have anything special installed on it and I have no idea what to do :(
 
Any guidance from the Ubuntu mighty overlords?
Thanks

---

### Post by blazemore on 2010-08-31
A friend of mine had this problem. I don't think he fixed it though.
A workaround: After you log into the TTY text interface you use the command "startx" to load the graphics interface.

---

### Post by MisterLambda on 2010-08-31
When you get to the terminal, log in with your account name, enter your password, (it won't appear when typing, but it's accepting your typing, don't worry) and run the command startx.

---

### Post by isaac_moller on 2010-09-05
Thanks guys.

I figured something else, when I interrupt the normal sequence of boot in grub it almost always freaks out and takes me to the terminal like environment. Now I know the work around for it. Again
Thanks

---

