---
title: "stopping keyring"
date: 2009-01-18
forum: New to Ubuntu
---

### Post by wstay on 2009-01-18
I uninstalled keyring using the following instruction:
rm $HOME/.gnome2/keyrings/default.keyring
and I even remove the /home/wstay/.gnome2/keyrings folder. 

And I still have to key in my keyring password to access my evolution mail.
Is there a way to stop keyring from starting when the computer starts?

---

### Post by PurposeOfReason on 2009-01-18
That is not a keyring issue. You will always need your password to get your mail. To bypass that (not recommended) read this:
[http://ubuntu-tutorials.com/2007/07/12/automatically-unlocking-the-default-gnome-keyring-pam-keyring/](http://ubuntu-tutorials.com/2007/07/12/automatically-unlocking-the-default-gnome-keyring-pam-keyring/)

---

### Post by diablo75 on 2009-01-18
Don't just use that rm commmand.  Open up your Home Folder, hit CTRL-H and find the .gnome2/keyrings/ folder.  Sometimes there's more than one file in there.  You want the keyrings folder to be completely empty.

When the keyring prompt pops up again (asking you to CREATE A NEW DEFAULT KEYRING because the one you just deleted doesn't exist anymore) don't type in a password.  Leave it blank.  It will store your password again but never prompt you to type in a keyring password in the future because you didn't give it one to lock the keyring.

[http://davestechsupport.com/blog/2009/01/16/how-to-remove-ubuntus-password-keyring/](http://davestechsupport.com/blog/2009/01/16/how-to-remove-ubuntus-password-keyring/)

---

### Post by wstay on 2009-01-19
> **diablo75 said:**
> Don't just use that rm commmand.  Open up your Home Folder, hit CTRL-H and find the .gnome2/keyrings/ folder.  Sometimes there's more than one file in there.  You want the keyrings folder to be completely empty.

When the keyring prompt pops up again (asking you to CREATE A NEW DEFAULT KEYRING because the one you just deleted doesn't exist anymore) don't type in a password.  Leave it blank.  It will store your password again but never prompt you to type in a keyring password in the future because you didn't give it one to lock the keyring.

[http://davestechsupport.com/blog/2009/01/16/how-to-remove-ubuntus-password-keyring/](http://davestechsupport.com/blog/2009/01/16/how-to-remove-ubuntus-password-keyring/)

Thanks, it works and this problem solved.

---

