---
title: "Logging in Without Password"
date: 2010-12-17
forum: New to Ubuntu
---

### Post by CBR_Rob on 2010-12-17
I want to set up my wifes netbook to automatically log in without a password. I've got it to automatically log in but I still have to enter the keyring password (same as login) in order to connect to the wireless network. Any way to get around this?

---

### Post by NertSkull on 2010-12-17
I've never used the keyring manager stuff because I do it differently.

But if it has a command line, you could just set up a simple script to pass the password to it.  Then add the script to the startup applications.

That way everytime she logs in, it runs the script and passes the password and all is well.  

Also, I believe (but could be wrong because I don't use it) that you should be able to set up the wireless network to connect without a password.  It may be something to do with permissions.  Sorry I can't help more on that, I still connect with a cable.

---

### Post by sean.ferguson on 2010-12-17
I never use the keyring for the wireless connection on my eepc 701. When you connect to the wireless network for the first time and it asks you to enter a keyring password, just hit enter (blank password) then it will connect everytime without prompting for input.

Now to remove the keyring for the wireless i think if you go to System>Preferences>Passwords & Encryption Keys you should be able to delete the keyring for the wireless :)

---

### Post by cariboo on 2010-12-17
Just create a blank password for the keyring. Right click on passwords in the in the Passwords and Encryption Keys window and select Change Password, entry your current password and leave the rest blank.

---

### Post by cogier on 2010-12-17
Right click on the wireless icon and select **Edit connections**. Click on the **Wireless** tab. Select your wireless Name and click on **Edit**. Then mark the box **Available to all users**.

That should do it.

---

### Post by CBR_Rob on 2010-12-18
> **cariboo907 said:**
> Just create a blank password for the keyring. Right click on passwords in the in the Passwords and Encryption Keys window and select Change Password, entry your current password and leave the rest blank.
I stumbled across that just before reading this. Thanks for all the help.

---

