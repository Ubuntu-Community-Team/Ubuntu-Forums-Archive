---
title: "ndiswrapper is being inconsistant"
date: 2006-12-02
forum: Networking &amp; Wireless
---

### Post by joshdavies on 2006-12-02
OK, I tried to install Edgy, eventually got it installed, and found that I could not get ndiswrapper to work. After some googling, I found that Edgy is very buggy about this, and that I needed a specific version. After locating this version, I still couldnt get it to work, and so gave up, and reinstalled trusty old dapper.

Howver, much to my dissapointment, it wouldnt work on dapper either. I am using the same versions of ndiswrapper (ndiswrapper-utils_1.8-0ubuntu2_i386.deb) and (ndisgtk_0.6-0ubuntu1_all.deb) as I have always used in dapper, but now, they just don't work. I always install ndiswrapper as the first thing I do when dapper loads for the first time, and I have done this several times, and remember how I did it, but for some reason, it doesnt now.

If using ndisgtk, I sudo ndisgtk, and it appears, I click add driver, locate it, but it will not appear in the list, like it used to.

If i use ndiswrapper with the command line, it says it has installed it, and the driver is present in "ndiswrapper -l".

If I do "modmap ndiswrapper" it says "the alias is already present" or something like that.


Anyone got any ideas as to what is going wrong? It has confused me, as I am not doing anything differently from previous times when I have done this and it has worked.

(also, I have tried reformatting dapper after this problem occurred, and it did it again)


Thanks,
Josh Davies.

---

### Post by joshdavies on 2006-12-03
bump ;)

---

