---
title: "GPG and googlemail"
date: 2009-04-22
forum: New to Ubuntu
---

### Post by frogchild on 2009-04-22
Hi,
I have opened a googlemail account which as far as I can see is default HTML - there are two versions to this standard HTML and basic HTML that's it. If anyone knows how to change this to plain text then this may help with my problem?

Anyway I am sending gpg'd email which go fine and can be decrypted by the recipient. However they are using PGP and any emails I get back I can not decrypt. I get an error message of 'you don't have the private key'. I have the public key of the recipient and I have never had this issue with other email providers or from with other people sending me PGP'd email so I am guessing it is the issue of HTML.

Does anyone have any ideas or pointers?:confused:

---

### Post by Penguin Guy on 2009-04-22
Your friend is using their key to encrypt messages, when **they should be using your key**.
[[IMG]http://ubuntuforums.org/attachment.php?attachmentid=110725&d=1240505076[/IMG]](http://en.wikipedia.org/wiki/Public-key_cryptography)

---

### Post by michy99 on 2009-04-22
Your friend should encrypt with your public key. You unencrypt with your private key.

---

### Post by michy99 on 2009-04-22
If the HTML is a problem, he should attach the message as a text file.

---

### Post by Penguin Guy on 2009-04-22
Sorry misread.

---

### Post by michy99 on 2009-04-22
ok

---

