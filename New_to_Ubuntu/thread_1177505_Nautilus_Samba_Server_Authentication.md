---
title: "Nautilus Samba Server Authentication"
date: 2009-06-03
forum: New to Ubuntu
---

### Post by magicman5421 on 2009-06-03
Hey
So there's a server at my school that I want to connect to. I already connected once with a username and password, and saved it in my keyring. Now, I want to connect under a different username, but I told it to always allow nautilus to use the keyring. How do I reauthenticate?

---

### Post by billgoldberg on 2009-06-03
> **magicman5421 said:**
> Hey
So there's a server at my school that I want to connect to. I already connected once with a username and password, and saved it in my keyring. Now, I want to connect under a different username, but I told it to always allow nautilus to use the keyring. How do I reauthenticate?

System -> Preferences -> Encryption and Keyrings

?

Don't know, it's worth checking out.

---

### Post by magicman5421 on 2009-06-03
nope, checked all of those.
Applications>Accessories>Passwords and Encryption Keys
System>Preferences>Encryption and Keyrings
System>Administration>Authorizations

None of them have anything to do with samba authentication...

---

### Post by mcduck on 2009-06-04
> **magicman5421 said:**
> nope, checked all of those.
Applications>Accessories>Passwords and Encryption Keys
System>Preferences>Encryption and Keyrings
System>Administration>Authorizations

None of them have anything to do with samba authentication...

Yes, they do. The user name & password are stored in the keyring, and you can access/edit/remove them through Applications/Accessories/Passwords and Encryption Keys.

Just go to Passwords-tab, and click open the "passwords:login"-keyring. You'll find details for your Samba share there.

---

