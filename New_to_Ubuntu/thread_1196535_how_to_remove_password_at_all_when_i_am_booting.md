---
title: "how to remove password at all when i am booting?"
date: 2009-06-25
forum: New to Ubuntu
---

### Post by SKYDOS on 2009-06-25
i need ubuntu to boot without requaring a password and username
is this possible?

---

### Post by mltucker on 2009-06-25
Yes.  It is the Automatic Login option.  Look in System->Administration->Login Window, in the Security tab.

---

### Post by mltucker on 2009-06-25
Keep in mind, though, that once it logs in, you will have to enter your keychain password if you want to access wireless networks.

---

### Post by kansasnoob on 2009-06-25
Yes. Go to System > Admistration > Login Window, then click on the Security tab and tick Enable Auto Login and be sure to select your user name from User list.

---

### Post by Sub101 on 2009-06-25
> **mltucker said:**
> Keep in mind, though, that once it logs in, you will have to enter your keychain password if you want to access wireless networks.

Unless you change the keychain password to empty. You can do this in Apps ==> Accessories ==> Passwords and Encryption then the passwords tab.

---

### Post by ad_267 on 2009-06-25
Just note that this doesn't unlock the default keyring, so applications like Evolution that encrypt your email passwords using the keyring will have to ask for your password to unlock it.

Edit: Wow I was slow, 3 posts got in before me...

---

### Post by mltucker on 2009-06-25
But if you leave your keychain password blank, then all of your network credentials and whatnot will be stored in plain text.

---

### Post by jimv on 2009-06-25
> **mltucker said:**
> But if you leave your keychain password blank, then all of your network credentials and whatnot will be stored in plain text.

I'm pretty sure he's not too worried about that if it's auto-logging in.

---

### Post by SKYDOS on 2009-06-25
thanks!!
it worked! perfect!

---

