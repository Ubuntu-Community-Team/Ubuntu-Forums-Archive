---
title: "login keyring"
date: 2010-07-30
forum: New to Ubuntu
---

### Post by retro-rocket on 2010-07-30
morning i,ve just bought a new pc changed the password etc but when i go to connect to the net it come,s up withlogin keyring different to my password,, how do i change the keyring password,
many thanks daz

---

### Post by anglican on 2010-07-30
> **retro-rocket said:**
> morning i,ve just bought a new pc changed the password etc but when i go to connect to the net it come,s up withlogin keyring different to my password,, how do i change the keyring password,
many thanks daz
```
sudo apt-get install seahorse
```then:
```

[LIST=1]
[*]Navigate to Applications > Accessories > Passwords and Encryption Keys
[*]Select the tab “Passwords”
[*]Select your keyring
[*]Right-click and attempt “Change Password” or, if that doesn’t work, select “Delete”
[/LIST]

```H

---

### Post by retro-rocket on 2010-07-30
were do you put the sudo code ??

---

### Post by beew on 2010-07-30
A simpler method. 

Go to System > Place. Click and navigate to /home/username. "username" is your user name.

Click on "view" and check "show hidden files". Then go to the folder .gnome2 and open it. In it you will find the folder "keyrings". Delete it. At this point you may want to reboot though you probably don't have to.

Next time when you try to connect to wireless the keyring manager will show up and prompt you for a new password. You can either set it to your login password, create a new one, or not put in anything and click ok. If you don't put in anything it will give you a warning about "use unsafe storage" or something like that. Just press ok and continue and it will never bother you again.  :)

I put in nothing as I think one password check is enough, sometimes these security things can get overboard and become very annoying, it is not like I am using my laptop for secret spy missions, I don't even use it for banking or purchases, for that the safest way would be to use a live CD or a live usb without persistence.

---

### Post by stoogiebuncho on 2010-07-30
> **retro-rocket said:**
> were do you put the sudo code ??

Actually, you don't need to put that code anywhere because seahorse is installed by default.  Look in your System > Administration menu and look for something called "Passwords and Keyrings" or something like that.  I don't remember the exact name.

Once there, you'll probably see a "default" keyring.  Right-click on it, and select "Change Password".



But FYI, when people give you code to execute on this forum, you execute it by going to Applications > Accessories > Terminal

---

### Post by beew on 2010-07-30
By the way, instead of doing all the navigating and point and clicking you can also remove the keyrings
folder by simply typing in the terminal 

> rm .gnome2/keyringsWith that I assume you start the terminal in your default directory (which is /home/username)

But it would probably be more reassuring to actually see what you are deleting. :)

You don't need sudo as you don't need to invoke root privilege to do whatever in your home directory.

---

