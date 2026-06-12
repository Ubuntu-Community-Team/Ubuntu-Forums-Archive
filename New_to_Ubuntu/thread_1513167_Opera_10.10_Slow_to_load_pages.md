---
title: "Opera 10.10 Slow to load pages"
date: 2010-06-19
forum: New to Ubuntu
---

### Post by terrykiwi83 on 2010-06-19
Well have been having some problems with Opera 10.10 on my Ubuntu 10.04 install now since day one. Basically type in a web address, hit enter and...... nothing happens for about 10 seconds then gradually the page will load up very slowly.

Have tried the same browser on Win 7 and its lightning fast, also have tried Firefox on my Ubuntu install and that to is much faster.

Have already tried disabling IPv6 and that has had not much affect.

Just out of ideas at the moment and looking for some guidance.

Thanks

---

### Post by Soul-Sing on 2010-06-19
when you take a look at your syslog or messages log, do you find so called "segfault errors"?
(after starting Opera?)

---

### Post by terrykiwi83 on 2010-06-19
have just had a browse through the log files and found nothing relating to segfault errors?

---

### Post by Soul-Sing on 2010-06-19
> **terrykiwi83 said:**
> have just had a browse through the log files and found nothing relating to segfault errors?

ok, thx every time I start Opera in 10.04 I have got these errors
and a delayed/slow start.

---

### Post by lovinglinux on 2010-06-19
Opera 10.10 is a lot slower than Firefox and Chrome here. See [this video](http://lovinglinuxblog.blogspot.com/2010/05/browser-speed-test.html) and tell if that is what you see.

---

### Post by PinchedNerve on 2010-06-19
Download the [10.60 beta]("http://www.opera.com/browser/next/"), I think you'll be happier.

---

### Post by Tombgeek on 2010-06-19
Opera has been known to be a slow web browser, especially with Linux versions, but as far as I know the 10.60 beta is not that bad. But Firefox and Chrome are the fastest web browsers available.

---

### Post by Linuxforall on 2010-06-23
Till Chrome came along, Opera has always been the undisputed speed king in both Windows and Linux along with some incompatibility issues with poorly designed webpages. That changed with Chrome which beat version 10.10 handily and even FF managed to scrape past Opera 10.10. However with version 10.50, Opera started beating out even dev versions of Chrome and FF was just a history. The latest 10.6 alpha for Opera handily beats whatever Chrome has on offer, be it stable or dev. The fastest benchmark on Peacekeeper site for the last few months has been Opera and not Chrome.

---

### Post by Linuxforall on 2010-06-23
> **terrykiwi83 said:**
> Well have been having some problems with Opera 10.10 on my Ubuntu 10.04 install now since day one. Basically type in a web address, hit enter and...... nothing happens for about 10 seconds then gradually the page will load up very slowly.

Have tried the same browser on Win 7 and its lightning fast, also have tried Firefox on my Ubuntu install and that to is much faster.

Have already tried disabling IPv6 and that has had not much affect.

Just out of ideas at the moment and looking for some guidance.

Thanks


In Opera advanced>preferences>network, turn off look for local machines, thats whats causing your delay. 10.10 may not be quickest but its no slouch either.

---

