---
title: "difficulty booting"
date: 2010-02-01
forum: New to Ubuntu
---

### Post by baddnady23 on 2010-02-01
While updating my ipod with rhythmbox, the system (ubuntu 9.10) froze and required a hard reset.  I unpluged my ipod and restarted the computer.  However, now when it gets to the boot screen, it stalls out saying there is a problem with the fstab.  When hitting control-d to get to a terminal screen i dont know what to do so I exit it. 

After exiting, the screen flashes quickly saying that there was a problem with the swap mounting.  Any ideas anyone?  Thanks!

---

### Post by samantha_ on 2010-02-01
> **baddnady23 said:**
> While updating my ipod with rhythmbox, the system (ubuntu 9.10) froze and required a hard reset.  I unpluged my ipod and restarted the computer.  However, now when it gets to the boot screen, it stalls out saying there is a problem with the fstab.  When hitting control-d to get to a terminal screen i dont know what to do so I exit it. 

After exiting, the screen flashes quickly saying that there was a problem with the swap mounting.  Any ideas anyone?  Thanks!

its a bug thats has existed for some time. The argument is still going on about wether or not it should be automatic....
after pressing control +d, run
```

sudo fsck -y
```

---

