---
title: "How to get into a partially-installed upgraded system"
date: 2009-07-20
forum: New to Ubuntu
---

### Post by natescape on 2009-07-20
Hi all,

I've been working on my dad's Dell Latitude that was running WinXP. I installed Ubuntu, got it functional, and set up his Evolution Mail to work with his Gmail account. Unfortunately, while Ubuntu was doing its upgrade, the system just completely turned off and now I can't log in.

I can input his username and password, and then the system just hangs. I might have simply blown away the install and redone the system, but Evolution pulled down all his email (including some he hadn't seen), so I don't want to lose it. 

Can I repair the install somehow or can I get the email off the system and then reinstall it?

The .xsession-errors file says it had the following error:
/etc/gdm/Xsession: 129: Cannot create /dev/null: Permission (for numbers 129, 130, and about a dozen 192s)
/etc/gdm/Xsession: Executing default failed, will try to run x-terminal-emulator
Failed to get the session bus: Failed to execute dbus-launch to autolaunch D-Bus session
Falling back to non-factory mode.
Failed to contact the GConf daemon; exiting.

I'm a Ubuntu newbie.

---

### Post by masux594 on 2009-07-20
have u try with auto repair the packages.. I have a laptop and it happen the same thing[when upgrading from 8.10 to 9.04].. I boot in recovery mode then, tried to repair broken packages and after an half of hour of cpu work, the system reboot with 8.04.. like a miracle =)

Sysc, A

---

### Post by natescape on 2009-07-20
I just tried that, and am still not able to log on. That being said, it used to hang, and now it's simply giving me the "Your session only lasted less than 10 seconds" error. I also noticed a failed message during the startup:

Starting periodic command scheduler crond [fail]

---

### Post by wojox on 2009-07-20
Put your LiveCD in and boot from cd drive first.

---

### Post by irv on 2009-07-20
You could boot with the live CD mount your installed filesystem, go to the home directory and show hidden files. Find .Evolution directory and copy it to a USB drive and at least you would have a backup of his mail and address'. If you have to re-install the system you could just copy this directory back to your home and he would not loose his mail.

---

### Post by ajgreeny on 2009-07-20
Just start again and reinstall if needed, and don't worry about loosing his email.  If it's all for a gmail account, it will all still be there in the mail server archives, as read mail, which you can quickly mark as unread if you use firefox to go to the gmail web address, rather than access it with evolution.

---

### Post by natescape on 2009-07-20
Thanks folks. That seemed to do it. 

Of course, now it won't connect to Gmail at all. Fun!

---

