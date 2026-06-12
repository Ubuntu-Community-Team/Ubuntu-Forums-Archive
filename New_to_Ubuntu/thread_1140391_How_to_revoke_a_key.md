---
title: "How to revoke a key"
date: 2009-04-27
forum: New to Ubuntu
---

### Post by yeehi on 2009-04-27
What can be done?

Two keys, A and B, were published on a key server. Passphrases have been forgotten.

A still has the A.asc, revoke.asc and the sec_key.asc
B only has the B.asc.

Can I get them going again somehow?

---

### Post by unutbu on 2009-04-27
From [http://www.nmlug.org/faqs/gen-gpg-key.html:](http://www.nmlug.org/faqs/gen-gpg-key.html:)

> Be aware that once you upload your key to a public keyserver, there is no way for you to remove it. At most, you can send the keyserver a [revocation] certificate to state that you no longer are in control of this key. So, don't upload a key to a keyserver until you are sure that you completely satisified with your new key.

For the key with a revocation certificate:
> 
In the unfortunate event that you loose your private key, forget your passphrase to access youor private key, or that someone else gains access to your private key, you should have a revocation certificate. This certificate can be sent to the public key servers so inform other GPG users that you no longer trust your key.

For how to send it to the keyserver:
See also [http://lists.gnupg.org/pipermail/gnupg-users/2001-September/010160.html](http://lists.gnupg.org/pipermail/gnupg-users/2001-September/010160.html)

---

