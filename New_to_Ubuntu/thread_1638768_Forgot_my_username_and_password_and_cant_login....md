---
title: "Forgot my username and password and cant login..."
date: 2010-12-06
forum: New to Ubuntu
---

### Post by deversole88 on 2010-12-06
I forgot my username and password so like an idiot not knowing anything   about computer when into the BIOS setup utility and set a supervisor   password and a HDD password thinking it was the same password needed to   access my computer. Now when I restart my computer it asks for my HDD   password, once entered in take me to a command screen that says   "grub>" ... How can I fix this so that I can use my computer normally   or just get it to load to the username and password screen??? Sorry to  have to ask...

---

### Post by karthick87 on 2010-12-06
Boot using a live CD and post the results of [COLOR=DarkOrange][bootscript]("http://bootinfoscript.sourceforge.net/")[/COLOR]

---

### Post by Born-Thirsty on 2010-12-06
To get rid of the BIOS settings you added, one could always just remove the BIOS battery, wait a minute or two and then replace it. Usually resets it back to default settings, and then you can check whether or not it starts up to the login screen again.

For the problem with the remembering of usernames and passwords... there is an option in which you can boot to root login by defualt. Not entirely sure of what the command is, but you need to edit the grub menu login and add something about "init=/bin/bash" or such... Will try find it for you if you need it.

---

### Post by stoogiebuncho on 2010-12-06
Fixing this problem will be a three part process:

1.
You'll have to get your bios settings and grub figured out first.

First, go back into your bios settings and change them back to the way they were (remove the password, etc).

2.
If the settings are back to normal and you still can't boot, you'll have to reinstall grub (this is easy).  Follow these instructions:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

3. 
Now you should be able to boot to your login screen.  But you still don't know your password, right?  Follow these instructions to reset your password:
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)


Post here if you have questions or need additional help.

---

### Post by pricetech on 2010-12-06
Undo the changes you made in the BIOS first, then proceed according to the articles pointed to above.

---

### Post by I'mGeorge on 2010-12-06
> **Born-Thirsty said:**
> To get rid of the BIOS settings you added, one could always just remove the BIOS battery, wait a minute or two and then replace it. Usually resets it back to default settings, and then you can check whether or not it starts up to the login screen again.

If you have to reset BIOS the proper way to do it it's this [http://www.wikihow.com/Reset-Your-BIOS](http://www.wikihow.com/Reset-Your-BIOS)

---

