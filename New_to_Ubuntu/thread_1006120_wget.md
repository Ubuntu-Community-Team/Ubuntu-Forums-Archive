---
title: "wget"
date: 2008-12-09
forum: New to Ubuntu
---

### Post by Skivache on 2008-12-09
Im trying to set up a cron to wget a file once a day at a specific time.  Im currently using wget -O name.type url, but would like for the date (day, number date, something) to also be appended to the file name.  Is this possible via a wget command or any other simple method?

---

### Post by andrew.46 on 2008-12-09
Hi Skivache:

> **Skivache said:**
> Im trying to set up a cron to wget a file once a day at a specific time.  Im currently using wget -O name.type url, but would like for the date (day, number date, something) to also be appended to the file name.  Is this possible via a wget command or any other simple method?

If you are after a really simple method simply put backticks around your preferred date syntax. For example:

```
$ wget -O myfile_`date +%d%m%Y` my_url
```

This should work well and of course the date command allows many, many permutations.

All the best,

  Andrew

---

### Post by Skivache on 2008-12-09
Excellent, that is exactly what I was looking for!  Thanks for the suggestion. :D

---

