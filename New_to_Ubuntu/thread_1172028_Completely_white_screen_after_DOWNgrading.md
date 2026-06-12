---
title: "Completely white screen after DOWNgrading"
date: 2009-05-28
forum: New to Ubuntu
---

### Post by jlbr21 on 2009-05-28
Hello,
So I had Jaunty 9.04 and hated it, it was too buggy for me, especially the graphics gave me many headaches. So I decided to downgrade to intrepid. 
Since I have my home partition separate, I did not format it or touched it during the install, and afterwards I restarted the computer and now everytime i do, after the system loads, the screen goes completely white.
I have tried to reconfigure xorg like 10 times and still nothing.

I will appreciate it very much if you could help. This is short of a tragedy to me!!

---

### Post by Didius Falco on 2009-05-28
> **jlbr21 said:**
> Hello,
So I had Jaunty 9.04 and hated it, it was too buggy for me, especially the graphics gave me many headaches. So I decided to downgrade to intrepid. 
Since I have my home partition separate, I did not format it or touched it during the install, and afterwards I restarted the computer and now everytime i do, after the system loads, the screen goes completely white.
I have tried to reconfigure xorg like 10 times and still nothing.

I will appreciate it very much if you could help. This is short of a tragedy to me!!

Not formatting your Home partition is probably the cause of your problem. All the configuration files are stored in Home, so you may have things that are incompatible with 8.10 in your Home partition.

A separate Home partition is great for reinstalls or upgrades, but the only good way to downgrade is to wipe it all and reinstall, including the Home partition.

The white screen sounds like a Video driver problem, so let's concentrate on that first.

What kind of Video card do you have, and what was the last driver you had installed in 9.04?

Regards,

Didius

What

---

### Post by jlbr21 on 2009-05-28
Hi Didius and thanks,

I have a nVidia8600GT video card, and the last driver I installed was the nvidia propietary driver 180 version. 

Thank you for answering.

---

### Post by Mark Phelps on 2009-05-28
Sorry ... but this is why we tell folks that there is no simple way to downgrade.

If you save off /home, reinstall using a lower version (including replaceing /home) and then SELECTIVELY copy things back, you MIGHT be able to pull off a downgrade without problems.  But that requires a lot of in-depth knowledge that most folks don't have.

---

### Post by jlbr21 on 2009-05-28
Got it, I have got to either install Jaunty again or make a complete install of Intrepid, wiping out everything.

Thanks.

---

