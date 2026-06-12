---
title: "The Default Keyring Thingy"
date: 2009-12-16
forum: New to Ubuntu
---

### Post by Roger Allott on 2009-12-16
When I start Ubuntu, I get asked to type in my Default Keyring code so the prog can authorise me, I presume.

In jaunty, I replaced network-manager with wicd to get around the problem, but that strategy no longer works as UbuntuOne asks for the information instead.

Is there a simple way that I can tell network-manager and UbuntuOne and anything else that demands my Keyring code to fugg off and just go ahead and connect?

---

### Post by philinux on 2009-12-16
Navigate to ./gnome2/keyrings

Delete all files in there.

Now when asked for a keyring password leave it blank. You will get a warning but you wont be bothered again.

---

### Post by Roger Allott on 2009-12-17
> **philinux said:**
> Navigate to ./gnome2/keyrings

Delete all files in there.

Now when asked for a keyring password leave it blank. You will get a warning but you wont be bothered again.

It's taken three reboots to wash everything through, but it seems that was successful! Many thanks.

---

