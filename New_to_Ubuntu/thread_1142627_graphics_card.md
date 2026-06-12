---
title: "graphics card"
date: 2009-04-29
forum: New to Ubuntu
---

### Post by nayeem007 on 2009-04-29
Hello
I have installed ubuntu 9.04 on my studio xps 1340 laptop. It doesnt support my graphics card nvidia 9400 g.What can I do?Im just a kid in linux.Plz give me advice.

---

### Post by northern lights on 2009-04-29
The 180.XX.XX version of the nvidia driver should support this.

```
sudo apt-get update && sudo apt-get upgrade && sudo apt-get install nvidia-glx-180
```

---

### Post by nayeem007 on 2009-04-29
Thanks brother for ur advice
Brother Im afarid that is that version will really support my card NVIDIA GEFORCE 9400M G. Bcoz many users posted that their card werent supported perfectly. So plz assure me.

---

### Post by kpkeerthi on 2009-04-29
> **nayeem007 said:**
> Hello
I have installed ubuntu 9.04 on my studio xps 1340 laptop. It doesnt support my graphics card nvidia 9400 g.What can I do?Im just a kid in linux.Plz give me advice.

What do you mean not supported? Check in System -> Admin -> Hardware Drivers. If it is listed there, just click on the Activate button.

---

### Post by nayeem007 on 2009-04-29
I mean when I set high visual effect from desktop background, the operation cant be accomplished. There is nothing in my hardware driver list

---

### Post by ozzyprv on 2009-06-05
I have a similar problem, the new drivers wouldn't install.
kp, you are helping me with that [elsewhere]("http://ubuntuforums.org/showthread.php?p=7404567#post7404567")

Does that have to do with the SLI feature of the graphic card?

Thanks.

---

