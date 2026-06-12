---
title: "Change/disable keyring password in 10.10"
date: 2010-11-07
forum: New to Ubuntu
---

### Post by demonboy on 2010-11-07
My apologies for bringing up a subject that looks well documented on the forums but this relates to a later version of Ubuntu and the solutions I've read seem to relate to earlier versions.

I've done a complete install of Ubuntu Desktop 10.10 on my father's Samsung N140. I've allocated him a password that pops up at login and in the usual places when installing new apps. HOwever I am also being asked for the default keyring password to access the wifi network. I didn't assign a default keyring password and I don't know how to disable it.

I've tried following one solution that involved going to Passwords and Encryption Keys but I was told to use the one under Applications and NOT under System. I can only see the one under system.


Does anyone know if there is a standard password for default keyring? I don't think I want to disable it, I just want to use the same password as login.

Apologies for asking an old question!

---

### Post by kingcharles1666 on 2010-11-07
The fix is to change the password for login in seahorse:

To change the login password in seahorse press alt-F2 and type in: seahorse
Go to the Passwords tab (the left tab)
Right-click on Passwords: login
Select change password
Type in your old login password, then enter the new login password twice.

This should sync the passwords and solve your problem. If you only want to synchronize then use the same password for old and new

You need to do this also if a user changes his/her login password in the "about me" option of the admin menu.

---

### Post by demonboy on 2010-11-07
Thank you for your reply. I haven't logged off yet as I'm in the middle of an install but I'll check to see if they have synchronised when I next log on. Cheers.

---

### Post by demonboy on 2010-11-07
Quick update:

I tried the solution suggested by kingcharles but to no avail. I therefore just ended up deleting the keyring altogether, which is not ideal but the only solution I could come across. I followed this solution by komputes:

[http://ubuntuforums.org/showthread.php?p=4377271](http://ubuntuforums.org/showthread.php?p=4377271)

---

### Post by xpensv on 2010-12-10
I tried kingcharles1666 Suggestion and it worked for me.  

Thanks

---

### Post by germanix on 2010-12-10
I had a similar problem with Ubuntu 9.04 and did the following: I got rid of the keyring manager. (hey, it is my system and I can do with it what I like;)* 
Please note this will erase saved passwords you have so be sure you know or remember them before you make your computer forget them:
Open up your Home Folder by clicking Places>Home Folder
Press CTRL-H (or click View>Show Hidden Files)
Find a folder called .gnome2 (it has a period at the beginning of the name) and open it by double clicking on it
In side of the .gnome2 folder, there is another folder called keyrings.* Open it up.
Delete any files you find within the keyrings folder
Restart the computer
After you restart and login (or if you’re automatically logging in) you’ll probably be asked to enter your wireless networks WPA/WEP encryption key.* After you type that password in, the keyring manager will appear to let you know that it would like to handle the storage of that password and lock it away with a new keyring password.*
&#65532;
Instead of typing in a new password, leave both boxes completely empty and click Create.
You’ll then be asked if you know what the hell you’re doing:
&#65532;
Go ahead and click Use Unsafe Storage.
WARNING: Doing this creates a new file in your ~/.gnome2/keyrings/ folder called default.keyring and it will now house passwords IN CLEAR TEXT and not in an encrypted form. *So it is imperative that you are certain no untrustworthy persons can access your user account (either physically or by remote) or they will be able to easily open and read this file and obtain many passwords (for things such as FTP accounts, SSH, e-mail accounts, etc). *Proceed with caution.
From here on all keyring stored passwords you enter will not be safeguarded behind a master password or encryption.* Whether or not you want to do this is entirely up to you.* But you may have certain environmental factors that make having a master password over the rest of your passwords a good idea.* Keep in mind that the keyring password manager has absolutely nothing to do with your administrative/root privilages password that has to be entered any time you want to apply updates, or add/remove software.* You will still have to type your account password in for these actions.

---

### Post by beew on 2010-12-10
> **germanix said:**
> I had a similar problem with Ubuntu 9.04 and did the following: I got rid of the keyring manager. (hey, it is my system and I can do with it what I like;)* 
Please note this will erase saved passwords you have so be sure you know or remember them before you make your computer forget them:
Open up your Home Folder by clicking Places>Home Folder
Press CTRL-H (or click View>Show Hidden Files)
Find a folder called .gnome2 (it has a period at the beginning of the name) and open it by double clicking on it
In side of the .gnome2 folder, there is another folder called keyrings.* Open it up.
Delete any files you find within the keyrings folder
Restart the computer
After you restart and login (or if you’re automatically logging in) you’ll probably be asked to enter your wireless networks WPA/WEP encryption key.* After you type that password in, the keyring manager will appear to let you know that it would like to handle the storage of that password and lock it away with a new keyring password.*
&#65532;
Instead of typing in a new password, leave both boxes completely empty and click Create.
You’ll then be asked if you know what the hell you’re doing:
&#65532;
Go ahead and click Use Unsafe Storage.
WARNING: Doing this creates a new file in your ~/.gnome2/keyrings/ folder called default.keyring and it will now house passwords IN CLEAR TEXT and not in an encrypted form. *So it is imperative that you are certain no untrustworthy persons can access your user account (either physically or by remote) or they will be able to easily open and read this file and obtain many passwords (for things such as FTP accounts, SSH, e-mail accounts, etc). *Proceed with caution.
From here on all keyring stored passwords you enter will not be safeguarded behind a master password or encryption.* Whether or not you want to do this is entirely up to you.* But you may have certain environmental factors that make having a master password over the rest of your passwords a good idea.* Keep in mind that the keyring password manager has absolutely nothing to do with your administrative/root privilages password that has to be entered any time you want to apply updates, or add/remove software.* You will still have to type your account password in for these actions.

This was basically what I did. Except two things. 1) You can simply delete the whole keyrings folder in gconf.2 2) There is no need to restart.

---

### Post by mal205 on 2011-01-25
> **kingcharles1666 said:**
> The fix is to change the password for login in seahorse:

To change the login password in seahorse press alt-F2 and type in: seahorse
Go to the Passwords tab (the left tab)
Right-click on Passwords: login
Select change password
Type in your old login password, then enter the new login password twice.

This should sync the passwords and solve your problem. If you only want to synchronize then use the same password for old and new

You need to do this also if a user changes his/her login password in the "about me" option of the admin menu.

Perfect! Thanks

---

### Post by Dlambert on 2011-03-17
> **kingcharles1666 said:**
> The fix is to change the password for login in seahorse:

To change the login password in seahorse press alt-F2 and type in: seahorse
Go to the Passwords tab (the left tab)
Right-click on Passwords: login
Select change password
Type in your old login password, then enter the new login password twice.

This should sync the passwords and solve your problem. If you only want to synchronize then use the same password for old and new

You need to do this also if a user changes his/her login password in the "about me" option of the admin menu.

Thanks

---

