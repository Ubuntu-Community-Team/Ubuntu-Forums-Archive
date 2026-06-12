---
title: "3 options for ubuntu in grub"
date: 2011-03-10
forum: New to Ubuntu
---

### Post by amitpokhrel on 2011-03-10
I have 3 options for ubuntu in my grub.Before there were two but now when i restored the grub after installing windown there are 3 options. can anyone explain why it is happening and how can i reduce to 1 and which two should I remove??

---

### Post by akernan on 2011-03-10
One for each kernel version?  Run sudo update-grub to update the list.

---

### Post by ~Plue on 2011-03-10
those extra options would be older kernels. its recommended to keep at least the two most recent ones in case something goes wrong with the current one

you could follow the instructions here to remove the extra kernels >>> [http://ubuntuforums.org/showthread.php?t=1587462](http://ubuntuforums.org/showthread.php?t=1587462)

---

### Post by scouser73 on 2011-03-11
The best way to remove old kernels would be to install Ubuntu Tweak [http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

Once installed, you'll find it under **System Tools**, select it and it will open up then click on **Package Cleaner** and click on **Unlock** then click on **Clean Kernels** and a list of out-dated kernels will appear and then finally click on **Cleanup**.

---

