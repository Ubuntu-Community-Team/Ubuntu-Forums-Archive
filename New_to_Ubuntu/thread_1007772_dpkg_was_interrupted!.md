---
title: "dpkg was interrupted!"
date: 2008-12-10
forum: New to Ubuntu
---

### Post by blueshead on 2008-12-10
now i can't update, etc.. can anyone help?

---

### Post by SuperSonic4 on 2008-12-10
Did you get a specific error code? Normally I believe it to be
```
sudo dpkg --configure -a
```

---

### Post by blueshead on 2008-12-10
I got this..    E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

but when I put 'dpkg --configure -a' into the terminal.. It asks for a super user. I'm only a few weeks into Ubuntu.. so very n00b.. The terminal is fine as I'm an OSX user.. how go I find out what my super user p/w is?  and ty for your help..

---

### Post by Joeb454 on 2008-12-10
Run the command in post 2. Sudo is used in Ubuntu to give you super user permissions on the system. I believe this can also be used in OS X :)

```
sudo dpkg --configure -a
```

---

### Post by blueshead on 2008-12-10
ok i did that.. i now have this..

Processing triggers for man-db ...
Processing triggers for doc-base ...
Processing 2 added doc-base file(s)...
Registering documents with scrollkeeper...
mark@blueshack:~$ 


its stopped at this..and i have the blinking black box at the end.. what should i do now?  and thankyou for guiding me through this!  i know its late at night over there and early here in new orleans.. hoists a beer to you..   AHH  It seems update manader is working again and installing my packages.. i'll be back soon.. many thanks..there is a big difference going on now!

---

### Post by JoshuaRL on 2008-12-10
It seems that it worked.  You also might try these commands, just to clean stuff out.

```

sudo apt-get install -f
sudo apt-get update
sudo apt-get upgrade
sudo apt-get autoclean

```

The first attempts to fix any broken packages, much like the dpkg command did.  The second and third attempt to update your system, and the last cleans out any leftover files in the local repository.  Should make sure everything runs nice and slick.

---

### Post by blueshead on 2008-12-10
Thank you guys!  For helping me with Ubuntu.. 

thank you very much.. it looks like I'm off and running.. opens beer

---

