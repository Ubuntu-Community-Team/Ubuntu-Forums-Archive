---
title: "ubuntu at school problems"
date: 2009-01-27
forum: New to Ubuntu
---

### Post by justme0406 on 2009-01-27
I set up the main computer lab to duel boot in my school (with permission) for a web server class and the students need to be admins so the can access '/var/www' for PHP but we don't want to let them mount the windows partition. i cant give them admin rights without them mounting windows and if i get rid of the admin rights the cant do PHP. I'd rather not give them admin right and just let them edit files in /var/www because we only have me to fix things in Linux and I'm not that advanced plus I'm only a student.

i know it's a long story and i need help the only teacher that knows linux in the school only knows red hat 5

Please help

---

### Post by DGortze380 on 2009-01-27
You should be able to configure sudoers to allow sudo access (admin access) to /var/www and no other services. I'll have to research how, maybe someone else know off the top of their head.

---

### Post by LowSky on 2009-01-27
the guy who know RH5 can still help the commands as they are still the same.
All you need to do is create a new user group (maybe call it Student) add the kids to the student group. Then for the folder in question (var/www) change it so that root and/or student can acess that folder.

This way the students can access the folder but not the other directories.

---

### Post by justme0406 on 2009-01-27
Thank you that worked

---

