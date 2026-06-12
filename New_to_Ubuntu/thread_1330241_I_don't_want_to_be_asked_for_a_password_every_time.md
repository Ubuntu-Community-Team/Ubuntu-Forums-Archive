---
title: "I don't want to be asked for a password every time I connect to my wireless network!"
date: 2009-11-18
forum: New to Ubuntu
---

### Post by ovimunt on 2009-11-18
Hi,


When I installed Ubuntu I chose the automatic log on as I hate being asked for my password a million times since I'm the only user of my computer. 

But as a result, my wireless access key has been storred in that Password Wallet (or how exactly it's called) and every time I start my computer I get asked for the wallet password before I can connect to my wireless network. 

Now I understand that Linux is supposed to be more secure than Windows and all but this is ridiculous, I don't want to have to enter my password every time I swich on my computer, I don't want to enter my password every time I connect to my wireless network, and I don't want to be asked for my password every time I want to mount my NTFS partitions! 

So, is there any way to disable these excessive and paranoid safety settings?

Thanks

---

### Post by philinux on 2009-11-18
I would re-enable the login before doing this.

Places>home folder.

Press ctrl h to show the hidden config folders.

Navigate to the folder .gnome then keyrings. Edit select all and delete the contents. Now when you get asked for you wireless password the keyring app will ask you to store a password. Leave it blank and press enter.

---

### Post by kimda on 2009-11-18
You can add the ntfs partitions to fstab so that they get mounted at startup..

Here's an guide how to do this. 
[http://ubuntuforums.org/showthread.php?t=1330232](http://ubuntuforums.org/showthread.php?t=1330232)

About your wireless key - do you mean the passphrase to secure your wifi connection? You can store the passphrase in the network manager. Rightclick icon with the two computers and select "edit connections" Select wireless tab and edit your connection. Add the passphrase to the password field in the security tab.

---

### Post by winotree on 2009-11-18
EDIT - [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)  may be an option for you and anyone else with a desire to bypass your wireless password.  I fully understand the security implications but someone could easily slip my device into their pocket and a password won't help me then!  :D

---

### Post by ovimunt on 2009-11-18
Thanks for your answers, I'll try them out as soon as I get home.

On the other hand, maybe for some people it wasn't particularly clear what I meant: I'm not trying to bypass my WiFi key; instead, what I meant was that I wanted to bypass the Ubuntu Keyring password.

In any case, I also found [this little Blog]("http://pherricoxide.wordpress.com/2009/02/22/ubuntu-keyring-password-change/") which gives the same solution as someone else has already mentioned in this thread.

---

