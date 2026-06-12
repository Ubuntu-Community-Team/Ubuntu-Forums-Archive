---
title: "decryption problem"
date: 2009-11-13
forum: New to Ubuntu
---

### Post by ave2 on 2009-11-13
I created a key, encrypted a file, then exported the key- so I ended up with a .asc file

I then formatted my pc, installed ubuntu 9.10
in encryption, I imported my .asc file again
now I can encrypt files, but cannot decrypt them afterwards- I get the error:
Decryption failed. You probably do not have the decryption key.

does anyone know whats going on here?

---

### Post by Baelus on 2009-11-13
I'm not familiar with the ubuntu specific way of doing this, but from what I can tell, it's using a public/private key pair for encryption. Essentially this means that there are 2 keys. The data is encrypted by one key and it can then only be decrypted by the matching second key.

If this is what is happening in this situation, I'm afraid you won't be able to decrypt those files without the matching key.

---

### Post by delcypher on 2009-11-13
Are you using gpg?

If you are sounds like you've lost your private key but still have your public key. If that's the case you will never get your data back. When you export your key set you need to export your public key & private key!

To see if it is gpg you could run
```
gpg --list-keys
```

and

```
gpg --list-secret-keys
```

Of course if you're not using gpg then what I've posted isn't relevant.

---

### Post by Baelus on 2009-11-13
Ok. I had a look at the "Passwords and Encryption Keys" program under the Accessories menu (using 8.10 Intrepid). If that's what you're using then read on.

If you can see your key listed under the "My Personal Keys" tab, you should be fine.

If your key is found under the "Other Collected Keys" tab, then it looks like you're out of luck. :(

I also had a look at the export functions. All the menu items and buttons say "Export Public Key", which is fine. Public keys are used publicly.;)

The "Personal" keys are your private keys. The export option for this is not very visible. Usually this is a good thing as a private key shouldn't be accidentally exported and given away. Right click the relevant key under the "My Personal Keys" tab and select "Properties". Click on the "Details" tab. There you'll find the option to "Export Complete Key". That is what will get you your public AND private key as a .asc file.

When you import that .asc file it will appear under the "My Personal Keys" tab. That gets you encryption and decryption.

Importing a public key will fall under the "Other Collected Keys" tab. This allows only encryption.

---

