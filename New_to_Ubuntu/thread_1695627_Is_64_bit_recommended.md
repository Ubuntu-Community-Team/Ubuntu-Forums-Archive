---
title: "Is 64 bit recommended?"
date: 2011-02-26
forum: New to Ubuntu
---

### Post by rhuse on 2011-02-26
I'm about to install ubuntu again and switch to it full time. But some of the recommendations got me confused. I have a laptop (amilo pro v3405) with a core 2 duo t5200 64 bit processor. Is there any reason why I should not pick the 64 bit version of ubuntu?

I ask because the download site ([http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)) lists 32 bit as recommended but the community wiki ([https://help.ubuntu.com/community/32bit_and_64bit](https://help.ubuntu.com/community/32bit_and_64bit)) says "Unless you have specific reasons to choose 32-bit, we recommend 64-bit.".

(I have searched but the threads I have come up with are a couple of years old and I guess things might have changed ie. more 64 bit compatible software)

---

### Post by EpiLePTiC FaiRY on 2011-02-26
It might recommend 32 bit because you're running a 32 bit OS at the moment. If you have a 64 bit CPU then install the 64 bit OS. You may need to fiddle to get 64 bit flash installed but the 64 bit instruction set means you can install more than 4GB of RAM (if your motherboard supports it) and that is a good thing!

---

### Post by CharlesA on 2011-02-26
The ubuntu site "recommends" 32-bit since it will work on virtually all computers. Not every machine has the ability to run 64-bit, but it's getting there, as most (if not all) new machines have 64-bit processors.

---

### Post by rhuse on 2011-02-26
Thank you for your answers! (the community is a big reason for the switch)

---

### Post by u-slayer on 2011-02-26
> **CharlesA said:**
> The ubuntu site "recommends" 32-bit since it will work on virtually all computers. Not every machine has the ability to run 64-bit, but it's getting there, as most (if not all) new machines have 64-bit processors.

I'm sorry, but this is getting ridiculous. The majority of computers sold today have at least 4GB of ram. In a couple years you won't even be able to buy one with less than 4GB. The change to 64 bit has been coming for many years now and I think it's safe to say now that it's here. It's better to start using it now, then be forced to upgrade in a couple years.

---

### Post by pi.boy.travis on 2011-02-26
I've been using the 64-bit kernel since 8.04, it's been fine for me.

---

### Post by CharlesA on 2011-02-26
> **u-slayer said:**
> I'm sorry, but this is getting ridiculous. The majority of computers sold today have at least 4GB of ram. In a couple years you won't even be able to buy one with less than 4GB. The change to 64 bit has been coming for many years now and I think it's safe to say now that it's here. It's better to start using it now, then be forced to upgrade in a couple years.
I agree, but I don't think it's going to be changed any time soon. See the [huge thread in Recurring.]("http://ubuntuforums.org/showthread.php?t=1526391")

In any case, if you've got 3GB of RAM or more, the installer will install the PAE kernel, so you can access all your memory.

---

### Post by Spyderkid on 2011-02-26
is there a command you can run to check if you have a 32/64bit processor

---

### Post by CharlesA on 2011-02-26
> **Spyderkid said:**
> is there a command you can run to check if you have a 32/64bit processor
Run this:

```
cat /proc/cpuinfo
```

If it says "lm" under flags, it has 64-bit support.

See [here]("http://www.brandonhutchinson.com/Understanding_proc_cpuinfo.html").

---

### Post by pi.boy.travis on 2011-02-26
> **Spyderkid said:**
> is there a command you can run to check if you have a 32/64bit processor

It's in System Monitor, I believe.

---

### Post by kroq-gar78 on 2011-02-26
> **CharlesA said:**
> Run this:

```
cat /proc/cpuifo
```

If it says "lm" under flags, it has 64-bit support.

See [here]("http://www.brandonhutchinson.com/Understanding_proc_cpuinfo.html").

I'm not sure if that was a typo or if that's how it is in 10.04, but in 10.10 for me it's
```
cat /proc/cpuinfo
```

---

### Post by CharlesA on 2011-02-26
Yep, Typo ftl. =/

---

