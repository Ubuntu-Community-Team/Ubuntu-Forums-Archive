---
title: "Requires installation of untrusted packages"
date: 2011-02-21
forum: New to Ubuntu
---

### Post by davidbarik on 2011-02-21
Here i am facing problem while updating my System,i am using Ubuntu 10.10 
System shows following error..
[SIZE=2][B]
Requires installation of untrusted packages[/B][/SIZE]

The action would require the installation of packages from not authenticated sources.

**Details**

libvpx0


How can i update my system??

---

### Post by fabricator4 on 2011-02-21
> **davidbarik said:**
> How can i update my system??

Have you changed your update servers recently?  I had similar thing recently when I had very slow data from the Australian server.  I changed to a NZ mirror (selected as 'best server' after doing some tests) and started getting this "untrusted packages" message.  I changed back to the "Server for Australia" and the problem went away.  I have no idea what's going on: maybe some of the mirrors aren't official ones?

Chris

---

### Post by bioterror on 2011-02-21
> **davidbarik said:**
> Here i am facing problem while updating my System,i am using Ubuntu 10.10 
System shows following error..
[SIZE=2][B]
Requires installation of untrusted packages[/B][/SIZE]

The action would require the installation of packages from not authenticated sources.

**Details**

libvpx0


How can i update my system??

open terminal, and say
```

sudo apt-get update

```

And after that

```
sudo apt-get upgrade
```

You need to put your password and possible press Y ;)

---

### Post by davidbarik on 2011-02-21
Thank You ..It works!!!

---

### Post by grahammechanical on 2011-02-21
I have another understanding of this issue. I may be wrong. 

When I go to the Update Manager and click on Settings I see some tabs. The Ubuntu Software tab has some check boxes, which include "Canonical Supported Open Source Software" and "Community Maintained Open Source Software". I assume these to be trusted sources.

There is another tab - Other software. The check boxes on this tab are for Canonical Partners (software packaged by Canonical for their partners). This I also assume is a trusted source.

Then there are check boxes for Independent (software provided by third party developers). These are links direct to the developers website. They are called PPAs and I have put these links in myself. I think these are what Canonical is saying are untrusted sources not because the developers are necessarily untrustworthy but because we have chosen to put the update links there and they work outside of the Ubuntu arrangement for updates.

Regards.

---

