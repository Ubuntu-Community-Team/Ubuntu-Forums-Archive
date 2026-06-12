---
title: "Removing Wine - dpkg error. help please"
date: 2011-07-27
forum: New to Ubuntu
---

### Post by helenacoder on 2011-07-27
Hello,

I'm new to linux. and i went through a couple threads before i decided  to start this one.  Here's my problem... everytime i try to do

$ sudo app-get remove wine

i get this error:

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.

can someone help me with this?

also, note that I have already used different variations of  remove/uninstall/delete commands following instructions from several  threads here on how to completely remove wine.

Reasons for removing wine:

I installed an older version. 1.2.2 -- ubuntu software manager has a new/different version as far as i know. 
Thank you to anyone who is wiling to help.

---

### Post by jtarin on 2011-07-27
You have written ```
sudo app-get remove wine
```It should be ```
sudo apt-get remove wine
```

---

### Post by lisati on 2011-07-27
Have you run this from the terminal as suggested?
```
sudo dpkg --configure -a
```

---

### Post by helenacoder on 2011-07-27
> **lisati said:**
> Have you run this from the terminal as suggested?
```
sudo dpkg --configure -a
```

i did, nothing happens.

> **jtarin said:**
> You have written ```
sudo app-get remove wine
```It should be ```
sudo apt-get remove wine
```

I get the same error message with the corrected syntax. Thank you for catching it. Any other suggestions? Thank you.

---

### Post by sirgogo on 2011-07-27
Hmm, for silly quirks like this, you can open the Synaptic Package Manager via the gui (System-->Administration-->Synaptic Package Manager... I think). Find the package in question (wine) and right click --> Complete Removal.

But yeah, terminal is usually way better for more complex tasks. Plus, it makes sure stuff gets done (e.g. kill -9 proc#). Check if dpkg supports a --force parameter, with ```
man dpkg
```

---

### Post by helenacoder on 2011-07-27
> **sirgogo said:**
> Hmm, for silly quirks like this, you can open the Synaptic Package Manager via the gui (Accessories-->Administration-->... I think). Find the package in question (wine) and right click --> Complete Removal.


But yeah, terminal is usually way better for more complex tasks. Plus, it makes sure stuff gets done (e.g. kill -9 proc#). Check if dpkg supports a --force parameter, with ```
man dpkg
```


I'm effed. I get the same exact error on part 1 of what you suggested. plus this next line:


E:_cache->open() failed, please report

---

### Post by jtarin on 2011-07-27
Try  ```
sudo dpkg-reconfigure <packagename>
```

---

### Post by helenacoder on 2011-07-27
> **jtarin said:**
> Try  ```
sudo dpkg-reconfigure <packagename>
```


it didn't work sir..thanks for the suggestion though

---

### Post by helenacoder on 2011-07-27
i figured it out! thank you all!!!

---

### Post by sirgogo on 2011-07-28
Good to hear. Post your solution/what you were doing wrong, so your experience can be passed on to the next user with a similar problem! :P

---

