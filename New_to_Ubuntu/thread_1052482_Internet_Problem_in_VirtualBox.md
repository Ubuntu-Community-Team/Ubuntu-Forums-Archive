---
title: "Internet Problem in VirtualBox"
date: 2009-01-27
forum: New to Ubuntu
---

### Post by YoungD112 on 2009-01-27
So I just got VirtualBox and installed Windows 7 on it.  The problem I'm having is I can't connect to the internet within VirtualBox.  Does anybody have a solution?

---

### Post by YoungD112 on 2009-01-27
Anybody?

---

### Post by XanderCrews on 2009-01-27
Just a guess here, but it sounds like a Windows 7 problem.

XC

---

### Post by medley on 2009-01-27
> **YoungD112 said:**
> So I just got VirtualBox and installed Windows 7 on it.  The problem I'm having is I can't connect to the internet within VirtualBox.  Does anybody have a solution?

The latest version of VBox (2.1.2) supports Win 7 as a guest so make sure you are using that rev. Check your network settings for the VM; I use 'connect to host' (or however it's described; I'm in VBox now and can't check the settings while the VM is running). That will make your Win 7 VM part of your local subnet (ie, if your host is 192.168.1.2, for example, your guest will be assigned an address in the same range, so that it can access your real world network). FWIW, VBox works very well, including networking. I'm using Kubuntu 8.10 right now within VBox on top of Vista.

Good luck

---

### Post by YoungD112 on 2009-01-27
> **medley said:**
> The latest version of VBox (2.1.2) supports Win 7 as a guest so make sure you are using that rev. Check your network settings for the VM; I use 'connect to host' (or however it's described; I'm in VBox now and can't check the settings while the VM is running). That will make your Win 7 VM part of your local subnet (ie, if your host is 192.168.1.2, for example, your guest will be assigned an address in the same range, so that it can access your real world network). FWIW, VBox works very well, including networking. I'm using Kubuntu 8.10 right now within VBox on top of Vista.

Good luck

Thanks.  I had an older version so I'm going to try again after I get the latest...

---

### Post by pHreaksYcle on 2009-01-27
Please make sure to mark this thread as solved if you get it running!

---

### Post by Mason Whitaker on 2009-01-27
You could just use the "Install Guest Addons" option :P

Just installs all the right things to make your VB experience better ( Internet, Seamless mode, ect )

---

