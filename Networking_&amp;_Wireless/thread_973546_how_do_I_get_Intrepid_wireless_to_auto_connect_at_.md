---
title: "how do I get Intrepid wireless to auto connect at boot"
date: 2008-11-06
forum: Networking &amp; Wireless
---

### Post by charonred on 2008-11-06
Just setup a wubi install of Intrepid on a friends PC.

Wireless networking connects fine; but I have to enter the root password each time the system boots before the wireless will connect.

How do I get the wireless networking to auto connect at boot?

---

### Post by pytheas22 on 2008-11-06
What exactly do you mean when you say that you have to enter the root password to get the wireless to connect?  Do you mean that a box pops up when you log into the desktop asking for a password (probably it says something about 'unlocking the keyring')?  Or are you typing something at a command line?

Either way, you can probably get around it by simply [writing a boot script]("http://ubuntu.wordpress.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/").

---

### Post by charonred on 2008-11-06
Yep, that's it - 'unlocking the keyring' - which is something that annoyed me every time I started Evolution as well (which I no longer use)

Sorry, but couldn't make sense of that 'boot up script' blog; it assumes I already have written a script, which I haven't, and don't know how to.

I've setup a couple of 'Hardy' installs with wireless and they don't ask for a keyring, they just connect; as does my laptop running 'Hardy' (using KDE kwifi), it just connects as well.

just hoping for a 'sudo' type script to make network manager auto connect.

---

### Post by pytheas22 on 2008-11-06
It asks you for the password because it has the passphrase to your wireless network saved in the system 'keyring', and Network Manager needs to unlock the keyring in order to lookup your wireless password.  By default, the keyring should get unlocked when you log into Gnome, without you having to enter a password, but if something changed (like if you changed the user password), that might not be the case.

If you go to Applications>Accessories>Passwords and Encryption Keys and then go to Edit>Preferences, you can change the password for the keyring.  Make sure that the keyring password and the password for your friend's user account are the same.  Then reboot.  Does it still prompt you for the password?

Your other option is to write a boot script to connect to the wireless network when the machine boots, but that's probably not the best way to do things in this situation.

---

### Post by charonred on 2008-11-07
Haven't changed the password for the Ubuntu Gnome user account; I only installed it last night and each time I rebooted, it sought to unlock the 'keyring', at which point I typed in the user password, and it then connected to the wireless network with the appropriate stored passphrase.

The system is set to auto logon the user (and he's the only user), so he can switch on PC, go get a cuppa and come back to a 'ready for work' desktop.

---

### Post by pytheas22 on 2008-11-07
That's strange.  On all of my fresh installs, Network Manager never bothers me about the keyring password unless I change my user's password or something.  If you're using all default settings, I'm not sure why it's bothering your friend for this information.

I found [this thread]("http://ubuntuforums.org/showthread.php?t=192281") which may be helpful, although it's a bit dated.

Another option would be to use [wicd]("http://wicd.sourceforge.net") to connect instead of Network Manager.  I'm not positive but I think that if you used Gnome Sessions (System>Preferences>Sessions) to launch wicd when Gnome starts, it would auto-connect to any network for which it has the password and you check the auto-connect box.

---

### Post by charonred on 2008-11-07
ok, I'll check out all that when I get over his place next

---

### Post by abisdad on 2008-12-21
I had the same problem with Intrepid 8.10. It was because I had changed my user password, this does not change your keyring password. I found the answer [here]("http://ubuntuforums.org/showthread.php?t=863891&highlight=change+keyring+password").

Under Applications > Accessories > Passwords and encryption keys.

Hope that helps you.

---

### Post by pete25r on 2008-12-22
I found this thread on "disabling" the keyring...

[http://ubuntuforums.org/showthread.php?p=2776815#post2776815](http://ubuntuforums.org/showthread.php?p=2776815#post2776815)

---

