---
title: "Burning iso with Brasero"
date: 2009-07-05
forum: New to Ubuntu
---

### Post by nepmit on 2009-07-05
Since Jaunty the lowest iso burn speed I can do is 24. I use to be able to burn at 2.5 with the same hardware. I've tried on several rigs and many burners. Is anyone else having this issue?  I'm trying to burn a Ubuntu Live CD but not at 24. Thanks

---

### Post by MrWES on 2009-07-05
> **nepmit said:**
> Since Jaunty the lowest iso burn speed I can do is 24. I use to be able to burn at 2.5 with the same hardware. I've tried on several rigs and many burners. Is anyone else having this issue?  I'm trying to burn a Ubuntu Live CD but not at 24. Thanks

Try this from the terminal command line, of course change the name of the iso to suit your needs:

```
wodim dev=/dev/scd0 driveropts=burnfree -v speed=2.5 -data cd_image.iso
```

---

### Post by Sef on 2009-07-05
> Since Jaunty the lowest iso burn speed I can do is 24. I use to be able to burn at 2.5 with the same hardware. I've tried on several rigs and many burners. Is anyone else having this issue? I'm trying to burn a Ubuntu Live CD but not at 24. Thanks

I've been burning isos at that speed (24) and have not had a problem with a bad disk.

Have you had problems with bad disks?

---

### Post by ramjet_1953 on 2009-07-05
I know it's a bit off-topic, but I have found that since recent updates, even in Hardy, Brasero doesn't seem to work as well as it used to with my hardware.

However, I downloaded the GnomeBaker package using Synaptic and have found that it seems to work much better.

Of course, with your particular configuration, that may not be the case, but it may be worth a try.

Regards.
Roger O:)

---

### Post by RedRat on 2009-07-05
I run 8.04 and have had difficulties with Brasero. Very good luck with GnomeBaker though, so far no problems. Interface is a bit tricky but it works very well for me.

---

### Post by nepmit on 2009-07-06
Thank for responding. MrWes, I tried your suggestion but didn't work. Sef, Yes burning at 24 failed to install. Ramjet and Redhat I'll give Gnomebaker a try. Thanks to all. It's strange that all Ubuntu forums recommend burning Live CDs at the slowest possible speed (2,4) and the default burner only allows a burn at 24.

---

### Post by MrWES on 2009-07-06
> **nepmit said:**
> Thank for responding. MrWes, I tried your suggestion but didn't work. Sef, Yes burning at 24 failed to install. Ramjet and Redhat I'll give Gnomebaker a try. Thanks to all. It's strange that all Ubuntu forums recommend burning Live CDs at the slowest possible speed (2,4) and the default burner only allows a burn at 24.


Sorry, I probably made the assumption you had wodim installed. First install it:
```
sudo apt-get install wodim
```
Now try burning the iso with the following command:
```
wodim -speed=2 yourisofilehere.iso
```

Bill

---

