---
title: "phenom 9550 quad core issues"
date: 2011-04-25
forum: New to Ubuntu
---

### Post by spillage2 on 2011-04-25
Hi All.

Been having major issues with my cpu's working overtime. Even if I just leave the system monitor running only and maybe firefox then one or two of my cores can start working at 100% which sometimes are causing the system to run to a halt.

My fans also are suffering from this causing them the run very fast and making the whole system noisy as the tower is on my desk.



Running 10.04
4gb of ram so that should be fine..
Kernel 2.6.32-31-generic-pae
Gnome 2.30.2
GeForce 8600 GT
firefox 4

plus I'm running compiz but that never seems to show over 10%.

Although when it goes mad the resources list doesn't list anything running high..


Any ideas would be very helpful.

Cheers,

Spill.

---

### Post by K_45 on 2011-04-25
I'd crack open the case, and clean out the fans and case. I'd also re-apply some thermal paste and check the BIOS to ensure Cool N' Quiet is enabled.

---

### Post by spillage2 on 2011-04-25
Hi K_45,

I have recently renewed the thermal paste and although blowing out the crud might help a little its not the bad in there really.

I have just bolted on another large fan for more intake to see if that would help but so far its still as bad.

---

### Post by K_45 on 2011-04-25
Open up a terminal and enter 

```
top
```

Work for a bit, but what do you see hogging up your CPU cycles?

---

### Post by spillage2 on 2011-04-25
Ok left for a while with nothing really serious going on.

Then started system monitor and root for xorg started to climb.

Before the it was hitting at max 40% but normally around 25%. As soon as system monitor started  it climbed to double that to 80% so I killed it.


seems pointless to have a system monitor that kills my system.

---

### Post by K_45 on 2011-04-25
"Root for xorg"?

---

### Post by spillage2 on 2011-04-25
yep I have user "root" and the command "xorg"

as soon as system monitor starts it kills my cpu's.

---

### Post by K_45 on 2011-04-25
Hmmm, can you try a different task monitor?

```
sudo apt-get install lxtask
```

Does that one still cause problems?

---

### Post by spillage2 on 2011-04-25
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package lxtask is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package lxtask has no installation candidate

not sure 10.04 supports this.

installed conky and that seems fine showing cpu at 11% and xorg at about 9% but my fans are still running high. guess ill just have to live with it.

---

### Post by K_45 on 2011-04-25
Are there are any BIOS options you might adjust?

---

### Post by deconstrained on 2011-04-25
Have you tried sorting PID's by CPU resource consumption? In the "Processes" tab, click on "% CPU" and that should show you which processes are the biggest resource hogs.

---

