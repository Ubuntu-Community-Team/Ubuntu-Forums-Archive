---
title: "uninstalling in terminal"
date: 2009-09-03
forum: New to Ubuntu
---

### Post by Megatron3000 on 2009-09-03
hello, in the epic 'get your graphic card working'-saga, Automaton 26 pointed me to [http://ubuntuforums.org/showthread.php?t=1256855](http://ubuntuforums.org/showthread.php?t=1256855) , where the same issue is found. I want to try this solution, but before, when i installed the ati driver, my system wouldn't start up anymore, and -unexperienced as i am- i reinstalled everything.
 
 I suppose there is a way to just undo the installing of the ati-driver in recovery mode, by accessing a terminal, in case things go wrong again.  
 
 My guess is that 'sudo get-apt remove fglrx' would do the trick, but does that automatically bring me back to the default driver -which works, even though things aren't too pretty? thanks for helping me out!

---

### Post by MrWES on 2009-09-03
> **Megatron3000 said:**
> hello, in the epic 'get your graphic card working'-saga, Automaton 26 pointed me to [http://ubuntuforums.org/showthread.php?t=1256855](http://ubuntuforums.org/showthread.php?t=1256855) , where the same issue is found. I want to try this solution, but before, when i installed the ati driver, my system wouldn't start up anymore, and -unexperienced as i am- i reinstalled everything.
 
 I suppose there is a way to just undo the installing of the ati-driver in recovery mode, by accessing a terminal, in case things go wrong again.  
 
 My guess is that 'sudo get-apt remove fglrx' would do the trick, but does that automatically bring me back to the default driver -which works, even though things aren't too pretty? thanks for helping me out!

Reboot and hit the ESC button to get to the grub menu. Choose the recovery mode for the latest kernel (usually second from the top) and then navigate to the xfix option. Should do it.

Bill

---

### Post by wojox on 2009-09-03
You have to reset your xorg.conf:

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by Megatron3000 on 2009-09-03
thanks, i'll give it a try

---

### Post by Megatron3000 on 2009-09-03
but before that, wojox, do you mean i enter that after installing or after things go wrong, from the rescue terminal? from what i get now, my options are: 
 
a. everything turns out allright, sweet! 
b. everything stalls, in recovery mode i try xfix, if that does not work i 
-open a terminal, delete the ati driver 
-reconfig xorg 
 
 Right? or should i leave the deleting out?

---

### Post by Megatron3000 on 2009-09-03
okay, i ended up having to put up a fight with the drivers in text mode, but things seem to work more or less for now. Thanks!

---

