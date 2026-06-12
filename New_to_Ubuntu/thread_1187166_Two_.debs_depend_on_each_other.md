---
title: "Two .debs depend on each other"
date: 2009-06-14
forum: New to Ubuntu
---

### Post by sparky8251 on 2009-06-14
How would I install two .debs that reqire each other? If it helps here are the flie names:
 
libstdc++6-4.3-dev_4.3.2
 
g++-4.3_4.3.2

---

### Post by CatKiller on 2009-06-14
sudo dpkg -i  libstdc++6-4.3-dev_4.3.2.deb  g++-4.3_4.3.2.deb

---

### Post by sparky8251 on 2009-06-15
Thanks.

---

