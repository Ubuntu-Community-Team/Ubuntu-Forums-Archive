---
title: "[SOLVED] Network Manager connect automatically without password?"
date: 2008-07-15
forum: Networking &amp; Wireless
---

### Post by stormtrooprdave on 2008-07-15
I have my profile set to auto login but every time it boots it asks for the admin password before it will connect to the internet.  How do I get it to to connect on start up without asking for the password?

---

### Post by stormtrooprdave on 2008-07-15
bump

I've looked all over these boards and tried all the solutions from various threads but nothing seems to work.

I've tried adding in common pam thing in the text file, deleted keyring folder files, set login and other passwords to the same, etc - nothing works.  Its extremely annoying having to type in the password everytime i boot up

---

### Post by tom957 on 2008-07-16
I have the same annoying problem. Does anyone have an idea?

---

### Post by tom957 on 2008-07-16
I just found this:

[http://ubuntuforums.org/showthread.php?t=320308&highlight=network+manager+keyring](http://ubuntuforums.org/showthread.php?t=320308&highlight=network+manager+keyring)

---

### Post by stormtrooprdave on 2008-07-16
> **tom957 said:**
> I just found this:

[http://ubuntuforums.org/showthread.php?t=320308&highlight=network+manager+keyring](http://ubuntuforums.org/showthread.php?t=320308&highlight=network+manager+keyring)
> **taqkavar said:**
> To get rid of the keyring prompt after automatic login in hardy 8.04 you can: 

System > Preferences > Encryption and Keyrings 
Under Password Keyrings click on "login Automatically unlocked when user logs in."
Click "Change Unlock Password"
Enter your old password, but leave the new password fields blank.
Ok , confirm and you should be set.

I confirm this works.  What are the security implications of this though?

---

### Post by darco on 2008-07-16
These forums need a better search tool....
This is from a previous post:

Just found a solution in this one: delete existing key, reboot & when keyring manager next time asks a new password for keyring just press OK without entering any password. It will ask if you're sure about it just click yes & after that your network should start automatically on startup.

good luck
darco

---

### Post by Oak37 on 2008-07-17
You might also consider giving [Wicd]("http://www.wicd.net/") a try. It allows automatic connection with automatic login.

---

### Post by darco on 2008-07-17
The solution above also works when I logged into Evolution.....

darco

---

### Post by cybrsaylr on 2008-07-19
Thanks, I was looking for that also.

---

