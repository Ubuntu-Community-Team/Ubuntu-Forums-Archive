---
title: "Fresh install on partitioned HD with Encrypted Home"
date: 2010-09-24
forum: New to Ubuntu
---

### Post by getut on 2010-09-24
Ok,

Way back I took the advice of old time linux users and got in the habit of manually partitioning my Ubuntu installations. A root partition, a home partition, and a swap partition.

It makes it very easy for me to do fresh installs instead of upgrades without touching my home folders.

Now introduce the encrypted home, which I finally did on my newest machine. When it comes time, how will I pair the new OS install to my encrypted home so nicely and neatly as when it did it this time.... ie no secondary password prompting with home automatically decrypting and becoming useable when I sign in?

---

### Post by getut on 2010-09-25
Does anyone have an answer for this.

I can find tons of articles about how to simply access it offline with a live cd but I would like to know how to get a fresh install to use a pre-existing encrypted home like would exist if you did a fresh install on a machine with 3 partitions, one for root, one for home and one for swap.

---

### Post by spiky001 on 2010-09-25
hi if you do the partition manuely you will be able to load make home your old home partition and just replace the os system

---

### Post by getut on 2010-09-28
Its that simple? I won't have to do anything special to get the new installation to automatically decrypt the home folders for the users stored on that partition again?

---

### Post by Paqman on 2010-09-28
You'll be fine as long as you know the mount password. And even if you don't, [you can recover it]("https://help.ubuntu.com/community/EncryptedPrivateDirectory#Recovering Your Mount Passphrase").

---

