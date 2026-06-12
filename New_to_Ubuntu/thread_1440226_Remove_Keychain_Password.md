---
title: "Remove Keychain Password?"
date: 2010-03-27
forum: New to Ubuntu
---

### Post by listerdl on 2010-03-27
Hi does anyone know how to remove the keychain password that I am always prompted for?

Thanks

---

### Post by duanedesign on 2010-03-27
This will erase saved passwords you have so be sure you know or remember them before you make your computer forget them:

   1. Open up your Home Folder by clicking Places>Home Folder
   2. Press CTRL-H (or click View>Show Hidden Files)
   3. Find a folder called .gnome2 (it has a period at the beginning of the name) and open it by double clicking on it
   4. In side of the .gnome2 folder, there is another folder called keyrings.  Open it up.
   5. Delete any files you find within the keyrings folder
   6. Restart the computer

After restarting and logging in the next time you are prompted for a password, like your wireless, after entering the password the keyring manager will appear. Instead of typing in a new password, leave both boxes blank and click Create. You will get a dialog box warning you that you will now house passwords IN CLEAR TEXT and not in an encrypted form

[How to remove the Keyring password manager in Ubuntu Linux]("http://davestechsupport.com/blog/2009/01/16/how-to-remove-ubuntus-password-keyring/")

---

### Post by listerdl on 2010-03-27
id like to completely remove it! thanks

---

### Post by vedek on 2010-03-27
if it comes up when trying to connect to a wireless network then you need to right click the wireless icon select edit connections -> type in your password if it prompts you. select the connection that you need to edit, click edit then tick the available to all users and then that's you fixed.

---

