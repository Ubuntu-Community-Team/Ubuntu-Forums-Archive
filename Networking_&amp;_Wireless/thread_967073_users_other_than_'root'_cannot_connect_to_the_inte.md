---
title: "users other than 'root' cannot connect to the internet"
date: 2008-11-01
forum: Networking &amp; Wireless
---

### Post by paolomatteis on 2008-11-01
I can access the internet only when using the user root, not when using any other user. I've tried to give more privileges to the other users (also including administration privileges), and also to create new users, without success.
I access the internet through my own WiFi router (itself connected to an ISP). Users other than root can access the administration page of the WiFi router itself (which imply that they can use the WiFi), but no other web address or service, whereas the root user works on the internet without any problem.

Up to a few days ago everything was working (i.e., all users reached the internet); then upon booting the pc said it had some problem with the file system and required to run 'fsck', which I did; this apparently corrected a series of incoherences in the file system (I always chose 'yes' whenever it asked permission to correct an error), and then the pc booted correctly. This had happened a few times previously, and every time the system was then completely recovered and worked correctly; however, this time I've then encountered the internet problem described above.

Can somebody help me? Thank you very much for your attention.

---

### Post by lisati on 2008-11-01
You might want to check the user's privileges on the Applications->System->users and groups menu. The same thing that caused fsck to find errors could have also scrambled the settings.

---

### Post by paolomatteis on 2008-11-02
I've given to the users all the privileges listed in the GUI (in System > Administration > Users and groups > User privileges), but it does not work.
Do you know which specific group / privileges a user needs to work on the internet?

---

### Post by paolomatteis on 2008-11-02
I've given to the users all the privileges listed in the GUI (in System > Administration > Users and groups > User privileges), but it does not work.
Do you know which specific group / privileges a user needs to work on the internet?

---

