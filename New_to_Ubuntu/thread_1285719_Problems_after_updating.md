---
title: "Problems after updating"
date: 2009-10-08
forum: New to Ubuntu
---

### Post by SDU2112 on 2009-10-08
Hello

I am completely new to the linux experience so do please bear with me.

Last night I noticed that my newly installed version of ubuntu required updating so I updated it - no problems there.

It also said that I should update some drivers - a driver for my broadcom wireless card and an nvidia driver.  Fair enough I thought and set it to do that too.  However, when I restarted my machine it would not start up.  It appears to be getting part of the way through and then seems to hang with the screen showing half black and half orange/brown.

Any suggestions as to how I can get myself out of this situation?

---

### Post by Peter09 on 2009-10-08
Hi,
a little bit of information please - what version of ubuntu and what type of machine?

You can try hitting escape as soon as you seen the Grub line (almost the first thing you see after the bios).
This will give you a menu, use the arrow keys to go down one line and select the recovery boot. This will boot into a menu, which includes the item to reconfigure your video drivers - try that.

---

### Post by SDU2112 on 2009-10-08
Hi

It's an old Dell Inspiron laptop (can't remember what number sorry - I'm at work) and it's got ubuntu 9.04 on it.

I don't know if it makes a difference but I set it up as a dual boot machine so it had Windows XP on it first and then I let ubuntu partition the drive and what have you and then instal itself.

---

### Post by Peter09 on 2009-10-08
OK -9.04 is still in development and not a final and stable release - so some issues are to be expected. Having said that most people using it are getting a stable and working system. As I suggested earlier, try getting into recovery mode and see if that helps.

If what I suggested does not help you can get into command mode from the recovery menu and issue the following terminal commands.

```
sudo apt-get update
```

```
sudo apt-get upgrade
```

These commands will update the system to its latest configuration - (you will need a wired connection for this)

---

### Post by SDU2112 on 2009-10-08
OK, thanks

I'll give that a try and see where I get.

---

### Post by mikechant on 2009-10-08
> OK -9.04 is still in development and not a final and stable release - so some issues are to be expected. 

You're thinking of 9.10, which is in beta testing at present.
9.04 was finalized and released in April 2009 (hence the version - year 9, month 4)

---

### Post by Peter09 on 2009-10-08
Whoops - your are right:confused:

---

