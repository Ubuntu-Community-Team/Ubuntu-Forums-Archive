---
title: "Flash Player Stops Working In Firefox-3.5 after a while."
date: 2009-08-25
forum: New to Ubuntu
---

### Post by Matuku on 2009-08-25
I'm running 64-bit Linux Mint 7 and installed Firefox 3.5 from the repos. Originally the flash didn't work at all but I downloaded the 64-bit beta flash player and put it in ~/.mozilla/plugins as a walkthrough told me to. Flash seems to work now but only initially after firefox is started; if I find a flash game/movie after about 30 minutes then it fails to load. I can restart firefox and it'll work fine so I'm not sure what's happening here...

Any ideas?

---

### Post by Ocxic on 2009-08-25
make sure you remove any other instances of flash that may be installed from "/usr/lib/mozilla/plugins" and /usr/lib/firefox/plugins

---

### Post by Matuku on 2009-08-25
Just go to the folders and delete them? Or should a terminal command be used?

---

### Post by Ocxic on 2009-08-26
either way, but to use nautilus(file browser), type "gksu nautilus" in a terminal.

by the way, I used to have the same problem and doing the same thing fixed it for me.

---

