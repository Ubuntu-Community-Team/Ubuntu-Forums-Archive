---
title: "yeah"
date: 2009-12-23
forum: New to Ubuntu
---

### Post by pvplahing138 on 2009-12-23
sorry for bad  title
ok i had one bad sector
then i installed win xp
then i tried to install ubuntu 
and quess what my disck what healty
so is this normal that ad sector will repair it self\?

---

### Post by mgranet on 2009-12-23
Bad sectors will accumulate over the lifetime of a drive for a variety of reasons. It only becomes a concern when larger numbers of sectors start failing in short order. You can install smartmontools to monitor the situation, if you are concerned.```
sudo apt-get install smartmontools
``` 

To run (in a terminal): sudo smartctl -HAc /dev/yourdrivedesignationhere

---

