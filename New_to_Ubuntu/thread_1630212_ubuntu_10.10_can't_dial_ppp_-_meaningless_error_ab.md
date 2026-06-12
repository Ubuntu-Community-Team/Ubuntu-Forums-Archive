---
title: "ubuntu 10.10 can't dial ppp - meaningless error about 'dip' group"
date: 2010-11-24
forum: New to Ubuntu
---

### Post by itsols on 2010-11-24
Since I got onto 10.10, every now and then, I find that my broadband link is down. And when I try:

pon dsl-provider

from the terminal I get this absurd error:

"Error: only members of the 'dip' group can use this command"

Am I overlooking something or is this a bug.

Strangely, sometimes I try connecting with sudo and it work. But sometimes it does not... Only a reboot is able to bring things back. Sometimes (on a different computer) even the reboot doesn't work.

Please advise...

Many thanks!

---

### Post by BugBuster on 2010-11-24
Add yourself (your username) to the dip group by doing so..

```
sudo usermod -a -G dip <username>
```

Then logout and login again and you should be able to use "pon dsl-provider" without the sudo prefix.

CAUTION: Remember to add the -a option or else you will be locked out of your own machine!!

---

### Post by itsols on 2010-11-25
I don't understand why it was necessary in this version but it did the trick!

Thanks a lot!!!

---

### Post by QLee on 2010-11-25
> **itsols said:**
> I don't understand why it was necessary in this version but it did the trick!

On my system, access to /etc/ppp/peers/ and the "provider" files in that container are restricted to root and members of the dip group, perhaps yours are the same. In that case, the error message is not meaningless, rather it is useful.

---

### Post by itsols on 2010-11-25
Yup, it does makes sense... And I've got to get used to SURPRISE CHANGES from now on :)

Thanks!

---

### Post by QLee on 2010-11-25
Get used to trusting GNU/Linux error messages, they often point in the right direction, at the very least give a "keyword" which can be used in a search engine. That has helped me many times.

---

