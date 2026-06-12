---
title: "Nvidia Driver"
date: 2009-05-09
forum: New to Ubuntu
---

### Post by Chris_k0818 on 2009-05-09
So I boot Ubuntu 9.04 and try out some stuff to find out that my video driver won't work. I tried the restricted hardware drivers and it's not listed there. I have tried downloading it many different ways and it still won't work. Someone help me please! Nothing will work without it.

---

### Post by Didius Falco on 2009-05-09
It may be that your card was dropped to a legacy list, but to determine that, we need to know what video card you have.

Type ```
lspci | grep VGA
``` in Terminal and paste the output into your next post. That is a "pipe" not an l or I in after lspci - the pipe is usually the uppercase part of the \ key.

Regards,

Didius

---

### Post by Chris_k0818 on 2009-05-09
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)

---

### Post by Didius Falco on 2009-05-09
Compiz still has that card blacklisted:

[http://wiki.compiz-fusion.org/Hardware/Blacklist](http://wiki.compiz-fusion.org/Hardware/Blacklist)

However, there are some unofficial hacks people are using to get around it. I'm not endorsing these hacks, and only you can decide if you want to try them on your computer.

Here are links to the relevant information:

[http://ubuntuforums.org/showpost.php?p=7142974&postcount=5](http://ubuntuforums.org/showpost.php?p=7142974&postcount=5)

[http://ubuntuforums.org/showthread.php?t=1076014](http://ubuntuforums.org/showthread.php?t=1076014)

[http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)

[http://ubuntuforums.org/showpost.php?p=7132843&postcount=5](http://ubuntuforums.org/showpost.php?p=7132843&postcount=5)

I hope this helps...

Regards,

Didius

---

### Post by Chris_k0818 on 2009-05-09
None of that worked sadly. I'll have to have a friend look at it I guess. Unless of course you have some more suggestions. I'm a huge newb when it comes to ubuntu so the more detailed the instructions the better. Thanks.

---

