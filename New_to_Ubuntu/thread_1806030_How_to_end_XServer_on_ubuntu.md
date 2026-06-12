---
title: "How to end XServer on ubuntu"
date: 2011-07-17
forum: New to Ubuntu
---

### Post by GeneralShep on 2011-07-17
Please help! I need to install my driver! Please tell me EVERYTHING I need to do!!! I installed linix only today!

---

### Post by wildmanne39 on 2011-07-17
> **GeneralShep said:**
> Please help! I need to install my driver! Please tell me EVERYTHING I need to do!!! I installed linix only today!Hi, first look in additional drivers and see if there is a driver there for your card. You will need to be connected to the internet first.

If there is not one there run this command in a terminal.
```
lspci | grep VGA
```
and post the outcome  here by clicking on new reply and click # and paste the information between the brackets.

---

### Post by Wim Sturkenboom on 2011-07-17
The direct answer
```

sudo service gdm stop

```

---

### Post by GeneralShep on 2011-07-17
Okay, I have a driver in the additional drivers. Then I click "Activate" and then a few minutes later this pops up "SystemError: installArchives() failed"

Once I run that command in terminal this is results

02:00.0 VGA compatible controller: nVidia Corporation G92 [GeForce 9800 GT] (rev a2)


And when I typed in the thing the other guy told me to type in this popped up "Warning: Fake initctl called, doing nothing."

---

### Post by wildmanne39 on 2011-07-17
> **GeneralShep said:**
> Okay, I have a driver in the additional drivers. Then I click "Activate" and then a few minutes later this pops up "SystemError: installArchives() failed"

Once I run that command in terminal this is results

02:00.0 VGA compatible controller: nVidia Corporation G92 [GeForce 9800 GT] (rev a2)


And when I typed in the thing the other guy told me to type in this popped up "Warning: Fake initctl called, doing nothing."Hi, were you connected to the internet when you tried to install the driver?

---

