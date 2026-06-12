---
title: "Thunderbird - automount drive"
date: 2009-08-03
forum: New to Ubuntu
---

### Post by il pepe on 2009-08-03
I'm again in deep dodoo with thunderbird.

After some time i got thunderbird running on ubuntu, as i was using it under vista. Sharing profiles and stuff all worked well. (at least after some tuning).
These profiles were on a NTFS drive as i'm dual booting Vista and ubuntu and i have had vista longer then ubuntu.

So i had to open the NTFS drive at the start to be able to connect to this NTFS drive. and then it worked.

Then i had the idea of automounting the NTFS drive, to make things easier. But then it all fell apart.
Thunderbird wouldn't start anymore and said it was already running. It wasn't the lock file, as i have encounered this problem before.

Then i removed thunderbird from the applications, and reinstalled it several times, and i always get the same problem over and over again. It says it's already running.

Any help?

---

### Post by JagDragon on 2009-08-03
What method are you using to automount your NTFS drive? And does your user have read/write access to it when it is automounted?

---

### Post by il pepe on 2009-08-03
> **JagDragon said:**
> What method are you using to automount your NTFS drive? And does your user have read/write access to it when it is automounted?
i followed the steps like in this post: [http://ubuntuforums.org/showthread.php?t=785263](http://ubuntuforums.org/showthread.php?t=785263)

But as i have removed thunderbird, i thought i also would have deleted the connection towards the NTFS disk. I would import these profiles again afterwards, but i can't even start Thunderbird...

---

### Post by il pepe on 2009-08-03
Problem solved with:

[http://ubuntuforums.org/archive/index.php/t-253593.html](http://ubuntuforums.org/archive/index.php/t-253593.html)

---

