---
title: "E: _cache-&gt;open() failed, please report."
date: 2009-02-25
forum: New to Ubuntu
---

### Post by alanfang on 2009-02-25
Whenever I try to update or use the package manager I get this message preventing me from doing so. Does anyone have any idea how to resolve this. Thanks.

---

### Post by Partyboi2 on 2009-02-25
Can you please open a terminal (Applications>Accessories>Terminal) and post the output to
```
sudo dpkg --configure -a
```

---

### Post by alanfang on 2009-02-25
I get a pop up window about moblock-control and no text return I can see.

---

### Post by alanfang on 2009-02-26
anyone?

---

### Post by kansasnoob on 2009-02-26
Please be certain that no other package manager is running, that is be sure that Synaptic, Update Manger, etc. are closed then in terminal run:

```
sudo dpkg --configure -a
```

Then post the full output.

---

### Post by jre on 2009-02-28
Confirm the moblock-control dialog!
See here: [https://help.ubuntu.com/community/MoBlock#I%20tried%20to%20install%20MoBlock%20but%20I%27m%20stuck%20on%20a%20screen%20with%20a%20Moblock%20warning](https://help.ubuntu.com/community/MoBlock#I%20tried%20to%20install%20MoBlock%20but%20I%27m%20stuck%20on%20a%20screen%20with%20a%20Moblock%20warning)

---

