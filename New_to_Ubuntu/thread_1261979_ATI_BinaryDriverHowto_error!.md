---
title: "ATI BinaryDriverHowto error!"
date: 2009-09-09
forum: New to Ubuntu
---

### Post by hungry bunny on 2009-09-09
Hello,

I'm having problems with my ATI graphics card and the proprietary drivers. I know this issue is well covered but after searching and trying for hours I have resorted to your help.

- I have Ubuntu 8.04

- lspci | grep VGA reveals:

06:00.0 VGA compatible controller: ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)

My problem is that when I look in System -> Administration -> Hardware drivers I see that I have an ATI Fire GL driver that is enabled but not in use.

I have tried to use the BinaryDriverHowtoATI community documentation but when i follow the steps to install the fglrx drivers I get the error 

insmod: error inserting '/lib/modules/2.6.24-16-generic/volatile/fglrx.ko': -1 Operation not permitted

I have semi-decent graphics as it is (fglrx yields about 1400fps) but I would like to get my desktop effects working because when they are enabled my screen goes really funky, also it would be really great to get the most out of my hardware.

I'm a new Ubuntu user so if you could "go slow" it would be appreciated.

Thanks very much

---

### Post by jimsheep on 2009-09-09
you are likely already doing this, but ensure you preceed all commands with

```
sudo
```

:)

---

