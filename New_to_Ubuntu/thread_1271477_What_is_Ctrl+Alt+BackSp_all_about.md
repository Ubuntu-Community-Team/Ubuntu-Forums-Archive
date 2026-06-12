---
title: "What is Ctrl+Alt+BackSp all about?"
date: 2009-09-20
forum: New to Ubuntu
---

### Post by jfloydb on 2009-09-20
What is Ctrl+Alt+BackSp all about? What does it do? Why should I want it? How can I enable it in Jaunty? AND how can I dis-able it if I don't like it? Thanks.

---

### Post by ankspo71 on 2009-09-20
If you ever use your computer, and something on your desktop freezes up, or the entire desktop freezes up, you can use ctrl+alt+backspace to kill the display and log you out. When you log back in, everything should be return back to normal.

If you want it installed in 9.04 you have to open up a terminal and type the following:
```
sudo apt-get install dontzap
```
Then you enable it by disabling dontzap
```
sudo dontzap --disable
```
The ctrl+alt+backspace will take effect after you reboot.

Edit: You can then disable it by doing the opposite of the command above:
```
sudo dontzap --enable
```

Hope this helps.
James

---

### Post by Cheezespread on 2009-09-20
What is it about && what does it do ?
[https://wiki.ubuntu.com/XorgCtrlAltBackspace](https://wiki.ubuntu.com/XorgCtrlAltBackspace)

How do I enable it in Jaunty ?

[https://wiki.ubuntu.com/X/Config/DontZap?action=show&redirect=DontZap](https://wiki.ubuntu.com/X/Config/DontZap?action=show&redirect=DontZap)

---

### Post by ankspo71 on 2009-09-20
Hi, 
I don't have the option to use "Key sequence to kill the X server" in my "USA With EuroSign on 5" layout options. Does anyone else? I currently don't have dontzap installed either because I did a fresh reinstall and forgot about it, so it can't be because of that.
James

---

### Post by Paqman on 2009-09-20
Alt-SysRq-K does the same as Ctrl-Alt-Backspace, and is enabled by default on Jaunty.

---

### Post by ankspo71 on 2009-09-21
> **Paqman said:**
> Alt-SysRq-K does the same as Ctrl-Alt-Backspace, and is enabled by default on Jaunty.

Thanks. It works perfectly.
James

---

### Post by humphreybc on 2009-09-21
I've never had much luck with Ctrl + Alt + Backspace.

Before it was disabled in Jaunty, whenever I did it in Intrepid it would usually end in severe graphical screwups and then a kernel panic.

Now, in Jaunty, I've installed dontzap and run sudo dontzap --disable and then restarted, and Ctrl + Alt + Backspace does nothing.

But, Alt+SysRq-K intiates a lovely system freeze, crazy graphics and then a kernel panic...

---

