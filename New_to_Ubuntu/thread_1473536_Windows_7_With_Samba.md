---
title: "Windows 7 With Samba"
date: 2010-05-05
forum: New to Ubuntu
---

### Post by Mogrix on 2010-05-05
I installed samba on my Linux machine (10.04) and am new to Ubuntu.

I've already right clicked the folders i want to share and enabled Sharing on them on the Linux machine. 

My windows 7 laptop can find the Linux Computer from the Network, but when i try to access the folder i wanted to share from Linux, i get a pop up on windows asking for username and password.

I've tried the username/password I've set up on my Linux machine, but that hasn't worked. 

I've also tried Googling this problem but it doesn't seem to be a common problem, so it must be isolated to me, and not knowing what i'm doing -- it's probably something i'm just not getting. 

Any help on fixing this?

---

### Post by Troublegum on 2010-05-05
I recommend to install the package [FONT=Courier New]system-config-samba[/FONT] that gives you a graphical interface for configuring your samba server.

Regarding the login data: samba server has its own user directory. You manually have to add every user that has access to your shares. With the [FONT=Courier New]system-config-samba[/FONT] package, you can easily do that without using the terminal. You just have to go to System -> System -> Samba.

---

### Post by Mogrix on 2010-05-05
Thank you so much. this configured everything.

I used the GUI interface to add the Windows User to the accepted list like you suggested and no more permission issues.

You have my gratitude. =]

---

