---
title: "failed to find file or catalogue"
date: 2010-01-29
forum: New to Ubuntu
---

### Post by zansiball on 2010-01-29
i try to do this simple steps.

> mkdir srcds_l
cd srcds_l
wget [http://www.steampowered.com/download/hldsupdatetool.bin](http://www.steampowered.com/download/hldsupdatetool.bin)
chmod +x hldsupdatetool.bin
./hldsupdatetool.bin

when i try to do ./hldsupdatetool.bin it says it cant find the file or catalogue. what am i doing wrong?

the file is clearly downloaded and located in the folder. im using ubuntu server 64 bit.

---

### Post by zansiball on 2010-01-29
i solved it by running apt-get install lib32gcc1

---

