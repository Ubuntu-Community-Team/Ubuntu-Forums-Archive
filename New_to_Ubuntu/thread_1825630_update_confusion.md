---
title: "update confusion"
date: 2011-08-15
forum: New to Ubuntu
---

### Post by reptile1 on 2011-08-15
hi I have 2 main problems here.
I run xp home on 2 pc's and have installed ubuntu 10.04 on both from disc some updates applied over time. More updates applied to pc **No2**
I get choice of boot...but

On pc **No1** on boot up.... ubuntu or xp home and pc always boots xp unless i choose ubuntu.
Havn't used ubuntu on this pc for ages and so will have loads of updates for ubuntu but now wont boot when choose ubuntu? reboots instead when I select ubuntu. Why wont it load and what do i do about it without causing problems to the installed xp and data?
on pc **No2** different problem get boot up choice of loads of updated ubuntu generic and recovery.
   latest ...ubuntu with linux 2.6.32.33 generic
I think there are 6 or more other choices and also mem check  as well as xp home
Pc always boots to latest ubunu unless i choose otherwise.
Why is this one different and how do i correct the long list of possible boots without damaging windows xp or loosing any data?

Any advice would be of help 
thanks
rep

---

### Post by reptile1 on 2011-08-15
hi I have 2 main problems here.
I run xp home on 2 pc's and have installed ubuntu 10.04 on both from  disc some updates applied over time. More updates applied to pc **No2**
I get choice of boot...but

On pc **No1** on boot up.... ubuntu or xp home and pc always boots xp unless i choose ubuntu.
Havn't used ubuntu on this pc for ages and so will have loads of updates  for ubuntu but now wont boot when choose ubuntu? reboots instead when I  select ubuntu. Why wont it load and what do i do about it without  causing problems to the installed xp and data?
on pc **No2** different problem get boot up choice of loads of updated ubuntu generic and recovery.
   latest ...ubuntu with linux 2.6.32.33 generic
I think there are 6 or more other choices and also mem check  as well as xp home
Pc always boots to latest ubunu unless i choose otherwise.
Why is this one different and how do i correct the long list of possible boots without damaging windows xp or loosing any data?

Any advice would be of help 
thanks
rep

---

### Post by raja.genupula on 2011-08-15
in the pc 1 default loading os is xp . i dont know why its not booting ubuntu now 


2n pc you have several ubuntu options means everytime you update your kernel your grub will update so its include old kernel and as well as new kernel . if your new kernel working fine then you can happily remove old one by typing this ```
sudo gedit /boot/grub/grub.cfg
```. in that select carefully the old kernels ,(dont mess there , other wise you gonna have grub problems ) or put # before old kernels name in that file . so next time in grub you will not found those old one . 


give me the file , i will do the modification an i upload it. then you can do copy and paste .

---

### Post by Daveth on 2011-08-15
which version of Ubuntu are you running on your XP machines? 
Is it the same Ubuntu version on both PCs?
When you installed Ubuntu, did you put your /home (with all your documents, music, pictures etc) on a separate partition to the system files, or is it all on the same place, like your XP?
This sounds like a GRUB issue to me, but the version is important. Your XP data ought to be fine whatever.

---

### Post by drs305 on 2011-08-15
Threads merged. Please do not create multiple threads on the same issue.

---

### Post by reptile1 on 2011-08-17
Hi I am using 10.04 on both. Originally from disc but with some updates on pc1 and all updates on pc2
Thinking of installing new upgrade to 11.04 also
thanks
rep

---

### Post by reptile1 on 2011-08-22
Hi Guys still need help here before I do something daft and screw up my sys.
Dont want to reinstall ubuntu and find that it effects files setting on xp partition.
Really would like to try and understand what is going on here and then deal with it
Thanks
Rep

---

