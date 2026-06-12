---
title: "How to safely boot into tty instead of X at startup?"
date: 2011-08-21
forum: New to Ubuntu
---

### Post by zengrz on 2011-08-21
Awhile ago, I reformatted my hard drive after upgraded the system to 11.10 because the system was unable to start a graphical session and always boots itself into tty1 (courtesy of NVIDIA). Now, I am on 11.04 and the system boots well (into X) and tty1 is gone.

However, I kind of miss tty and wish it back. How can I boot safely into tty without affecting my X? I probably will still want to use X once in awhile. =D

I have done some research and the two ways I am offered are "set gfxpayload=text" and "sudo apt-get remove gdm". The latter sounds a little bit intimidating, but I haven t try anything yet. I want to still be able to "startx" in the tty whenever I need to. Also, how can I revert the changes?

Thanks!

---

### Post by ajgreeny on 2011-08-21
Removing gdm is no problem; it just means that the system will boot to a cli (tty) and when you want an X session you just use the command **startx**.  It will not affect any other packages as far as I can see.

However, as you have found, there are other ways of getting a cli at boot, and it is really a case of using whatever method you find easiest.

---

### Post by cj13579 on 2011-08-21
When you get to the login screen you can press Alt+F1 to go to a TTY shell. You can go back to your X session by hitting a Alt+F7.

---

### Post by zengrz on 2011-08-23
Found two related posts that solves this problem:

[http://ubuntuforums.org/showthread.php?p=10798400#post10798400](http://ubuntuforums.org/showthread.php?p=10798400#post10798400)

[http://ubuntuforums.org/showthread.php?t=1767191](http://ubuntuforums.org/showthread.php?t=1767191)

Sum up, to disable GDM:
```

echo "manual" | sudo tee -a /etc/init/gdm.override
GRUB_CMDLINE_LINUX_DEFAULT="quiet"
sudo update-grub

```

To start X session in tty:
```

sudo service gdm start

```

To re-enable GDM:
```

sudo rm /etc/init/gdm.override

```

Note 1:
By default, the system will boot into tty7, which is your X session channel. Since you have already disabled GDM, it will show up as a black screen. Press ctrl + alt + (f1 - f6) to switch to a tty, then log in to your account.

Note 2:
Do not use "startx"; use "sudo service gdm start" instead. For unknown technical reasons, "startx" will only give you a incomplete desktop without menu bar and side bar.

Note 3:
The shortcut to my terminal (ctrl + alt + t) was mysteriously set to NULL after I applied these changes. To set the shortcut to your terminal back to (ctrl + alt + t), search for "Keyboard Shortcuts" using the Ubuntu icon at top left hand corner and open it, go to the last entry under "Desktop" category (which is your terminal shortcut), and set it back.
([http://ubuntuforums.org/showthread.php?t=1748836&page=2](http://ubuntuforums.org/showthread.php?t=1748836&page=2))

Cheers.

---

