---
title: "What is the best way to have encrypted partition in ubuntu?"
date: 2009-05-05
forum: New to Ubuntu
---

### Post by legolas_w on 2009-05-05
Hi
Thank you for reading my post.
What is the best way to have an encrypted partition in ubuntu? I am using ubuntu 9.04 and want to have some documents hidden from possible intruders.

Thanks

---

### Post by hexanol on 2009-05-05
Well, if you only want **some** documents to be encrypted, you can use tools like [EncFS]("http://www.arg0.net/encfs") (or TrueCrypt). I personnaly use EncFS to hold some sensitives files.

There's also other solutions if you want to encrypt a complete file-system/partition or disk. But if you got everything already installed, I guess it would be simpler to use stuff like EncFS or TrueCrypt.

---

### Post by _sAm_ on 2009-05-05
Cryptkeeper is very easy to use if you only want a folder to be encrypted. You will find it in Synaptic.

---

### Post by DBrocks on 2009-05-05
I think you can encrypt an entire partition with TrueCrypt. But it involves re-formatting it though. TrueCrypt can also create a "vault" for storing files you wish to encrypt. Check it out.

---

### Post by nobodysbusiness on 2009-05-12
I recently wrote a blog tutorial about encrypting a Dropbox folder. You may not be interested in the Dropbox part, but if you cut out a few bits, it may give you what you need to set up EncFS without Dropbox. The tutorial is [available here]("http://pragmattica.wordpress.com/2009/05/10/encrypting-your-dropbox-seamlessly-and-automatically/").

---

