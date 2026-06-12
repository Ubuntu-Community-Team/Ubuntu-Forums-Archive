---
title: "I installed netbeans on ubuntu but now...."
date: 2010-08-24
forum: New to Ubuntu
---

### Post by fawzan on 2010-08-24
i installed net beans via this code
sudo apt-get install netbeans
after that it was appearing there in application tab. but i did not open at least once after i installed it. 
without checking it at least once. i shut down my machine. when i turn on it again, it was not appearing there where it was before. what is the reason for that? how can i get netbeans that i have already installed. 

Please clarify. Thank you.

---

### Post by kaldor on 2010-08-24
From my understanding, you installed Netbeans but it is not showing up in your menus? 

Right click on the GNOME menu (Applications, System, etc) and click edit menus. In the Programming tab, make sure Netbeans is listed. If it is not, then click "New item" and then in the fields, fill in:

Type: Application
Name: Netbeans IDE (or whatever you want to call it)
Command: netbeans (or if that doesn't work, /usr/bin/netbeans)
Comment: An IDE

To make sure that it is actually installed, type netbeans in the terminal.

I hope I wasn't too vague. This is all from memory :)

---

### Post by fawzan on 2010-08-24
Thanks a lot dude....

---

### Post by kaldor on 2010-08-24
Not a problem! Be sure to mark the thread as Solved :)

---

### Post by krishnasrikanth on 2011-04-08
I installed from the .sh file downloaded from netbeans.org. But after restart the shortcut was missing. Saw the response in this thread but actually it got installed in /usr/local/netbeans-6.9.1 folder. So I gave the shortcut as /usr/local/netbeans-6.9.1/bin/netbeans. Now it is working for me. :)

---

