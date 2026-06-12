---
title: "Error message on new installation"
date: 2010-11-17
forum: New to Ubuntu
---

### Post by Kbaynes on 2010-11-17
This is my first foray into using Linux OS. I have a home built desktop with 70 GB hard drive currently split into 3 separate partitions. I have Windows XP as the original OS installed, but I wanted to create a dual boot PC as not sure about how compatible Ubuntu is going to be with some of my software. 

I installed Karmic koala version of Ubuntu from a CD alongside Windows using the automatic software. When I first used it everything seemed fine, but on the second boot it went wrong. When I boot using the Ubuntu software the log in screen appears. I log on, but an error message comes up. "Install problem. Configuration defaults for Gnome power manager have not been installed correctly."

All I can do then is to switch off the machine.

I am stuck and do not how to work around this. I thought about uninstalling the software and starting again, but I cannot work out you do this in Linux!

I am not at all confident about typing in code commands, but I seem to be able to open a terminal window if I boot the software from a CD without installing it.

Can anyone help me gently?

Kevin
London

---

### Post by sikander3786 on 2010-11-17
Hi and Welcome to the forums :-)

Press Ctrl + Alt + F1 at your login screen. You will see command prompt. Log in using your credentials and try these commands,

```
sudo dpkg --configure -a
```

```
sudo apt-get install -f
```

Press Ctrl + Alt + F7, you'll see the login screen again. Try to login. If unsuccessful, please post the errors if any returned by the above commands and also output of this command.

```
ls /home
```

---

### Post by Kbaynes on 2010-11-17
Hi! Thanks for the reply.

I tried the commands you suggested. No error messages came up.

I still cannot log in.

The same error message comes up

"Install problem! The configuration defaults for Gnome power manager have not been installed correctly. Please contact your computer administrator."

The result of the command ls /home was

Kbaynes

This is, of course, my username.

Thanks for your attention.

Kevin

---

### Post by sikander3786 on 2010-11-17
Ok.

Are you sure your root partition is not running out of space?

```
df -h
```

---

### Post by eriktheblu on 2010-11-17
First thing I'd try:
```
sudo aptitude reinstall gnome-power-manager
```

---

### Post by wojox on 2010-11-17
I would just reinstall it. Make sure you get a good burn at the lowest speed. Another thing is to try without installing, to see if everything runs okay. 

Welcome aboard. :)

---

### Post by Kbaynes on 2010-11-17
I ran the command

df -h

This returned as the first line

/dev/sda7    Size 7.8 GB   Used 100 per cent

This maybe suggests that there is a disk space problem, but I do not know how to fix it.

Kevin

---

### Post by sikander3786 on 2010-11-17
Ubuntu itself doesn't take up that much space. Did you copy some of your personal data in that drive?

You can clean up a few hunder mega bytes by

```
sudo apt-get clean
```

Try log in again, if successful, move your files to some other drive.

If you can't login, boot from a Live CD and move your files around.

---

### Post by Kbaynes on 2010-11-17
I do not have any personal data on this drive. All my personal data is on the d: and e: drive partitions.

Kevin

---

### Post by sikander3786 on 2010-11-17
I don't know then what is taking about 8 GB of disk space.

If you don't have any valuable data on this drive, I'd also go for a re-install now and increase the size of Ubuntu partition if possible.

---

### Post by Kbaynes on 2010-11-17
How do I do a re-install??

Sorry, I am a true beginner!

---

