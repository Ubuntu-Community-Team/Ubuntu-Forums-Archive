---
title: "No Sound in Alienware Area-51 M15x"
date: 2010-05-14
forum: New to Ubuntu
---

### Post by Stobei117 on 2010-05-14
Hello All,
I Most recently switched to the world of Ubuntu after a friend of mine was telling me how amazing it is, and i do completly agree and love it. Though i have a few questions and need a little help :)
1. My speakers do not work, my headphones do however work  when i plug them in.
2. I need to run Visual Studio for my Programing class, tried installing with Wine...gave me a error message :/ Or is there a another option?
3. Is there a way to get the color changing program for my lit keyboard. 

This is my system here:
[http://computershopper.com/laptops/reviews/alienware-area-51-m15x-laptop](http://computershopper.com/laptops/reviews/alienware-area-51-m15x-laptop)

Thanks

---

### Post by -humanaut- on 2010-05-14
1) Click the Volume icon and then click preferences and make sure Front PCM etc... Aren't Muted. 

2) Visual Studio I'm not familiar with is it for coding in Visual Basic? You might need to dual-boot or possibly load windows in a VirtualBox for it.

If I remember correctly Dell bought out Alienware you could check there forums about your keyboard because I honestly Don't know. (Dell has pretty decent Linux support for an OEM)

---

### Post by lidex on 2010-05-14
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
Please post text output using code tags. *_Also helpful is the make/model of your PC/Laptop._*

---

### Post by Stobei117 on 2010-05-15
Thank you  both, was able to fix it from dells fourms. THanks much :D

---

### Post by lidex on 2010-05-16
> **Stobei117 said:**
> Thank you  both, was able to fix it from dells fourms. THanks much :D

Awesome. Could you post the fix, or a link to it, and mark the thread as solved using 'Thread Tools' up top please?

---

