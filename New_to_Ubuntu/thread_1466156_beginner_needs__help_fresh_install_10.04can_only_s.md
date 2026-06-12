---
title: "beginner needs  help fresh install 10.04can only start fail safe graphics mode"
date: 2010-04-30
forum: New to Ubuntu
---

### Post by bill1357 on 2010-04-30
i have an intel  855gme chipset  that worked fine in 9.10 , but now it,s not recognized. I have no clue how to fix this as I am an aabsolute beginner to linux .any help would be much appreciated thanks.

---

### Post by Rasa1111 on 2010-04-30
hi bill, welcome, ...

2 of us are having the same problem in this thread...
[http://ubuntuforums.org/showthread.php?t=1465883](http://ubuntuforums.org/showthread.php?t=1465883)

no idea how to fix it yet, but we can figure it out together...
im sure... eventually... lol

 all works fine now, 
but low graphics mode cant be changed... 

 but it is only happening to a few it seems... 

hmm.. patience we must have.. lol

 good luck bro, all of us in low graphics mode can use it. :)
thankfully for me though, I only ran from the liveCD, i didnt do an install yet..
wheww! lol

p..s.. thanks for starting the thread!! :D

---

### Post by bill1357 on 2010-04-30
Tanks for pointing me to that thrad. This is what worked for me.

echo options i915 modeset=1 | sudo tee /etc/modprobe.d/i915-kms.conf
sudo update-initramfs -u


thanks again bill

---

### Post by Rasa1111 on 2010-04-30
:) very good. 
happy to hear it!

---

### Post by hot_franks_49_cents on 2010-05-01
Thanks, Bill.  My old IBM x40 was having the same problem and that modprobe addition cured it right up.

---

### Post by leendrt on 2010-05-05
Thanks Bill, 
had the same problem with my old Dell Latitude X300 and it worked for me as well.

---

### Post by Flower_Mike on 2010-05-27
Wow, I spent ages trying to solve this problem. This worked straight away.

Can someone explain how it fix's the problem.

Just incause anyone else is having the same problem I was using a Toshiba Satellite A10 with an INTEL Pent4 chip.

**EDIT**: OK, so initially I could not boot into graphical mode at all. But I could use recovery mode and boot into fail safe graphics. So I entered the commands above that worked for Bill. Then I rebooted and it went straight into graphical mode. Then after a couple of restarts it comes up with the error saying it can only start in fail safe graphics mode. Any ideas how I can get it to boot properly?

---

