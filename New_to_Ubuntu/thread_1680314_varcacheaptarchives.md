---
title: "/var/cache/apt/archives/"
date: 2011-02-02
forum: New to Ubuntu
---

### Post by Blutkoete on 2011-02-02
Hello!

Does anything else than "apt-get clean" remove files from the */var/cache/apt/archives/* folder?

I never ran *apt-get clean* on my desktop at home and wanted to copy the tex packages from there to my netbook, as my bandwith is limited and *texlive-full* is larger than a gigabyte. That procedure always worked for me in the past - but yesterday I was astonished that after copying the whole folder to my netbook after a clean Kubuntu install there, it still wanted to download over 700 MB when I tried to install texlive full.

So is there any other process that cleans the folder from time to time and/or any way to avoid that? I'm sure I never ran *apt-get clean*, and actually half of the packages are still there, only half of them are missing.

Thank you very much,

Blutkoete

---

### Post by psusi on 2011-02-02
IIRC, there is a cron job that auto cleans old packages after enough time.

---

### Post by Blutkoete on 2011-02-02
Thank you!

I'll try to find that cron job and deactivate it.

P.S.: And I learned a new acronym. I googled for "IIRC" because I thought that's the name of a program running in the background ;).

---

### Post by Blutkoete on 2011-02-02
The "bad guy" is *apt* in */etc/cron.daily* which can be configured with */etc/apt/apt.conf.d/02periodic*.

I'll dive a little bit deeper into that.

Thank you again. Marked as solved.

---

### Post by gmargo on 2011-02-02
Instead of trying to disable normal maintenance tasks, you should try installing a proper tool designed for proxying and caching your .deb downloads, namely **apt-cacher-ng**.  Point all your machines through it, and no more duplicate downloads.

[http://packages.ubuntu.com/maverick/apt-cacher-ng](http://packages.ubuntu.com/maverick/apt-cacher-ng)

---

### Post by Blutkoete on 2011-02-03
You're probably right. For now, I haven't disabled the cron job (just configured a higher MaxAge for the packages) and am trying out apt-cacher-ng which sounds just like what I was always looking for.

Thank you!

---

