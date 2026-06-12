---
title: "keyring password very annoying"
date: 2008-01-01
forum: Networking &amp; Wireless
---

### Post by bigmonmulgrew on 2008-01-01
when I logon I'm asked to enter the password for the keyring. Under the password box is a check bow to automatically logon. when I enter my password it pops straight up and asks for it again this time without the check box.  I want it gone completely so I don't need to keep entering password. Please help. Cheers

---

### Post by jonny5tails on 2008-01-01
Go to System\Admin\login window & under security, check the box for "Enable Automatic Login" for yourself. When you reboot, you'll bypass the logon screen & right into Ubuntu.

---

### Post by bigmonmulgrew on 2008-01-02
thats for user logon I mean for wireless network logon

---

### Post by andyclaxn on 2008-01-02
Hi, I'm on Feisty, on one machine and Gutsy on another, and I found a link that gives really simple instructions how to do this in Ubuntu.  The address is:

[http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)

Just follow the instructions and then go to System, Administration, then Network. You can then click on your wireless connection and you must re-enter your Network Name (ESSID) and your network password.

That's it. Hope this helps. Worked for me and took about 5 minutes.
regards Andy

Shiny shoes, shiny mind!

---

### Post by andyclaxn on 2008-01-02
Just found another problem, when you re-boot you may lose your wireless connection. The fix is simple, just remove any other wireless manager that you have via add/remove in Applications or with synaptic package manager, and then re-install Wicd as before. I have rebooted five times now and all seems to be going well.
Sorry
Andy

---

### Post by bigmonmulgrew on 2008-01-09
As soon as I selected it for install it automatically offered me the chance to remove the old network manager. Worked a treat cheers

---

