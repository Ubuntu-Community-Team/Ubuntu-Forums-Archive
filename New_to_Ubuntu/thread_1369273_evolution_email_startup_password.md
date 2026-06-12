---
title: "evolution email startup password"
date: 2009-12-31
forum: New to Ubuntu
---

### Post by Matt26 on 2009-12-31
when the evolution email client starts up it prompts me for a password- is there a way to set this password so that i'm not prompted for it each time evolution starts?

---

### Post by duanedesign on 2010-01-04
If  you have auto-login enabled Evoloution will prompt you for a password as a security feature. You can turn auto-login off (System > Administration > LogIn Screen). Then at boot up you will be asked your password thus unlocking the keyring.

[Here]("http://davestechsupport.com/blog/2009/01/16/how-to-remove-ubuntus-password-keyring/") is an alternate work around

---

### Post by mcduck on 2010-01-04
> **duanedesign said:**
> If  you have auto-login enabled Evoloution will prompt you for a password as a security feature. You can turn auto-login off (System > Administration > LogIn Screen). Then at boot up you will be asked your password thus unlocking the keyring.

[Here]("http://davestechsupport.com/blog/2009/01/16/how-to-remove-ubuntus-password-keyring/") is an alternate work around

Otherwise true, but the workaround you posted is quite a nasty one (since it deletes all keys stored in the keyring!).

The keyring password can be changed (or removed) with the Seahorse, found in Applications/Accessories/Passwords and Encryption Keys. Just right-click on the "Passwords:login"-keyring in the passwords-tab and select "Change Password". Doing it this way doesn't destroy any data stored in the keyring.

---

### Post by DZ* on 2010-01-04
> **duanedesign said:**
>  Here is an alternate work around
([http://davestechsupport.com/blog/2009/01/16/how-to-remove-ubuntus-password-keyring/](http://davestechsupport.com/blog/2009/01/16/how-to-remove-ubuntus-password-keyring/))

Deleting ~/.gnome2/keyrings/* is an overkill. It erases all stored passwords. There is a non-destructive way:

type seahorse from a terminal, right-click on "Passwords: login", type in the old password and leave out the (new) password entry empty. After that, passwords will be stored in ~/.gnome2/keyrings/ in plain text.

---

