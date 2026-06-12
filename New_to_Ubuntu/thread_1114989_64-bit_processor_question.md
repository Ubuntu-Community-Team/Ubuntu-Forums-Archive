---
title: "64-bit processor question"
date: 2009-04-03
forum: New to Ubuntu
---

### Post by erunamo114 on 2009-04-03
Hello, my fellow Linux brothers and sisters. I have a general question. I have an AMD 64-bit processor in my computer, and I have recently installed Ubuntu and am somewhat new to everything. I have been having several compatibility problems with different things. It seems like each thing I try to do I have problems with, even watching DVDs on Totem player or Mplayer. Is it normal to have a lot of problems with a 64-bit processor as opposed to a 32-bit? I am getting a lap top soon and giving away my desktop so if the processor is the main issue I will make sure to have a 32-bit because it's been driving me crazy. I really want to keep using Ubuntu though. What do you guys think?

---

### Post by taurus on 2009-04-03
You need to install media codecs on your machine first.

```
sudo apt-get update
sudo apt-get install ubuntu-restricted-extras
```

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

And if you want to watch a DVD on your machine, you need libdvdcss2.

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by SuperSonic4 on 2009-04-03
As well as the above you may want to turn off desktop effects, your CPU may get overloaded and produce choppy video

---

### Post by empty_spaces on 2009-04-03
Most of the initial issues with 64bit such as flash and java have long since been sorted out. If you have a 64bit processor, then 64bit ubuntu is highly recommended.
The issues you are facing are almost certainly not due to the OS being 64bit.
I would recommend that you make a separate post for each of your specific issues in the appropriate section where someone might be able to point you in the right direction.

---

