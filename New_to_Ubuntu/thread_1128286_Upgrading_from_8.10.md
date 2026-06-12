---
title: "Upgrading from 8.10"
date: 2009-04-17
forum: New to Ubuntu
---

### Post by Salgat on 2009-04-17
I would like to upgrade from 8.10 to the new release, but when I go to the update manager "update-manager -d" it doesn't show the new release. I went under software sources and made sure the updates were set to all normal releases, but it still doesn't show the option to upgrade. What do I need to do?

---

### Post by DJiNN on 2009-04-17
It's just a guess, but i would imagine that it's not available yet because they've only just released the RC version. As soon as the final release is available, you may find that it becomes available as an upgrade option.

Makes sense really, because they would get one hell of a mess allowing people to upgrade to Alphas, Beta releases etc. Better to just allow those that want to try out the early releases, to download their chosen ISO's and have a play, install, use VirtualBox or VMware etc. To use an early (Alpha, Beta) release as your everyday desktop, although fun, is somewhat risky and should be avoided if you want a stable working environment.

Only a couple of days to go before 9.04 is released..... not too long now. :)

DJiNN

---

### Post by Therion on 2009-04-17
Try using:```
  sudo aptitude update && sudo aptitude dist-upgrade && sudo aptitude dist-upgrade 
```

---

### Post by sadaruwan12 on 2009-04-17
Hi,

 Bro, Don't do it wait till it comes out as a final release don't rush in to installing Alpha, Beta and RC 'cos they are full of bug's if you still want to do it then it's up to you. But really it's not worth it 'cos the new release is very near so hold your horses.

---

