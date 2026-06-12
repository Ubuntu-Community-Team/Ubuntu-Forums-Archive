---
title: "sudo password in ubuntu10.10"
date: 2011-02-17
forum: New to Ubuntu
---

### Post by Jon Anderson on 2011-02-17
I tried to find the set resolution setting by using terminal and it said  that it needed sudo password  and I dont think I know what that  password is and I cant check what I think it might be because the  keyboard wont type in the terminal after it asks for sudo  password,nothing types in keyboard quits

---

### Post by kellemes on 2011-02-17
> **Jon Anderson said:**
> I tried to find the set resolution setting by using terminal and it said  that it needed sudo password  and I dont think I know what that  password is and I cant check what I think it might be because the  keyboard wont type in the terminal after it asks for sudo  password,nothing types in keyboard quits

The terminal does not show your typing, but it's registering the password just fine..
Enter your password and hit <ENTER>

---

### Post by lisati on 2011-02-17
Some more information about Root & Sudo can be found here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Jon Anderson on 2011-02-17
Thank you, what Im trying to do is find a way to get into vesa mode .I Found the vesa vga=773 that I need but dont know how to install the line. So by my reading your suplied page I shouldnt use sudo because I could crash the whole system and since I know so little about what Im doing (I have been a user for maybe a week) Ill pass on using sudo if I can.

---

### Post by lisati on 2011-02-17
Changing system settings is something that can mess things up, which is why many situations require "admin" privileges, also known as "root" privileges. This adds a layer of protection against accidents and malicious software.

---

### Post by hansolo4949 on 2011-02-17
Yes, your sudo password is usually the password for the first (administrator) account. It does not show your typing, but it is registering your keystrokes. You should be careful about using sudo, because it allows you, or another program, to do things on your computer which may be helpful, but one slip, and you just deleted a critical file using sudo because you thought it was a file you wanted to get rid of to free up hdd space, or something similar.

---

### Post by dee_exlusive on 2011-02-18
hello is it possible to change my password in ubuntu10.10?..  If it is.. does somebody know how?

---

### Post by megabuffen on 2011-02-18
Sure, open a terminal and enter the command "passwd". It will ask you for your old one and then the new one and a confirmation. Typing your password will work, but no letters will show up.

To open the terminal, just look for the "Terminal" program in the programs menu. Alternately, you can just press Ctrl+Alt+F6, login with username and password, issue the command, and press Ctrl+Alt+F7 to get back to your desktop.

---

### Post by perspectoff on 2011-02-18
> **megabuffen said:**
> Sure, open a terminal and enter the command "passwd". It will ask you for your old one and then the new one and a confirmation. Typing your password will work, but no letters will show up.

To open the terminal, just look for the "Terminal" program in the programs menu. Alternately, you can just press Ctrl+Alt+F6, login with username and password, issue the command, and press Ctrl+Alt+F7 to get back to your desktop.

That should be

sudo passwd

---

### Post by megabuffen on 2011-02-18
No, sudo passwd will also work, but root privileges are not necessary to change one's own password. I tried it on my own Ubuntu 10.10 installation and it worked just fine.

---

