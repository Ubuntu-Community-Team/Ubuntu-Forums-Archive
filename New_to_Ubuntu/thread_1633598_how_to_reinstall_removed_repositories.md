---
title: "how to reinstall removed repositories?"
date: 2010-11-29
forum: New to Ubuntu
---

### Post by Louigi Verona on 2010-11-29
Hello guys!
I am on Ubuntu 10.04. Since the beginning had the infamous "[Requires installation of untrusted packages]("http://ubuntuforums.org/showthread.php?t=1339490&highlight=ubuntu+software+center")" problem. Sudo apt-key update does not seem to change anything, so I had to remove some of the repositories for good.

Now that I am left with almost an empty source list, I have no idea what  to do. Is there a "reset repositories list to default" button anywhere?

---

### Post by barney385 on 2010-11-29
Have you checked you software sources list at: System>Admin>Software sources ?

---

### Post by oldos2er on 2010-11-29
Which repositories? Could you re-enable all the repos you want to use, then run **sudo apt-get update && sudo apt-get upgrade** in a terminal, and post the output here? It shouldn't be too difficult to download the keys you need.

---

### Post by gmargo on 2010-11-29
Here's the default 10.04 Lucid sources.list file, attached.  Rename to "/etc/apt/sources.list" (backup the old one just in case!)

---

### Post by Louigi Verona on 2010-11-29
Thanks guys!

Here's what I did to solve the problem: removed all the offending repos. Then over irc talked to the author of the ppa and he helped me to reinstall all repos. Now everything seems fine since all the keys are valid.

---

