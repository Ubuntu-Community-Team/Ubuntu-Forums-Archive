---
title: "Sun Virtualbox error"
date: 2010-01-12
forum: New to Ubuntu
---

### Post by mcnallyb on 2010-01-12
I was using Sun VirtualBox to run xp on my work pc for some very specific programs that I couldn't get to work in any other emulator or whatnot.

Today I tried to open it and run the XP SP2 virtual machine, and got an error. It tells me "Kernal driver not installed." How do I fix this error so I can get back to my XP programs for an hour?

Brad

---

### Post by drs305 on 2010-01-12
You may have recently upgraded linux kernels. I don't remember if the error message you cite is the one I used to get after a kernel update but it sounds familiar. I thought this was done automatically now but you can try running this command to see if it solves things:
```

sudo /etc/init.d/vboxdrv setup

```

---

### Post by studmf on 2010-01-12
You should be able to reinstall VB and it retain your guest OS, as always though make a backup first.

---

### Post by mcnallyb on 2010-01-12
> **drs305 said:**
> You may have recently upgraded linux kernels. I don't remember if the error message you cite is the one I used to get after a kernel update but it sounds familiar. I thought this was done automatically now but you can try running this command to see if it solves things:
```

sudo /etc/init.d/vboxdrv setup

```

#-o 
Worked perfect - and for some reason I just was stuck. I think it had more to do with the outside situation at my office more than me realizing how to do it. Thanks for the help...

Brad

---

