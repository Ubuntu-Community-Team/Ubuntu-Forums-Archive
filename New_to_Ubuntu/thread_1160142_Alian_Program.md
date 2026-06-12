---
title: "Alian Program"
date: 2009-05-15
forum: New to Ubuntu
---

### Post by Leshinsky on 2009-05-15
Can anyone tell me what this means and how to fix it.  it was cut and pasted from my terminal window.

matthew@ubuntu:~$ sudo apt-get install alien
[sudo] password for matthew: 
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
matthew@ubuntu:~$

---

### Post by kanikilu on 2009-05-15
It looks like another program is using dpkg. Only one can be used at a time, so look for and close any instances of Add/Remove or Synaptic before trying to use apt-get.

---

### Post by LTFC2020 on 2009-05-15
I found this with a search
Hopefully your problem is as simple as running two installation appliactions at once

Check if Synaptic Package Manager is open or if another package update / installation application is already running. Close any other package managers (including Add/Remove application, language pack installer, etc.) and retry.

Good luck

---

### Post by LTFC2020 on 2009-05-15
ah
was beaten too it ):P

---

### Post by Leshinsky on 2009-05-15
I could not find any other open programs.  i even reboted my computer and did not open anything else.  any other ideas.

---

### Post by kanikilu on 2009-05-15
Check out this thread for other suggestions, including how to manually remove the lock if you're sure nothing else is using it.

[http://ubuntuforums.org/showthread.php?t=207743](http://ubuntuforums.org/showthread.php?t=207743)

---

