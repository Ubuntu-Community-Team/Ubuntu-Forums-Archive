---
title: "Update is hung, how to kill?"
date: 2011-01-26
forum: New to Ubuntu
---

### Post by Druegan on 2011-01-26
Just a bit ago I started installing a bunch of recommended updates through the Update Manager.. it downloaded all the packages, got to the "Applying Changes" window, and completely hung.

I have the following displayed in the "applying changes" window I cannot close, nor get rid of, and doesn't show on my taskbar..

```
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 222688 files and directories currently installed.)
Preparing to replace hpijs 3.10.2-2ubuntu2.1 (using .../hpijs_3.10.2-2ubuntu2_amd64.deb) ...
Unpacking replacement hpijs ...
```

It's dead.. it's hung...been staring at it doing nothing for a good 10 minutes..  Can anybody talk me through how to kill this process so I can try updating from the command line?

Thanks, 
   Druegan

---

### Post by Sh1n1g4m1 on 2011-01-26
You can go to de system monitor look for the ***id*** number that the update manager is using then open the console and type
```
sudo kill ***id***
```the ***id*** is the one that you found in the system monitor

Hope i was of any help

---

### Post by Druegan on 2011-01-26
Thanks, got it sorted :)

---

### Post by Sh1n1g4m1 on 2011-01-26
Don't forget to put solve on the post title

---

