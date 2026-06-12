---
title: "Lucid upgrade - Alternate CD"
date: 2010-05-05
forum: New to Ubuntu
---

### Post by dimitriv on 2010-05-05
Hi

I'm using 9.x and wanting to upgrade to 10.04 the pc is not connected to the internet.
I have the Alternate CD, I gather from reading other posts I may also need the Live CD.

How do I upgrade/install with the Alternate CD. If I boot from it it continues to ask questions such as 'Computer name' which concerned me that it was going to do a new install, not an upgrade.

Please advise, thank you

---

### Post by Kobalt on 2010-05-05
You'll find all needed information on upgrading using the Alternate CD here : [https://help.ubuntu.com/community/LucidUpgrades](https://help.ubuntu.com/community/LucidUpgrades)

---

### Post by yeats on 2010-05-05
To upgrade from the alternate CD, you just put in the CD it after booting into your current version (you say "9.X" - is this Karmic or Jaunty - there may not be a direct upgrade from Jaunty to Lucid - but I don't know that one way or the other).  The system should detect that the CD has a package repository - make sure to select that you do not want to download the newest packages from the Internet.

---

### Post by hellblazer on 2010-05-05
if it doesn't autorun, you can run ```
sh cdromupgrade
``` from the cd-rom root

---

