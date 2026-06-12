---
title: "changing password wireless card"
date: 2009-09-28
forum: New to Ubuntu
---

### Post by Northwoods on 2009-09-28
Is there a way to change the root password. I have a Dell Inspiron 1200 and it connects to the internet through its wireless card. I can easily change both my root password and my user password BUT when I reboot I get a dialog telling me it is locked and to supply the password. To get the card to work I need to supply it with the password I used when installing Ubuntu. Is this a matter of changing the ower of the device? Do I have to reinstall grub with the new password? I am learning I don't know very much about passwords and users. Can anyone help me?

---

### Post by Darkwing-Duck on 2009-09-28
The password that you are having to type is for your Keyring password. Here is how to change that.
 
Go to “Passwords and Encription Keys”, then Edit->Preferences.
 
There you see a small list. Click on the login keyring and naturally “Change Unlock Password”.
 
Done.
 
Hopefully this works out for you.

---

### Post by Northwoods on 2009-09-28
> **Darkwing-Duck said:**
> The password that you are having to type is for your Keyring password. Here is how to change that.
 
Go to “Passwords and Encription Keys”, then Edit->Preferences.
 
There you see a small list. Click on the login keyring and naturally “Change Unlock Password”.
 
Done.
 
Hopefully this works out for you.

Thanks!!!! That seems to have done the trick.

---

