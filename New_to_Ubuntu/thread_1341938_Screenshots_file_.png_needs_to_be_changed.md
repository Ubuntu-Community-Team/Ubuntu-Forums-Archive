---
title: "Screenshots file .png needs to be changed"
date: 2009-11-30
forum: New to Ubuntu
---

### Post by trucker33377 on 2009-11-30
Hi Can one change to default file ex. .png to a .tga on a screenshot?

If not how would i do this for a number of screenshots, batch convert?
right now i am doing it 1 at a time a bit slowwwwww

---

### Post by mörgæs on 2009-11-30
If you go for batch convert, there are a lot of applications for that purpose.

I have used XnView with good results, but I don't remember which formats it could handle.

---

### Post by conehead77 on 2009-11-30
1. install imagemagick
2. open a terminal, go to the folder with your screenshots and type:
```
mogrify -format tga *.png
```

---

### Post by trucker33377 on 2009-12-04
> **conehead77 said:**
> 1. install imagemagick
2. open a terminal, go to the folder with your screenshots and type:
```
mogrify -format tga *.png
```

I have that installed but have never gotten it to do anything for me. i redid them with gimp. 1 at a time

---

