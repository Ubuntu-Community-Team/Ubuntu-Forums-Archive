---
title: "decrypt encryption for public key opengpg"
date: 2011-08-21
forum: New to Ubuntu
---

### Post by DarrenMR415 on 2011-08-21
I cannot get the email to decrypt.  I saved the text in gedit text editor and no matter what I do in the terminal it will not decrpyt.

Saved it as UnsavedDocument.

```
gpg: can't open `UnsavedDocument'
gpg: decrypt_message failed: file open error

```

Does it need to be saved someplace specific?


Doing it based off these directions

> As an alternate method you can read the message from the terminal. Copy and paste the message from "-----BEGIN PGP MESSAGE-----" till "-----END PGP MESSAGE-----" including those two lines in a text file. From the terminal run "gpg -d opgpm.txt" excluding the quotes where "opgpm" is the name you gave the text file. You will be asked to enter your passphrase and you get the decrypted message.

---

