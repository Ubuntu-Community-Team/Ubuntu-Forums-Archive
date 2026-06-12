---
title: "Trouble logging in under Kubuntu 10.04"
date: 2010-09-08
forum: New to Ubuntu
---

### Post by Nephtys on 2010-09-08
Hi,

I use Kubuntu 10.04 on an E-machines laptop. After I last logged and switched off, kubuntu did a routine check of my hard drive when I switched back on the next day. Ever since, I am unable to log in.

I know there is no trouble with my keyboard: I checked by typing my password into the username box. Also, if I try a wrong password the boxes go red instantly, whereas with the right password, the mouse icon turns into a cross and then into the time icon before returning me to the login screen.

A friend recommended that I try logging into recovery mode and running dpkg, which I did to no avail.

Any other plans would be highly appreciated. Thanks.

---

### Post by dmizer on 2010-09-09
Try logging into recovery mode again. Select the netroot option.

See if you can log in as yourself from the netroot prompt like so
```
su nephtys
```
replace <nephtys> with the username you actually use to log into your laptop.

If this is successful, try running this command
```
startx
```

---

### Post by Nephtys on 2010-09-19
Step 1 worked but step 2 didn't. After some more fiddling about, we (= dmizer and I) realized that the trouble merely stemmed from my hard drive being full to bursting.

After opening up some space and running ```
startx
``` again, everything worked fine. I'm removing more useless stuff now to clear up space on my machine.

Thanks for the help.

---

