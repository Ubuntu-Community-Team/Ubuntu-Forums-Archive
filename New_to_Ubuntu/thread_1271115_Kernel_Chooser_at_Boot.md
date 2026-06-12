---
title: "Kernel Chooser at Boot"
date: 2009-09-20
forum: New to Ubuntu
---

### Post by CJWW1989 on 2009-09-20
Everytime I boot up Ubuntu, it has me pick between 4 different Ubuntu kernels, or the XP kernel (I have wubi). How do I make it so it boots strait to Ubuntu's kernel?

---

### Post by infurnus on 2009-09-20
[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

You just need to change your timeout to it won't count down until boot. Google around for changing timeout for menu.lst

---

### Post by cholericfun on 2009-09-20
i vaguely remember theres also an option to skip the option screen unless you press esc on boot-up.

again, theres a lot said about editing menu.lst,
have a go at that

---

### Post by Conzo on 2009-09-20
> **cholericfun said:**
> i vaguely remember theres also an option to skip the option screen unless you press esc on boot-up.
 
again, theres a lot said about editing menu.lst,
have a go at that
 
 
There is a gui Also Called Kgrub in the add/remove 
 
 
Conzo

---

### Post by Old_Grey_Wolf on 2009-09-20
1.  Let it boot into Ubuntu Linux and enter the user name & password to login.
2.  Open a terminal window (hint - use menu - Applications -> Accessories -> Terminal).
3.  Type "sudo apt-get install startupmanager" without the quotes in the terminal.
4.  Enter your password at the prompt, it doesn't display what you type.
5.  After it is installed, go to menu System -> Administration -> StartUp-Manager.
6.  In the window that pops up use the "Timeout" to set it to 2 or 3 seconds.
7. Close the popup window.
8. Restart the computer.

You can customise it more by playing with clicking the check box for show bootloader menu, etc.

I've never tried this with a Wubi install though.

---

