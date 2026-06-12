---
title: "Importing encryption keys from file"
date: 2009-09-11
forum: New to Ubuntu
---

### Post by chris1950 on 2009-09-11
I installed UE 2.3 on another machine and want to import my keys. How do I Import them so that they go to the "My Personal Keys" tab and not the "Other Collected Keys" tab?

---

### Post by m_kelly on 2010-07-06
I believe the problem is not the import part of the process but the export. If you just right click on a key and select "Export", you export the "Public Key", which you can give away to other people. Since you presumably want your keys to encrypt and/or sign things, you need the "Private Key", which you *should not* give away to other people.

To export the private key, in the Passwords and Encryption Keys application, you have to right click on the key you want, select Properties, select the Details tab, and click the button to "Export Complete Key". When you import that key, it should show up under "My Personal Keys".

Once you have imported you key, you should probably delete the *KeyName*.asc file because if someone were to get that file, they could encrypt and/or sign things as if they were you.

---

