---
title: "failed to log in Ubuntu"
date: 2010-03-26
forum: New to Ubuntu
---

### Post by bl77122 on 2010-03-26
Hi,

I am %100 brand new to Ubuntu (lots of experience in Windows and a bit of experience in using Fedora). Last night, I installed Ubuntu 9.10 and successfully logged in Ubuntu.  But, after the update manager updated about 124 items, I can't log in anymore (I am able to log in text mode (recovery mode?)). It keeps asking me the password.

I appreciate if anyone guide me to where I can look for solution.

Thank you,

Bruce

---

### Post by coffeecat on 2010-03-26
I don't know why this should happen, but the easiest fix would be to reset the password in the recovery shell. Instructions here:

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

By the way, you don't actually log into recovery mode. You simply get dumped into a root CLI. Which is why you need to take care in recovery mode. :)

---

### Post by Mykk on 2010-03-26
If you can get to the log in screen try, ctrl alt f2 and login in.

Then you could try "sudo apt-get install ubuntu-desktop"

Once thats done press ctrl alt f7 to exit.

Hope this helps :)

---

### Post by bl77122 on 2010-03-26
It is the same Ubuntu is asking me to log in, although I have changed my password.

---

### Post by bl77122 on 2010-03-26
> **bl77122 said:**
> It is the same Ubuntu is asking me to log in, although I have changed my password.
I should have mentioned that changing password didn't solve my problem.

---

### Post by wojox on 2010-03-26
What's the Error message say exactly?

---

### Post by bl77122 on 2010-03-26
> **wojox said:**
> What's the Error message say exactly?

There is no error message.  I just can't log in Ubuntu (gnome session).  After entering my password, the screen blinks and becomes dark and returned to the log in screen asking me the password. I know that my password is OK because I can log in the terminal session.  But, I can't log in the gnome session.

Thank you for your help.

Bruce

---

### Post by Fxy on 2010-03-26
If you can get logged into a command line type > startx  That should load your desktop :D

---

### Post by bl77122 on 2010-03-26
> **Fxy said:**
> If you can get logged into a command line type   That should load your desktop :D

Hi,

It loaded my desktop, but the problem is not solved.

These are what I did.

Log in to recovery mode.
Login
startx
and then restart the computer (from the menu).
the screen goes to text mode ($ prompt).
hit control-alt-del to reboot the computer (dual boot; is this right way to reboot the computer from the command line (with $ prompt?).

I am in the same situation where I can't log in the gnome session.

Any way to fix it permanently?

Thank you,

Bruce

---

### Post by tom.gobel on 2010-03-26
I think the shutdown command is what you're looking for.

To restart, for example, try: sudo shutdown -r

---

### Post by bl77122 on 2010-03-26
> **tom.gobel said:**
> I think the shutdown command is what you're looking for.

To restart, for example, try: sudo shutdown -r

By chance, any idea why I can't log in gnome session even when I can start it by typing 'startx' in the command line mode?

Thank you,

Bruce

---

### Post by wojox on 2010-03-26
Maybe GDM got disabled? To reset it try:

```
sudo update-rc.d gdm defaults 13 01
```

---

### Post by bl77122 on 2010-03-26
> **wojox said:**
> Maybe GDM got disabled? To reset it try:

```
sudo update-rc.d gdm defaults 13 01
```

It doesn't resolve the problem.

Thanks,

Bruce

---

### Post by wojox on 2010-03-26
Is this a wubi install? 
When you get to the gdm screen can you choose sessions > gnome-failsafe?

---

### Post by bl77122 on 2010-03-26
> **wojox said:**
> Is this a wubi install? 
When you get to the gdm screen can you choose sessions > gnome-failsafe?

I am not sure what wubi is.
I can't log in gnome-failsafe either.

Thank you,

Bruce

---

### Post by macogw on 2010-03-26
When you login on the command line, are you:
A) using your username and password
B) using a recovery shell
??
 
Is it possible the installers for the updates used up remaining space on your hard drive?  If so, "sudo apt-cache clean"

---

### Post by bl77122 on 2010-03-26
> **macogw said:**
> When you login on the command line, are you:
A) using your username and password
B) using a recovery shell
??
 
Is it possible the installers for the updates used up remaining space on your hard drive?  If so, "sudo apt-cache clean"

Yes, I used username and password.
I am not sure if I used a recovery shell or not.
I just booted up 'recovery mode' which displays $ prompt.

Thank you for your help.

Bruce

---

### Post by amarjoshi88 on 2010-03-26
> **bl77122 said:**
> I am not sure what wubi is.
I can't log in gnome-failsafe either.

Thank you,

Bruce
I am facing the same problem as Bruce.... I can log in "gnome-failsafe" but not in Gnome
Help!!!!

---

### Post by achase79 on 2010-03-26
sounds like X is crashing upon login and brings it back to GDM

---

### Post by amarjoshi88 on 2010-03-29
so what can I do to fix it????

---

### Post by admiralspark on 2010-03-29
well, maybe this will work:

```
sudo apt-get uninstall xorg
sudo apt-get autoclean
sudo apt-get update
sudo apt-get install xorg
```If that doesn't work, you might just have to reinstall everything. :(

EDIT: try [this]("http://www.linuxforums.org/forum/debian-linux-help/41622-new-linux-ubuntu-install-gui-problem-2.html#post237760")

---

### Post by bl77122 on 2010-03-30
> **admiralspark said:**
> well, maybe this will work:

```
sudo apt-get uninstall xorg
sudo apt-get autoclean
sudo apt-get update
sudo apt-get install xorg
```If that doesn't work, you might just have to reinstall everything. :(

EDIT: try [this]("http://www.linuxforums.org/forum/debian-linux-help/41622-new-linux-ubuntu-install-gui-problem-2.html#post237760")

Hi,

I don't know what it will do, but I think I identified the cause of my problem.
Ubuntu fail to log in when I changed the display to lower (1280x1024) resolution.
When I log in command mode and run startx, I can log in Ubuntu.
If I change the resolution to the default, Ubuntu let me log in.

I appreciate if anyone knows how to get rid of this trivial annoyance?

Thanks,

Bruce

---

