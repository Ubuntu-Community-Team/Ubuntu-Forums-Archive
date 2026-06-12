---
title: "Yet another Hibernate issue"
date: 2009-03-27
forum: New to Ubuntu
---

### Post by bawng on 2009-03-27
I know there's already a bunch of threads about hibernation but I couldn't find the right answer.
I recently installed Intrepid on a Samsung NC10. Suspend works fine but not hibernate. I've tried both pm-hibernate and s2disk and neither works.
pm-hibernate gives an error message about btusb which disappeared when I blacklisted that module, but hibernate would still not work.

It seems like everything goes fine while saving to disk (and the computer shuts down like it should) but when resuming, the computer just boots normally. It's as if it doesn't check if it was hibernated. Am I supposed to add an instruction for this somewhere?

Suspend works perfectly. (The one built into ubuntu. pm-suspend i guess?)

Anyone got any ideas?

Thanks
Erik

---

### Post by jerrrys on 2009-03-27
how much ram do you have? how big is your swap file?

---

### Post by bawng on 2009-03-28
ram is 1gb. swap is 3gb
at first s2disk complained over not having any swap. for some reason it thought that sdb6 was swap (sda6 would be correct). When i changed to sda6 it stopped complaining and seemed to hibernate like it should. just not resuming.

---

