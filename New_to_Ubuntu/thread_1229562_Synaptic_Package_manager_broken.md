---
title: "Synaptic Package manager broken ?"
date: 2009-08-02
forum: New to Ubuntu
---

### Post by INTENSETUX on 2009-08-02
Hi

I have attempted to install TimeVault in Ubuntu 9.4 and when logging out and then back in again my keyboard and mouse stopped responding.

I restarted the computer from the power button and all seemed to be fine again but when i tried to use Synaptic Package manager i recieved the following error message that said

 '' E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I then ran this command in the terminal after which the computer reboots and the keyboard and mouse are unresponsive again

Any help would be appreciated

Thanks , Daz

---

### Post by llamabr on 2009-08-02
So you ran:

```
sudo dpkg --configure -a
```

and it finished correctly?  Did it reboot automatically, or you did it?

Finally, try using apt-get to remove timevault, and see if that corrects your problem.  We can then verify that it's the source of the errors.

---

### Post by INTENSETUX on 2009-08-02
Thanks for the reply

Tried apt get and return'' Package timevault is not installed, so not removed''

Beforehand it was listed in Applications/System Tools and now it isnt which has cured Synaptic Manager :D , i'm guessing a screw up during installation caused all this

Thanks for your help , much appreciated

Daz

---

