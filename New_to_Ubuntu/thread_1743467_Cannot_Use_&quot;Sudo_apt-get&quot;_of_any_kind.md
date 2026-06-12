---
title: "Cannot Use &quot;Sudo apt-get&quot; of any kind?"
date: 2011-04-29
forum: New to Ubuntu
---

### Post by Riku Reed on 2011-04-29
When I open up the terminal, everything I try to use "sudo apt-get update", "sudo apt-get autoclean", "sudo apt-get autoremove", and Etc. it always returns me this this "> E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?"

I checked to see if synaptic was running, it's not.
I checked to see if anything else was up and running from preventing me to use sudo apt-get and still I cannot.

Why has it locked me out?

---

### Post by Riku Reed on 2011-04-29
I read this post: [http://ubuntuforums.org/archive/index.php/t-519612.html](http://ubuntuforums.org/archive/index.php/t-519612.html)

I tried "sudo rm /var/lib/dpkg/lock" and I can now use "sudo apt-get update" and the others.:D

---

### Post by earthpigg on 2011-04-29
maybe update manager, maybe ubuntu software center, but either *some* package manager *is* running, or something is very broken.

if 30 seconds of clicking around isn't letting you find whatever is running in the background, log out and back in.

---

