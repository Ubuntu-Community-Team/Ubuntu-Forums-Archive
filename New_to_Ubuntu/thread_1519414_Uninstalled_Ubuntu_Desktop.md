---
title: "Uninstalled Ubuntu Desktop"
date: 2010-06-28
forum: New to Ubuntu
---

### Post by suyash01 on 2010-06-28
Hi,

I have, by mistake, uninstalled the Ubuntu Desktop (from the Ubuntu Software Center). So naturally I am not able to proceed any further after the login screen.

Can anyone please guide me how to get back a running desktop again?
I have tried installing the desktop system by issuing the following command in the recovery mode:
sudo apt-get install ubuntu-desktop

However it shows some error connecting to "in.archive.ubuntu.com:http//". Earlier, when Ubuntu desktop as running properly, I set up the internet connection and set it to automatically connect on startup. So I don't see any reason why it is not able to connect.

Any help would be appreciated.
-Suyash.

---

### Post by gradinaruvasile on 2010-06-28
Dont boot in recovery mode - the networking may be disabled.
Boot normally, then log in the text console then type:

startx

To start the GUI (x server). Then install whatever you want.

---

### Post by suyash01 on 2010-06-28
> **gradinaruvasile said:**
> Dont boot in recovery mode - the networking may be disabled.
Boot normally, then log in the text console then type:

startx

To start the GUI (x server). Then install whatever you want.
Thanks for the reply.
But how do I log into the text mode if I boot in the normal mode because it is showing only the login screen. When I enter my password it simply re-shows the login screen ?
-Suyash

---

### Post by CharlesA on 2010-06-28
Hit Ctrl + Alt + F1 and see if it asks you to log in.

---

### Post by suyash01 on 2010-06-28
> **CharlesA said:**
> Hit Ctrl + Alt + F1 and see if it asks you to log in.
Ubuntu forums is great (thanks to you people!).
Ctrl+Alt+F1 trick just worked and then I issued the apt-get command which re-installed the ubuntu-desktop.
I have got everything up and running in less than 5 minutes.
Thanks again.
-Suyash.

---

### Post by Chris_cur on 2010-07-11
I am having this same problem but Ctrl+Alt+F1 does not work... anything else?

---

