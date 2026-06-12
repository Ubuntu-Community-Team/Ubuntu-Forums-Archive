---
title: "setting resolution locks it up"
date: 2008-12-06
forum: New to Ubuntu
---

### Post by tool88 on 2008-12-06
hi im really new to this i installed ubuntu and installed the kde destop everry thing went fine until i set my resolution to 1024x768 now when i log onto kde it loads flickers black for a second and then loads a locked up os. im using a older ati card 5800 if any one can help is gratly appreciated

---

### Post by Joeb454 on 2008-12-06
Do you have the video drivers for your card installed?

---

### Post by tool88 on 2008-12-06
i thought they were like i said i just installed it did my updates and then changed my resolution i cant get into kde without it locking up to check but when i go to log on ubuntu normally it shows my ati drivers installed

---

### Post by tool88 on 2008-12-09
ok so it still locks up on me so i tried xorg ati drivers and now i lost gui for log in so what should i do?

---

### Post by Tatty on 2008-12-09
```
xfix
``` should set your graphics back to as they were before.

I dont think ATI supports cards that old with their proprietry drivers anymore, so you will have to run with the open source drivers.

Try setting your colour depth to 16, it sounds like your card cant handle 1024x768x24

---

### Post by tool88 on 2008-12-09
i was wrong the 5800 is in one of my other computers this one has the 9200se in it not that it is much newer. so how do i go about doing that ive tried sudo apt-get remove. and what drivers should i use for the ati that i have that would work the best. also thanks for the replys

---

### Post by Tatty on 2008-12-09
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)  according to this page "The 'fglrx' driver does not support cards earlier than the 9500".  So you will have to stick with the open source drivers for now.

---

### Post by tool88 on 2008-12-10
thanks for getting me back on track and slowing the learning curve. but i still have the problem of my resolution in ubuntu i can get my 1024x768 while when i change sessions in kde it locks up on me every time dosnt ubuntu and kde use the same drivers?

---

