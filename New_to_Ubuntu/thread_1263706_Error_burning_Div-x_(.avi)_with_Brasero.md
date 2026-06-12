---
title: "Error burning Div-x (.avi) with Brasero"
date: 2009-09-11
forum: New to Ubuntu
---

### Post by webwiller on 2009-09-11
hi all and thanks in advance for your help!
It's the third time I'm trying to burn a video Dvd with Brasero. Everything seems right but early stage of concrete burning Brasero stops and ejects disk saying an error accured.
I thought it was because of a faulty disk but now I'm sure it isn't.

---

### Post by zerhacke on 2009-09-11
Sounds like your permissions on your CD Burner are borked.

In a terminal, type the following

sudo chmod 777 /dev/scd0

And press enter, then give it your password.  After that you should be able to burn.

---

### Post by webwiller on 2009-09-11
How can it be...I burned a data dvd just yesterday...
Anyway...mt disk sounds like /dev/sda...should I write this instead of sdc?

---

### Post by webwiller on 2009-09-11
How can it be...I burned a data dvd just yesterday...
Anyway...mt disk sounds like /dev/sda...should I write this instead of scd0? Like sda0? My disk is partitioned too, does it change anything?

---

