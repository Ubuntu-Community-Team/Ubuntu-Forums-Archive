---
title: "Upgrade login lockout 10.10"
date: 2011-05-29
forum: New to Ubuntu
---

### Post by Epiphileon on 2011-05-29
I was using ubuntu 10.x and used update manager to upgrade to 10.10, when I restarted my system, I was presented with a login screen I'd never seen before.  I have tried numerous possible user names, including "administrator", and my password from my previous version, nothing works. 
Is there anyway around this problem?

---

### Post by wildmanne39 on 2011-05-29
> **Epiphileon said:**
> I was using ubuntu 10.x and used update manager to upgrade to 10.10, when I restarted my system, I was presented with a login screen I'd never seen before.  I have tried numerous possible user names, including "administrator", and my password from my previous version, nothing works. 
Is there anyway around this problem?
Hi, what user name and password for the user did you use when you set up the previous version? If you have to you can reset the password, make sure you cap locks have not been on, here is a link to reset it if you need to. [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by Epiphileon on 2011-05-29
> **wildmanne39 said:**
> Hi, what user name and password for the user did you use when you set up the previous version? If you have to you can reset the password, make sure you cap locks have not been on, here is a link to reset it if you need to. [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)
I do not recall having set one, other than the default "administrator".

---

### Post by Epiphileon on 2011-05-29
Okay so searching the web I found a procedure that had me hit escape at the "GRUB" prompt during startup. To then edit the kernal line to add, "**rw init=/bin/bash**"
Then reboot, into passwordless root shell and type, "**passwd **username" for username I just added my firstname.
It asked me to type new password, and confirm it. Then I had to use the reset button to reboot as for some reason the reboot command did not do it.
Now my system is booting, accepting my login, but booting into terminal mode, now I just need to find out how to get it back to GUI boot.

---

### Post by wildmanne39 on 2011-05-29
> **Epiphileon said:**
> Okay so searching the web I found a procedure that had me hit escape at the "GRUB" prompt during startup. To then edit the kernal line to add, "**rw init=/bin/bash**"
Then reboot, into passwordless root shell and type, "**passwd **username" for username I just added my firstname.
It asked me to type new password, and confirm it. Then I had to use the reset button to reboot as for some reason the reboot command did not do it.
Now my system is booting, accepting my login, but booting into terminal mode, now I just need to find out how to get it back to GUI boot.
Hi, did you use the link I gave you to reset your password?

---

### Post by Epiphileon on 2011-05-29
> **wildmanne39 said:**
> Hi, did you use the link I gave you to reset your password?
No although it seems like the very same procedure, I will try that as some of the precursor steps seem different; however, I am able to login now. I found another thread here, [**10.10 only opens in a terminal mode**]("http://ubuntuforums.org/showthread.php?t=1638040"), I followed the procedure in the 3rd post, nothing changed. I did the **lspci | grep VGA, **and got information on my nVidia card.  Then I chose the desktop safe mode from a drop down menu at the login screen and "poof" it came up in GUI mode. I don't know what will happen when I reboot again first I'm going to check into my graphics drivers, which will also be a learning experience.

---

### Post by Epiphileon on 2011-05-29
Okay, went my system/administration menu, chose nvida x-server settings, got an error message saying the drivers were not loaded, went to terminal,  accessed root by typing sudo su, then ran the command the error message gave me.
[SIZE=3]Problem Solved[/SIZE]

---

### Post by wildmanne39 on 2011-05-29
> **Epiphileon said:**
> Okay, went my system/administration menu, chose nvida x-server settings, got an error message saying the drivers were not loaded, went to terminal,  accessed root by typing sudo su, then ran the command the error message gave me.
[SIZE=3]Problem Solved[/SIZE]
Hi, that great, your drivers for that card can be found in additional drivers.

---

