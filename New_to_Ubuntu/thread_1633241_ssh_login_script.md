---
title: "ssh login script"
date: 2010-11-29
forum: New to Ubuntu
---

### Post by tdapower on 2010-11-29
[SIZE=3][COLOR=Red]please tell me the way how can i write a script to login to  a remote pc with ssh by integrating password inside the script?[/COLOR][/SIZE]

---

### Post by HermanAB on 2010-11-29
Howdy,

Short answer: You can't.

Long answer: Use Public Keys.  Generate a key pair on your local machine with ssh-keygen (Important: Press enter when asked for a passphrase) and copy the public key to the remote machine.

Read the Snail book for details: [http://www.snailbook.com/](http://www.snailbook.com/)

---

