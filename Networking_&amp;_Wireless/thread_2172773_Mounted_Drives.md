---
title: "Mounted Drives"
date: 2013-09-06
forum: Networking &amp; Wireless
---

### Post by Tropicalbound on 2013-09-06
Good day!

When I look in the /mnt folder, I see all the mount points that I have created.  Is there a command I can enter to view which mount points are in use?  As the day goes on, sometimes I am unsure if I have mounted a drive or not.

Thank you!!

TB

---

### Post by Crusty Old Fart on 2013-09-06
Yes.
```

df | grep -v ^none

```

---

### Post by Tropicalbound on 2013-09-06
Perfect!

Thank you.

TB

---

### Post by Crusty Old Fart on 2013-09-06
You're mighty welcome.
I edited the command to specify that the regular expression should match the word: none, at the beginning of the line.
It' a little better that way.

```


     Please mark your thread as: [SOLVED]. Thanks.

                         _---_
                        /_/|\_\
                       (/-O^O-\)
                __    /_\\/*\//_\    __
         ------vVVv----- o###o -----vVVv------
                          """

                   Darthroy was here.


```

---

