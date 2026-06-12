---
title: "intel integrated graphics VGA resolution problems with 9.10"
date: 2009-11-15
forum: New to Ubuntu
---

### Post by lordbyron on 2009-11-15
Hi. I have upgraded to 9.10 and as usual I have not retained my screen resolutions. am only able to do a maximum of 800x600 I have a Philips 22inch wide screen monitor (220cw8) and i Have 82865G integrated graphics controller. and I really have no idea how to get the larger screen sizes. can anyone help. Cheers

---

### Post by Meskarune on 2009-11-15
Type this into a terminal as user, then paste the result here. You may need to add a section to your xorg.conf for you monitor resolution.

```
cat /etc/X11/xorg.conf
```

---

