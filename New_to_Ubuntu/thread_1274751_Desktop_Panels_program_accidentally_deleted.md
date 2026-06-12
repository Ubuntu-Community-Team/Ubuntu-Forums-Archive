---
title: "Desktop Panels program accidentally deleted"
date: 2009-09-24
forum: New to Ubuntu
---

### Post by ricardo.gloe on 2009-09-24
Hello, 

I started using Linux/Ubuntu about three days ago, have been doing well so far. But my curiosity/recklessness got the best of me and I accidentally removed the "panel" program, using the add/remove function from the left top menu. 

Now I have a desktop full of icons but no panel on top or bottom. How can I re-install the program? 

If you can tell me where the terminal program can be opened from the filesystem (I have file browser on my desktop) and tell me how to get the program that restores the panels, I think it will work.

---

### Post by lindsay7 on 2009-09-24
I think if you just right click on where the top panel was you can choose "New panel" and that will put one back where it is supposed to be.

Once you get the panel back, right click on it and click on "add to panel to add what you want..

---

### Post by Mad Hacker on 2009-09-24
press alt-F2 and type in 
```
gksu synaptic
```
to start synaptic, the package you are looking for is probably called 'gnome-panel'

---

### Post by nothingspecial on 2009-09-25
I may be wrong but I don`t think Alt-F2 works without a panel.

Reboot your computer and when you see the bit about grub loading press escape.

Choose recovery mode or failsafe terminal or whatever they call it at the moment, something like that anyway.

Log in and type ```
sudo apt-get install gnome-panel
```

When it`s finished it`s doings type ```
sudo shutdown -r now
```

To reboot.

---

### Post by lindsay7 on 2009-09-25
Just right click on the Desktop screen and choose "open in terminal"!

---

### Post by philinux on 2009-09-25
[http://ubuntuforums.org/showthread.php?t=392387](http://ubuntuforums.org/showthread.php?t=392387)

---

### Post by Wataru8675 on 2009-09-25
> **nothingspecial said:**
> I may be wrong but I don`t think Alt-F2 works without a panel.

Reboot your computer and when you see the bit about grub loading press escape.

Choose recovery mode or failsafe terminal or whatever they call it at the moment, something like that anyway.

Log in and type ```
sudo apt-get install gnome-panel
```When it`s finished it`s doings type ```
sudo shutdown -r now
```To reboot.

Whoa.  You're thinking too hard.  Listen to Lindsay7.

And don't forget to re-add the Notification Area.  I did this exact same thing a few weeks ago and I was DYING without the Notification Area.  It displays your battery life, wireless networks, printer status, and any updates that need to be installed.

---

### Post by cgroza on 2009-09-25
Once i deletet my Xorg...i had to reinstall i was just a newbie....

---

### Post by nothingspecial on 2009-09-25
> **Wataru8675 said:**
> Whoa.  You're thinking too hard.  Listen to Lindsay7.



I`m not thinking too hard, I just don`t use a mouse ;)

---

### Post by mcduck on 2009-09-25
> **lindsay7 said:**
> Just right click on the Desktop screen and choose "open in terminal"!
That only works if he has installed "nautilus-open-terminal". By default the right-click menu doesn't have that option.

Although I agree that recovery mode is not really required for this, pressing Ctrl-Alt-F1 to enter a TTY would do the trick just fine (besides, "sudo" isn't needed in recovery mode since it opens a root shell).

---

### Post by nothingspecial on 2009-09-25
> **mcduck said:**
> That only works if he has installed "nautilus-open-terminal". By default the right-click menu doesn't have that option.

Although I agree that recovery mode is not really required for this, pressing Ctrl-Alt-F1 to enter a TTY would do the trick just fine (besides, "sudo" isn't needed in recovery mode since it opens a root shell).

true

---

### Post by wolvenfamily on 2010-12-09
> **mcduck said:**
> That only works if he has installed "nautilus-open-terminal". By default the right-click menu doesn't have that option.

Although I agree that recovery mode is not really required for this, pressing Ctrl-Alt-F1 to enter a TTY would do the trick just fine (besides, "sudo" isn't needed in recovery mode since it opens a root shell).

first i know this thread is old, but i am on a dell vostro with ubuntu 10.10 and after removing evolution (even after it warned it would remove the panel i did it anyway :( ), but i thank you for having this thread here, doing the above then doing the commands of:

sudo apt-get install gnome-panel (i belive my own hand written note says)
then sudo shutdown -r now saved my bacon!

i want to tip my hat to the person that said to add the notification app to the panel, again thank you to you very much! i now have the volume option and mail, ect where it was when i got this laptop a week ago (yes i was "toying" with it and deleted that too...

you people are the best!!!

---

