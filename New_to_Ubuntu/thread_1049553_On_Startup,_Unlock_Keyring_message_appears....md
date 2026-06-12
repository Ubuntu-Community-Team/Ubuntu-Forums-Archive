---
title: "On Startup, Unlock Keyring message appears..."
date: 2009-01-24
forum: New to Ubuntu
---

### Post by looi76 on 2009-01-24
Hi, How can I stop "Unlock Keyring" message from appearing every time I switch on my computer?

[[IMG]http://img171.imageshack.us/img171/1756/unlockkeyringec0.th.png[/IMG]](http://img171.imageshack.us/my.php?image=unlockkeyringec0.png)

---

### Post by MockY on 2009-01-24
By throwing NetworkManager out. It is a horrible software and I suggest that you replace it with Wicd right away. You will be asked for a password every time it tries to connect to a protected network.Wicd does not.

[http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)

---

### Post by mister_pink on 2009-01-24
Or alternatively, the more simple method. Go to Applications, Accessories, Passwords and Encryption keys. Then go to edit preferences, and select the login line, then change unlock password. The old password will likely be whatever password you had when you originally installed ubuntu. To not get asked in future you can use a blank password, or the same as your current login password.

---

### Post by diablo75 on 2009-01-24
[LIST=1]
[*]Open up your Home Folder by clicking Places>Home Folder

[*]Press CTRL-H (or click View>Show Hidden Files)

[*]Find a folder called .gnome2 (it has a period at the beginning of the name) and open it by double clicking on it

[*]In side of the .gnome2 folder, there is another folder called keyrings.  Open it up.

[*]Delete any files you find within the keyrings folder

[*]Restart the computer
[/LIST]

After you restart and login (if you&#8217;re automatically logging in) you&#8217;ll probably be asked to enter your wireless networks WPA/WEP encryption key.  After you type that password in, the keyring manager will appear to let you know that it would like to handle the storage of that password and lock it away with a new keyring password.  The box looks like this:

[IMG]http://www.davestechsupport.com/blog/images/keyring1.png[/IMG]

Instead of typing in a new password, leave both boxes completely empty and click Create.

You&#8217;ll then be asked if you know what the hell you&#8217;re doing:

[IMG]http://www.davestechsupport.com/blog/images/keyring2.png[/IMG]

Go ahead and click Use Unsafe Storage.  From here on all passwords you enter into your computer will not safeguarded behind a master password.  Whether or not you want to do this is entirely up to you.  I personally have had enough of this keyring manager and consider it kind of annoying.  But as I said before, you may have certain environmental factors that make having a master password over the rest of your passwords a good idea.  Keep in mind that the keyring password manager has absolutely nothing to do with your administrative/root privilages password that has to be entered any time you want to apply updates, or add/remove software.  You will still have to type your account password in for these actions, and that is something I am quite comfortable with.  I&#8217;m just happy I don&#8217;t have to have to ask my girlfriend to type in a keyring password every time I want to restart the computer while I&#8217;m away from home.

(From my blog post here:  [http://davestechsupport.com/blog/2009/01/16/how-to-remove-ubuntus-password-keyring/](http://davestechsupport.com/blog/2009/01/16/how-to-remove-ubuntus-password-keyring/))

---

### Post by pvfjr on 2009-02-02
Thanks diablo, that was a big help for me too.  But what happened to the "thanks" feature, can't seem to find it.

---

### Post by Nepherte on 2009-02-03
It is disabled. There were a lot of database issues with it, slowing down the forum.

---

