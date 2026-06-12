---
title: "finding out whether clamAV is running"
date: 2007-08-21
forum: Networking &amp; Wireless
---

### Post by Incompetnce on 2007-08-21
I have checked in synaptic and I have clamAV installed. I know I probably won't need virus protection much, but I'd like to be on the safe side. I don't know how to find out whether the virus protection is active or just installed and not working. I don't have anything related to the AV in the applications menu. I'm not entirely sure what to do... I'd like to make sure that everything is up to date and be able to scan every once in a while. This is more for my presence of mind than for any genuine threat to my machine... Should I get a GUI for clamAV? does such a thing exist?

---

### Post by ajgreeny on 2007-08-21
Clamav doesn't run in the background like antivirus does in windows as it's not needed.  You run clamav by using the terminal and typing **clamscan [option]**

Have a look at **man clamscan** in a terminal and it will tell you a lot more about using it, or get clamtk or klamav, both of which are GUIs for clamav.

Best to use, at least I think so, is **clamscan -ri** which checks all files in your /home/username folder recursively and only reports infected files.

---

