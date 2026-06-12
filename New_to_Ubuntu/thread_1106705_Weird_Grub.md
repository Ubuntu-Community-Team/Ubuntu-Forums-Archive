---
title: "Weird Grub"
date: 2009-03-26
forum: New to Ubuntu
---

### Post by loseby on 2009-03-26
For some reason Memtest has become the default start up for Grub. I have run Memtest and no problems with memory but it still remains the default bootup .  Now I want my WinXP to once again become my default startup but cant remember how I did it originally. I guess there isnt a simple little program and instead I have to use "Terminal" which I really am not comfortable with. 

Anyhelp with some detailed instructions ?

---

### Post by logos34 on 2009-03-26
change the ["default"]("http://users.bigpond.net.au/hermanzone/p15.htm#menu.lst") line in /boot/grub/menu.lst

---

### Post by kanikilu on 2009-03-26
If you're not comfortable with doing things in the terminal or editing the menu.lst file manually, you might try installing the *startupmanager* package, which will give you a GUI interface to do things like this.

Once you install it, you can run it from System > Administration > StartUp-Manager.

---

### Post by loseby on 2009-03-27
> **kanikilu said:**
> If you're not comfortable with doing things in the terminal or editing the menu.lst file manually, you might try installing the *startupmanager* package, which will give you a GUI interface to do things like this.
.


Startup manger was already there and it had Ubuntu 8.10 Memtest86+ as the default operating system, Why it did this I don not know but have now picked XP . Rarely use Ubuntu on this PC butits the main boot on my other computer

---

