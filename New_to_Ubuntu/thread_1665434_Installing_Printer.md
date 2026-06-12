---
title: "Installing Printer"
date: 2011-01-12
forum: New to Ubuntu
---

### Post by smooth65 on 2011-01-12
Hello everyone. New and learning here. I am attempting to install my lexmark Z2420 printer. I downloaded the necessary file to install but before I can fininsh with the installation, its asking me for a root password. I input the password from my initial installation of ubuntu but its not accepting it. Any ideas?

---

### Post by mikewhatever on 2011-01-13
Make sure the password is typed correctly. ;)

---

### Post by smooth65 on 2011-01-13
I did type the password correctly. Is it asking for the same password that I use when I installed ubuntu? If so, I typed exactly the way it should be. Confused here. Very new here so sorry for the double post. Did not realize that my previous question was replied to.

---

### Post by mikewhatever on 2011-01-13
Yes, the password to use is your user password.

---

### Post by anglican on 2011-01-14
> **smooth65 said:**
> Hello everyone. New and learning here. I am attempting to install my lexmark Z2420 printer. I downloaded the necessary file to install but before I can fininsh with the installation, its asking me for a root password. I input the password from my initial installation of ubuntu but its not accepting it. Any ideas?Some installers do require a root password to work (I've had this problem with other software). One solution is to actually set a root password, which you can do with:
```
sudo passwd root
```You can remove the root password afterwards by editing the file /etc/shadow and changing the test between the first two colons to an asterisk (*).

H

---

### Post by cloyd on 2011-01-14
I've had the same problem with lexmark. I think there is another, and better solution (I used the one just listed, but I understand that establishing a true root account has its dangers).

Instead of using the ordinary file browser, go to terminal and "gksudo nautilus" to open a file browser window with root privileges. Navigate to your install file and install from this window. After a new install, I used this . . . it is really easier (who wants to remember 2 root passwords, anyway?).
You will only be asked for your password as you open nautilus from the terminal, and the driver install will not ask for it. 

Best of luck to you. Next time, I'm buying another HP. But like you, I have to use what I have if it will work at all.

---

