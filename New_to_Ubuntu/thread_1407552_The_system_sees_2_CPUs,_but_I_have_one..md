---
title: "The system sees 2 CPUs, but I have one."
date: 2010-02-15
forum: New to Ubuntu
---

### Post by Julita on 2010-02-15
Is it normal? What should I do? The system labels it as CPU0 and CPU1, and "they" have different cpufreq-info... I needed to cpufreq-set, and I have changed "both of them," and now "they" have similar parameters. It's all weird because in my System Monitor, there are two CPUs with different load... Please, help!

---

### Post by noobie1 on 2010-02-15
Do you have dual core processor?

---

### Post by Evilhugbear on 2010-02-15
Maybe your processor has something called hyperthreading, which makes the cpu act like more than one core.

---

### Post by Julita on 2010-02-15
No-no! I have ASUS netbook with 1 Atom CPU of 1.67MHz :) Evilhugbear, you are right! I have looked at the specs of CPU, it, indeed, supports hyperthreading. Should I disable it? Can it be responsible for the system's overheating? The fan does not stop working... sensors shows 55-65 C.

---

### Post by Julita on 2010-02-15
Now I have found out that hyperthreading is not enabled in ubuntu by default, and the "duality" just indicates the capability of the CPU... Thanks for the tip about hyperthreading. Never knew about it!

---

