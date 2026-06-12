---
title: "Grubs secondary hdd install including windows 7"
date: 2011-01-06
forum: New to Ubuntu
---

### Post by jinba.ittai on 2011-01-06
Im running a 2 hdd setup, and today my main hdd failed (not sure whats wrong with it). I have windows 7 on the main 750gb hdd and 10.10 on the secondary 350 hdd, but in order to get my pc operational again i had to install a second boot of 10.10 next to the current one on the 350gb hdd to get grub to boot up.

Now i am trying to figure out how to get rid of the second install of ubuntu, remove the entry from grub and add an entry for windows 7 on a new hdd i put in. I know if i install windows 7 on the new hdd it will overwrite the grrub, so how do i go about installing windows 7 and getting grub to still boot from the secondary hdd?

---

### Post by LewRockwellFAN on 2011-01-07
You'll probably get a better and more elegant answer from somebody who really understands grub well but if not, or if you don't want to wait, here is an easy one. Install the W-7. Then, making sure any data you've stored on the Ubuntu partition is secure somewhere else (like maybe copy it to a data partition on the new drive) re-install Ubuntu over the old installation. It doesn't take ALL that long. Then the Grub menu should see both.

---

