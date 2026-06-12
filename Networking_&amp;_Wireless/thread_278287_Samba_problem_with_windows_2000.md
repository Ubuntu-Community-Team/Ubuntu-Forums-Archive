---
title: "Samba problem with windows 2000"
date: 2006-10-16
forum: Networking &amp; Wireless
---

### Post by aida on 2006-10-16
Hello,

I have 3 computers: an ubuntu dapper, a windows xp and a windows 2000 (service pack 4). I setup samba (3.0.22) on ubuntu and shared some files, I can access these shares without any problem from my windows xp computer but from my windows 2000 computer i can only read files, when i try to write it takes a long time and then fails.

I searched the forums and found some other people having this problem but no solutions.

---

### Post by TheWizzard on 2006-10-16
interesting. i did run into problems when trying to configure mu samba server. in the end i just used the /etc/samba/smb.conf file from a previous (fedora) installation. 
i use both linux and win2k to access the samba server and both work. 
if you post your /etc/samba/smb.conf we can try to track down the problem.

---

