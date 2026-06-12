---
title: "Translation-en_US failed"
date: 2008-12-26
forum: New to Ubuntu
---

### Post by jratliff on 2008-12-26
I get this message every time I update the package list. It doesn't seem to matter because the updates run afterwards. What does it mean though? Should I try to fix it? How?

Thanks.

---

### Post by juliobahar on 2009-06-11
> **jratliff said:**
> I get this message every time I update the package list. It doesn't seem to matter because the updates run afterwards. What does it mean though? Should I try to fix it? How?

Thanks.

I'm also getting the same message while running update-manager. What should that mean? I'm running Jaunty upgraded from Intrepid.

ANYONE?

---

### Post by Speed Of Light on 2010-05-17
I get that message too with Lucid !
any ideas ?

---

### Post by drs305 on 2010-05-17
It's harmless, but if you want to rid yourself of the message you can run this before updating the repositories:
```
unset LANG LANGUAGE
```

---

### Post by Speed Of Light on 2010-05-17
Thanks for answering !
I know it's harmless, but it's annoying !
and it's not a workaround to do an "unset" every time you update !!
I'm still a n00b, and I'm interested in knowing why this is happening?
Is it from Ubuntu repositories ? or is it something else ?

---

### Post by drs305 on 2010-05-17
Sorry for the incomplete answer. I knew the APT folder/files had changed a bit with recent releases but hadn't snooped around to find them at that point. Disclaimer - I can only provide the solution, not an explanation of how this part of APT works.

Here is a more permanent way to prevent the error messages. Add this line to /etc/apt/apt.conf.d/10periodic:
> APT::Acquire::Translation "none";

Edit:

Now deprecated to the following, but no longer appears to work properly:
> APT::Acquire::Languages "none";

---

