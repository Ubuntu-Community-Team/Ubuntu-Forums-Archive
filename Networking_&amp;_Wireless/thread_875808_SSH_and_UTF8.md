---
title: "SSH and UTF8"
date: 2008-07-31
forum: Networking &amp; Wireless
---

### Post by katzal on 2008-07-31
hi. 

I installed JeOS on a fresh VM. However when i connect ssh via putty all special characters the server sends are not displayed correctly. e.g. the german character 'ä' becomes 'Ã¤'. 
Seems, putty does display two-byte utf-8 characters as two ascii characters.

what can I do? Is there an option to tell openssh-server only to send in ascii? which ssh client for windows do you recommend?

greets, katzal

---

### Post by katzal on 2008-07-31
closed. found the utf-8 option in putty settings

---

### Post by dmizer on 2008-07-31
Please use the "thread tools" drop down and select "solved" so that others know there is a solution here.

---

