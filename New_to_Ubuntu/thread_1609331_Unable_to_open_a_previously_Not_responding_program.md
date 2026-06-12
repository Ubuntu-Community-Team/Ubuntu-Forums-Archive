---
title: "Unable to open a previously Not responding program on UBUNTU NETBOOK10.10"
date: 2010-10-30
forum: New to Ubuntu
---

### Post by zee965 on 2010-10-30
Assalmu Alaikum Dear All!
I am a new user of Ubuntu. i ve Ubuntu Net book Edition 10.10 installed on my nc6220.

My Kmobiletools was not responding and i reinstalled it but now when i click the icon of it no window opens. Plz Guide me what to do now?


Regards,
Zia

---

### Post by xjesse on 2010-10-30
Most likely it's still running. Open a terminal and type:

```
top
```

See if it's listed, if it is kill it by typing:

```
kill ***id number***
```

Or alternatively just restart.

---

### Post by Omnomnom on 2010-10-30
Did you try killall Kmobiletools and a restart?

---

