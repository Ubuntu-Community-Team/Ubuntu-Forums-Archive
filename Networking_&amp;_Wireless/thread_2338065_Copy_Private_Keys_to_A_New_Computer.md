---
title: "Copy Private Keys to A New Computer"
date: 2016-09-24
forum: Networking &amp; Wireless
---

### Post by Jason_Hunter on 2016-09-24
When using passwordless ssh, I install a public key on a remote computer. 

I'm trying to understand why it doesn't work, when I copy the private key to a new computer. 

I know the proper way is simply to generate a new key pair, but I want to understand why it doesn't work.

---

### Post by SeijiSensei on 2016-09-24
I just copy the entire contents of ~/.ssh to a new machine.  You can't just copy the private key, you must copy both the private and public key.

---

### Post by Jason_Hunter on 2016-09-24
If I take a look in my public key, I see that the hostname is appended at the end; doesn't this mean that the hostname has to be the same when transferred?

---

### Post by SeijiSensei on 2016-09-24
No, it doesn't matter.  I've used the same keys on a number of boxes without matching hostnames.

---

