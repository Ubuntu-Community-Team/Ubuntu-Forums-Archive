---
title: "Enter password to unlock keyring - how to get rid of it?"
date: 2010-05-20
forum: New to Ubuntu
---

### Post by const451 on 2010-05-20
Even I choose to login automatically every time I reboot I have to enter password anyways because I have this dialog box coming up: "Enter password to unlock keyring"...

How do I get rid of this?

Thank you!

---

### Post by ubunterooster on 2010-05-20
> **const451 said:**
> Even I choose to login automatically every time I reboot I have to enter password anyways because I have this dialog box coming up: "Enter password to unlock keyring"...

How do I get rid of this?

Thank you!
+1

I have been trying to do this a long time and have been subscribed to 18 threads on this which were not answered

---

### Post by bilodeau on 2010-05-22
Howdy,  
Try this link for auto-unlocking the keyring-manager.

[http://maketecheasier.com/auto-unlock-keyring-manager-in-ubuntu-intrepid/2009/03/14](http://maketecheasier.com/auto-unlock-keyring-manager-in-ubuntu-intrepid/2009/03/14)

I realize that it is for Intrepid, but it might be worthwhile.

---

### Post by const451 on 2010-05-24
Thank you, but it's different in Lucid, and I do not want to play with those passwords b/c I am afraid I will not be able to login then - I am new to Linux.

---

### Post by Chesamo on 2010-05-24
What do you have that uses the keyring?

---

### Post by gandaran on 2010-05-24
> **const451 said:**
> Even I choose to login automatically every time I reboot I have to enter password anyways because I have this dialog box coming up: "Enter password to unlock keyring"...

How do I get rid of this?

Thank you!
you will have to find the keyring configuration files in your hidden home user directory (/home/user/.gnome2/keyring, I think) and delete them, then the next time the keyring asks you to set a password don't enter/type anything, just proceed without a password and accept to use the unsecured option, after this it won't ask you again for passwords.

---

### Post by mk1w86 on 2010-05-24
Try this:

Go to Applications >> Accessories >> Passwords and Encryption Keys and make sure the Passwords tab is selected.   Then right click the Passwords: login entry and select Change Password, enter your current password, leave the new password boxes blank and confirm that you wan't to use unsafe storage. ;)

This worked for me anyway on Lucid because it kept asking for a password to connect to the wireless network.

---

### Post by pr0t3g3 on 2010-05-24
> **mk1w86 said:**
> Try this:

Go to Applications >> Accessories >> Passwords and Encryption Keys and make sure the Passwords tab is selected.   Then right click the Passwords: login entry and select Change Password, enter your current password, leave the new password boxes blank and confirm that you wan't to use unsafe storage. ;)

This worked for me anyway on Lucid because it kept asking for a password to connect to the wireless network.
I don't know why you'd *want *to.  If nothing else that password prompt should act as extra security, in a public environment. Don't be annoyed, be grateful.

---

### Post by bkratz on 2010-05-24
> **pr0t3g3 said:**
> I don't know why you'd *want *to.  If nothing else that password prompt should act as extra security, in a public environment. Don't be annoyed, be grateful.



Some of us are sitting at our desk at home with no others even around: it is a pain. If I was using a laptop I would be grateful for the extra security, but I have ultimate security (only user), hence the keyring is an annoyance.

---

### Post by mk1w86 on 2010-05-24
> **pr0t3g3 said:**
> I don't know why you'd *want *to.  If nothing else that password prompt should act as extra security, in a public environment. Don't be annoyed, be grateful.

First, the machines are not in a public environment (for me, I don't know about the OP) and secondly, what is the point of using auto-login if you are still asked for a password.  If I wanted the extra security I would login normally. :confused:

---

### Post by chiefster on 2010-05-24
in the edit connections box select your wireless connection and tick the box "available to all users".  Worked like a charm for me, no more keyring prompts

---

### Post by const451 on 2010-05-25
> **chiefster said:**
> in the edit connections box select your wireless connection and tick the box "available to all users".  Worked like a charm for me, no more keyring prompts


That worked!! I thought this was the easiest way and it worked! -- Thank  you!

Do you know what exactly does that mean "available to all users"?

I am the only user of my laptop but I do not want my wireless to be  available to all my neighbors. 

THX

---

### Post by k3lt01 on 2010-05-25
This dialogue box started on my laptop after I signed up for an Ubuntu One account. If I don't sign I assume I can't use the account, if I do sign I assume I can use the account. I only have this occurring on 1 machine, I have many machines, and it is the only one with Ubuntu One access.

The moral to this is make sure you know what is on your own machine. Asking to get rid of something may inhibit your usage of something if you do actually get rid of it.

---

### Post by mk1w86 on 2010-05-25
> **const451 said:**
> That worked!! I thought this was the easiest way and it worked! -- Thank  you!

Do you know what exactly does that mean "available to all users"?

I am the only user of my laptop but I do not want my wireless to be  available to all my neighbors. 

THX

There is also a root user on your system although by default on Ubuntu you can't log in to it, you use sudo to give your own account temporary root privileges.  You had to enter a password because by default you need root privileges to connect to a wireless network.  Being available to all users means your own account can also use wireless as well as any other user accounts on your system.

As long as your wireless network is encrypted (ideally with WPA2) nobody can connect to your wireless unless they have the encryption key.

Basically, you are allowing your account to access the wireless hardware on your machine itself NOT connecting to your wireless network which is what the encryption key is for. ;)

By the way if you are interested, the idea of a keyring is to aggregate many passwords so you only have to enter one to unlock them all.

Hope this helps. :)

---

### Post by elendilnl on 2010-05-26
> **mk1w86 said:**
> Try this:

Go to Applications >> Accessories >> Passwords and Encryption Keys and make sure the Passwords tab is selected.   Then right click the Passwords: login entry and select Change Password, enter your current password, leave the new password boxes blank and confirm that you wan't to use unsafe storage. ;)
This solved my problem by changing it for the **Default** password

---

### Post by const451 on 2010-05-26
> **mk1w86 said:**
> There is also a root user on your system although by default on Ubuntu you can't log in to it, you use sudo to give your own account temporary root privileges.  You had to enter a password because by default you need root privileges to connect to a wireless network.  Being available to all users means your own account can also use wireless as well as any other user accounts on your system.

As long as your wireless network is encrypted (ideally with WPA2) nobody can connect to your wireless unless they have the encryption key.

Basically, you are allowing your account to access the wireless hardware on your machine itself NOT connecting to your wireless network which is what the encryption key is for. ;)

By the way if you are interested, the idea of a keyring is to aggregate many passwords so you only have to enter one to unlock them all.

Hope this helps. :)

I see, thank you. Trying to fix this I read that keyring is something like password manager on FireFox.

---

### Post by leorolla on 2010-06-29
Please, before you do this to your computer, read this:

[http://ubuntuforums.org/showthread.php?p=9525569](http://ubuntuforums.org/showthread.php?p=9525569)

---

### Post by km0r3 on 2010-07-09
> **gandaran said:**
> you will have to find the keyring configuration files in your hidden home user directory (/home/user/.gnome2/keyring, I think) and delete them, then the next time the keyring asks you to set a password don't enter/type anything, just proceed without a password and accept to use the unsecured option, after this it won't ask you again for passwords.

It is the folder /home/<user>/.gnome2/keyrings/ where the login keyring is stored.

I have just opened a terminal, cd into the folder mentioned above and typed:

```
rm *
```


This solved the issue for me.

---

