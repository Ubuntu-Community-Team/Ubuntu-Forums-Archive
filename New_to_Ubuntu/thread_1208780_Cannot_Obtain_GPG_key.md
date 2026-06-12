---
title: "Cannot Obtain GPG key"
date: 2009-07-09
forum: New to Ubuntu
---

### Post by guv999 on 2009-07-09
Hi
I want to obtain my GPG key fingerprint.   I am following the instructions outlined in Launchpad at [https://launchpad.net/~daveandclaire75/+editpgpkeys](https://launchpad.net/~daveandclaire75/+editpgpkeys)

When I enter the text at the command line the all I see is:
dave@dave-desktop:~$ gpg --fingerprint
dave@dave-desktop:~$ 

Not sure what I am doing wrong - any help greatly appreciated

---

### Post by Mornedhel on 2009-07-09
Well, you kind of need to have a key before you can get its fingerprint.

Try gpg --gen-key first. Use a serious-sounding user ID, since this key will pretty much be the ultimate way of identifying you on the Internet.

---

### Post by binbash on 2009-07-09
[http://www.ubuntu-inside.me/2009/02/howto-fix-signaturekeyserver-problems.html](http://www.ubuntu-inside.me/2009/02/howto-fix-signaturekeyserver-problems.html)

---

### Post by Mornedhel on 2009-07-09
> **binbash said:**
> [http://www.ubuntu-inside.me/2009/02/howto-fix-signaturekeyserver-problems.html](http://www.ubuntu-inside.me/2009/02/howto-fix-signaturekeyserver-problems.html)

This has *nothing* to do with the OP's issue. He wants to associate *his own* gpg key to his Launchpad account.

I appreciate that you're trying to help, but unfortunately, like too many one-sentence-helpers around here, you haven't really read the OP's question carefully.

---

### Post by guv999 on 2009-07-09
> **Mornedhel said:**
> Well, you kind of need to have a key before you can get its fingerprint.

Try gpg --gen-key first. Use a serious-sounding user ID, since this key will pretty much be the ultimate way of identifying you on the Internet.

Thanks for that - all sorted now

---

