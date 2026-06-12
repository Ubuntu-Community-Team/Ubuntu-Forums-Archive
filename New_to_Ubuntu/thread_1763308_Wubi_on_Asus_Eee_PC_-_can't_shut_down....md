---
title: "Wubi on Asus Eee PC - can't shut down..."
date: 2011-05-20
forum: New to Ubuntu
---

### Post by 2CV67 on 2011-05-20
Using Wubi, I just installed Ubuntu 11.04 32-bit inside Windows Seven Starter OS on a new Asusu Eee PC 1015PED. (Unrelated to the Desktop in my signature)

It seems to function OK-ish, but it absolutely won't shut down on the button.
I have opened Ubuntu 9 times & had to switch off (hard shut down) 9 times.
Mostly I have tried the normal route - click on shutdown icon > select shutdown > confirm in next box - but this just results in a freeze with only wallpaper on the screen.
No pointer or cursor & no keyboard action (Esc - Enter - Ctrl/Alt/Del - Ctrl/Alt/Back - REISUB...)

I tried some other ways out:
1. Click on shutdown button > select Restart - this took me to a black screen with terminal-style text ending with "Checking for running inattended upgrades" but froze there.
2. From working desktop > Ctrl/Alt/Del > Select option shutdown - similar to above, but ending with "Checking for running unattended upgrades: init: plymouth-upstart-bridge main process (1683) terminated with status 1"

All this beats me, but it certainly is not "Just Works!"

Thanks for any help!

---

### Post by An Sanct on 2011-05-20
I know the frustration, but I see no reason to be angry ;)

try Ctrl + Alt + F1 (options are F1 to F7, where F7 gives you the GUI back)
log in with your username and password and execute this command
```

 sudo shutdown -h now
```Its self explanatory, it shuts down the machine asap.

edit: you can also run this command from any other terminal, since you log in as a soduer ...

---

### Post by mikechant on 2011-05-20
It may or may not be relevant in this case, but wubi installs do sometimes get odd problems that you don't get with 'proper' installs.

---

### Post by An Sanct on 2011-05-20
I would agree here, but have no experience with wubi installs. Live CD try-runs have some problems too, I would get the feeling, that wubi installs are "*the same*".

---

### Post by 2CV67 on 2011-05-20
> **An Sanct said:**
> I know the frustration, but I see no reason to be angry ;)
...execute this command
```
 sudo shutdown -h now
```Its self explanatory, it shuts down the machine asap....
Not angry - very sad.
After years of struggling with Ubuntu on my old XP desktop (see previous 500 posts) I was hoping & assuming that putting latest Ubuntu on a new netbook would be the proverbial piece of cake.

Another thread covers attempts to install Ubuntu "normally" alongside Windows, while Wubi was meant to be the no-problem method of trying out 11.04...

Thanks for the suggestion about ```
sudo shutdown -h now
```.
I tried that in a terminal, but that didn't work either.
Terminal said ```
Broadcast message from me@ubuntu (/dev/pts/0) at 19.50...
The system is going down for halt NOW!
me@ubuntu:~$
```
But the terminal (unusable) stayed on the screen with no activity for 10 minutes, so I switched off again = 10/10.

Any other ideas?

Thanks!

---

