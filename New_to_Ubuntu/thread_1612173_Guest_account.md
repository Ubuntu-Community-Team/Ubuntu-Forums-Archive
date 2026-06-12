---
title: "Guest account?"
date: 2010-11-02
forum: New to Ubuntu
---

### Post by servicetech on 2010-11-02
What is an easy way for people w/o a user account to use the computer? Say for instance my PC is off and somebody wants to go online w/o logging into a specific account...

---

### Post by cboxhero on 2010-11-02
Well, on 10.10 there is an option on the log-in screen for "other". It asks you for a user-name, so I think that is how someone could get in easily.

---

### Post by Frogs Hair on 2010-11-02
You could create a guest account and set it to log in automatically in login settings ; however, the user would have to select guest from the login box when the computer boots.

---

### Post by Old_Grey_Wolf on 2010-11-02
You can go to the menu System > Administration > Users and Groups to create an account. You will need to click the Add button, then enter your password. Then you can enter a Name for the new user -- note that you can change the Name later. You will get a window for setting the new user's password. Check the box next to "Don't ask for password on login", and click OK. With the new user selected, click the Advanced Settings button, then the User Privileges tab, then select the privileges you want a guest to have. Some things like Admin are disabled by default for you.

The person will still need to know to select the user name.

---

### Post by trikster_x on 2010-11-02
> **Old_Gray_Wolf said:**
> You can go to the menu System > Administration > Users and Groups to create an account. You will need to click the Add button, then enter your password. Then you can enter a Name for the new user -- note that you can change the Name later. You will get a window for setting the new user's password. Check the box next to "Don't ask for password on login", and click OK. With the new user selected, click the Advanced Settings button, then the User Privileges tab, then select the privileges you want a guest to have. Some things like Admin are disabled by default for you.

The person will still need to know to select the user name.

An alternative to making them go through the motions of actually finding the right account, you can set the comp to automatically log-in a specific user after a predetermined amount of time.  Simply open system>>administration>>login screen (assuming of course you are using 10.04+).

---

### Post by servicetech on 2010-11-03
I'm running 10.10. I tried the "other" option but it asks for a username. I tried random names and it doesn't work.

I ended up creating another account, however it requires a password at login to unlock the default keyring.

---

### Post by migs73 on 2010-11-03
Change the background of the login screen to include instructions/password for the guest to login.

---

### Post by Old_Grey_Wolf on 2010-11-03
> **servicetech said:**
> I'm running 10.10. I tried the "other" option but it asks for a username. I tried random names and it doesn't work.

I ended up creating another account, however it requires a password at login to unlock the default keyring.

Removing the password to unlock the keyring means that your keys and passwords are stored unencrypted.

You can remove the password by going to the new user account you created, then:
1) Going to menu Applications > Accessories > Passwords and Encryption Keys
2) Select the Passwords tab
3) Right click the entry that has the word "login" in the name
4) Select Change Password
5) Enter the Old Password and leave the Password: and Confirm: field blank
6) You will get a Warning message about storing unencrypted passwords.
7) If you are **really sure** you want to do this then click the Use Unsafe Storage button.

---

