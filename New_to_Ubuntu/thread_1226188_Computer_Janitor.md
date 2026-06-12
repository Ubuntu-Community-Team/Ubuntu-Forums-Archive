---
title: "Computer Janitor"
date: 2009-07-29
forum: New to Ubuntu
---

### Post by MikesGuitar on 2009-07-29
I have CJ installed but cannot find it in system tools. To access it I had to uninstall and install it again. How can I start this program easier in the future, or create an applet or icon? Something in terminal maybe?

---

### Post by NightwishFan on 2009-07-29
System -> Administration -> Computer Janitor on GNOME

I am not sure how to start in terminal, however, you can use tab to autocomplete or search for it using this command.

```
apropos janitor
```

I would be able to help more, however I am on Windows now...

---

### Post by philinux on 2009-07-29
In Jaunty it's installed by default in System>admin since it requires your password to run.

Also be careful with it.

---

### Post by MikesGuitar on 2009-07-29
Yea I hear that it can be a little risky. The only thing I need it for is after I install updates, the GRUB menu displays several Ubuntu versions ( all 9.0 but they say 9.0 11-16-13 -11-16-14 or something like that.)

---

### Post by philinux on 2009-07-29
Installing startupmanager can tidy grub up to your liking. I always like having 2 kernels showing just in case a new one plays nasty.]

[apt://startupmanager](apt://startupmanager)
[URL="http://apt/"]
[/URL]

---

### Post by superprash2003 on 2009-07-29
i thought computer janitor comes by default.. i dont think you need to install it

---

### Post by bodhi.zazen on 2009-07-29
> **superprash2003 said:**
> i thought computer janitor comes by default.. i dont think you need to install it

It is installed by default starting with 9.04

FYI: Ubuntu is not windows and these cleaning tools are not required the way they are in windows.

I suggest you use them with caution and review the changes they suggest rather then using the tool blindly.

---

### Post by wojox on 2009-07-29
> **bodhi.zazen said:**
> It is installed by default starting with 9.04

FYI: Ubuntu is not windows and these cleaning tools are not required the way they are in windows.

I suggest you use them with caution and review the changes they suggest rather then using the tool blindly.

+1 

Stay away from FSlint. Trust me

---

### Post by MikesGuitar on 2009-07-29
Thanks for the info guys. I'll check out the startup manager as a better option for changing the grub menu. I just don't see the point of having several start up choices, aside from the the recovery options.

---

### Post by LewRockwell on 2009-07-29
Editing the grub menu (menu.lst) is a good learning experience and provides a novice with some early success to build upon

Especially since the user sees the grub menu every time they start the machine

You can even edit the grub menu to note space partitioned but not yet used and to leave yourself (or others) important...or not so important notes...

There are plenty of tutorials about editing in general and editing the grub specifically but I did want to include this:```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.old
```Confirm that your original was copied and renamed BEFORE editing and you can always copy the old one back if necessary

.

---

