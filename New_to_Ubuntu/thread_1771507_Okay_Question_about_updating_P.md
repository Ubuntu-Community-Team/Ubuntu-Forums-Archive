---
title: "Okay Question about updating :P"
date: 2011-05-30
forum: New to Ubuntu
---

### Post by BloodRyaneX on 2011-05-30
Sadly I'm running like 9.10 on my ubuntu and its wanting me to upgrade to 10.04 if I upgrade... Will I loose all my files or no? 



Yes I'm still new with linux :):P

---

### Post by Paqman on 2011-05-30
No, if you do an upgrade all your files will be fine.

What it will do is disable any PPAs you're using, then upgrade all your packages with ones from the 10.04 repo. It's a bit like a really massive version of a normal update. Afterwards you'll have to change your PPAs to Lucid instead of Karmic, then re-enable them. You can do that in the Software Sources tool.

However, it's always a good idea to have a backup of your data anyway, so do one before you start just in case anything goes wonky.

Once you're on 10.04 you'll have two more years before you have to upgrade again.

---

### Post by BloodRyaneX on 2011-05-30
Yay! Thank you! I did do some back ups :) but Not many just like saves from some games and drawings I did!

---

### Post by BloodRyaneX on 2011-05-30
Okay, so I'm trying to upgrade but it says "An upgrade from 'jaunty' to 'Lucid' is not supported with this tool"


What does that mean?

---

### Post by sanderd17 on 2011-05-30
You said you used 9.10 (karmik) but the update manager sais Jaunty (9.04). It is only possible to upgrade from release to release. So

9.04 -> 9.10 -> 10.04...

or from LTS to LTS, so

8.04 -> 10.04 -> 12.04...

Upgrading from 9.04 to 10.04 is not supported.

If you still have 9.04, it won't be possible to upgrade since 9.10 has already reached the end of life. That means that the repositories of 9.10 are taken offline.

---

### Post by Paqman on 2011-05-30
> **sanderd17 said:**
> 
If you still have 9.04, it won't be possible to upgrade since 9.10 has already reached the end of life. That means that the repositories of 9.10 are taken offline.

Indeed. If this is the case, your only option is to install a fresh system with a supported version of Ubuntu (anything 10.04 or later). 

_Don't_ just continue to use your old system if it's connected to the internet, as it won't be getting security updates any more.

---

