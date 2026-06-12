---
title: "How to remove suspicious files form rkhunter and chkrootkit"
date: 2009-02-21
forum: New to Ubuntu
---

### Post by Ravernomina on 2009-02-21
Hey i ran both of these to see if my system was clean. I had some suspicious files can some 1 help me on what to do next TYVM.

     Ravernomina

---

### Post by llamakc on 2009-02-21
Are you certain that they are not false positives?

---

### Post by gandaran on 2009-02-21
> **Ravernomina said:**
> Hey i ran both of these to see if my system was clean. I had some suspicious files can some 1 help me on what to do next TYVM.

     Ravernomina
edit the rkhunter configuration file, command **sudo gedit /etc/rkhunter.conf**
uncomment the suspicious files lines, they are just warnings nothing to worry about!

---

### Post by Ravernomina on 2009-02-21
idk if they are or not, i cleaned 1 files and so far i didn't crash

after i deleted the file rkhunter said i was clean.

Then i ran chkrootkit and it gave me this

Searching for suspicious files and dirs, it may take a while... 
/usr/lib/xulrunner-1.9.0.6/.autoreg
/usr/lib/jvm/.java-6-sun.jinfo
/usr/lib/jvm/java-1.5.0-sun-1.5.0.16/.systemPrefs
/usr/lib/jvm/.java-6-openjdk.jinfo 
/usr/lib/jvm/java-6-sun-1.6.0.10/.systemPrefs 
/usr/lib/jvm/.java-6-cacao.jinfo
/usr/lib/jvm/.java-1.5.0-sun.jinfo 
/usr/lib/firefox-3.0.6/.autoreg 
/lib/modules/2.6.27-11-generic/volatile/.mounted 
/lib/init/rw/.ramfs

IF they are let me know pl0x :3

     Ravernomina


please let me know if they are infectedf iles or not :3

---

### Post by gandaran on 2009-02-21
> **Ravernomina said:**
> idk if they are or not, i cleaned 1 files and so far i didn't crash

after i deleted the file rkhunter said i was clean.

Then i ran chkrootkit and it gave me this

Searching for suspicious files and dirs, it may take a while... 
/usr/lib/xulrunner-1.9.0.6/.autoreg
/usr/lib/jvm/.java-6-sun.jinfo
/usr/lib/jvm/java-1.5.0-sun-1.5.0.16/.systemPrefs
/usr/lib/jvm/.java-6-openjdk.jinfo 
/usr/lib/jvm/java-6-sun-1.6.0.10/.systemPrefs 
/usr/lib/jvm/.java-6-cacao.jinfo
/usr/lib/jvm/.java-1.5.0-sun.jinfo 
/usr/lib/firefox-3.0.6/.autoreg 
/lib/modules/2.6.27-11-generic/volatile/.mounted 
/lib/init/rw/.ramfs

IF they are let me know pl0x :3

     Ravernomina


please let me know if they are infectedf iles or not :3
nothing to worry about, all hidden files (like .java) are reported so that you decide what to do about it, if you find a suspicious one just google that line, theres plenty of information in the internet.
don't delete any file they are needed.

---

### Post by brian_p on 2009-02-21
> **Ravernomina said:**
> Hey i ran both of these to see if my system was clean. I had some suspicious files can some 1 help me on what to do next TYVM.

I would be suspicious and wary of any warning about suspicious files given by either of these programs as they usually get it wrong. Under no circumstances would I ever delete one of them without a thorough investigation. The files it names are usually part of a normal system.

---

### Post by Ravernomina on 2009-02-21
alright thanks for all the info :3. It just that im new to linux and i like it alot better then Windows. And Its just new stuff so im being like Whoa careful so ty for all your help :3.

---

