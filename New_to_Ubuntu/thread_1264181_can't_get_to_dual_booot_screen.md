---
title: "can't get to dual booot screen"
date: 2009-09-11
forum: New to Ubuntu
---

### Post by AndyP79 on 2009-09-11
Hi All,
 Okay, so I just dual booted EasyPeasy with my Mint. Everything seems fine, but....When i turn the computer on, manufactures screen goes, then the dual boot screen flashes by so quick that I can not choose Mint or EasyPeasy. How do I fix this so I can?
Thanks in Advanced

*Edit*
Okay, so I did some googling, and maybe I don't have Mint mounted? When I start up, I have tried esc, or f10 and still I can not get the boot choice menu to stay long enough. I can see it as it flashes by, but it's too quick...so, do I need to mount the Mint section?

---

### Post by yeats on 2009-09-12
When you installed Mint, did you create a new GRUB configuration (would have been the last step in installation)?  Sounds like you need to increase the timeout for GRUB (there is a graphical frontend in the repositories called startupmanager that's more user-friendly than manually editing the /boot/grub/menu.lst file)

---

### Post by TobiasV on 2009-09-12
Here's a step by step tutorial to what chrissharp123 says.

Open up your terminal (alt+f2 > gnome-terminal).
Enter "sudo apt-get install startupmanager".
Enter your password.
Go to System>Administration>StartUp-Manager
You might have to enter your password again
Click on the Boot Options tab.
Increase the number under the "Timeout" setting.

---

