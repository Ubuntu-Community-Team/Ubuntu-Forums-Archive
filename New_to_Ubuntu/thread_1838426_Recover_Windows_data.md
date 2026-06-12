---
title: "Recover Windows data"
date: 2011-09-03
forum: New to Ubuntu
---

### Post by rrshanks on 2011-09-03
I installed Ubuntu 11.04 on an old Pentium desktop last week. I didn't choose the dual boot option and wiped out Windows entirely. Now my wife wants me to recover some old photos from that machine. How can I do this? Are there any tools in Ubuntu that will allow me to scan the hard disk and recover the Windows files?

Thanks

---

### Post by Leshrac on 2011-09-03
You can use Testdisk and Photorec [http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec), they do exactly what you want.

Keep in mind however that they are not magical, they can't recover something once it has been overwritten but you might be able to recover the pictures as long as they were not stored close to the beginning of the disk.

Edit: I forgot to add that you can install it directly from the software center, or by writing: "sudo apt-get install testdisk" without quotes in a console.

---

### Post by rrshanks on 2011-09-03
Thanks for the prompt reply Leshrac. I will give this a shot now..

---

