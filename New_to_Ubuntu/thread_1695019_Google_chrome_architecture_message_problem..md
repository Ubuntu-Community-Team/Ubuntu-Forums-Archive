---
title: "Google chrome architecture message problem."
date: 2011-02-25
forum: New to Ubuntu
---

### Post by vnpifhf on 2011-02-25
Hello, I tried to install the google chrome browser but when it opens up into the software centre it says Wrong architecture 'amd64'.

I have an Amd phenom 64 bit so I do not see the problem.

Help?

---

### Post by Perfect Storm on 2011-02-25
But did you installed ubuntu 64-bit?
```
uname -a
```

---

### Post by vnpifhf on 2011-02-25
jay@jay-VPCEE2S1E:~$ uname -a
Linux jay-VPCEE2S1E 2.6.35-22-generic #33-Ubuntu SMP Sun Sep 19 20:34:50 UTC 2010 i686 GNU/Linux
jay@jay-VPCEE2S1E:~$

---

### Post by Perfect Storm on 2011-02-25
You're using 32-bit version of Ubuntu, so you need to get the 32-bit package of chrome.

If you're using 64-bit OS it should look something like this;
```
orion@universe:~$ uname -a
Linux universe 2.6.35-25-generic #44-Ubuntu SMP Fri Jan 21 17:40:44 UTC 2011 **x86_64 GNU/Linux**
orion@universe:~$ 

```

If you want to get'n'install Ubuntu 64-bit, you need to re-install with Ubuntu 64-bit version.

---

### Post by vnpifhf on 2011-02-25
but I recieved the CD from ubuntu, shouldn't it have done it automatically and chosen my system as 64 bit?

---

### Post by Perfect Storm on 2011-02-25
> **jahangir99 said:**
> but I recieved the CD from ubuntu, shouldn't it have done it automatically and chosen my system as 64 bit?

No, the CD that you can get through mail are all 32-bit. To have both 32-bit and 64-bit on same dics would require a DVD version to fit in. The 32-bit version ~640mb, the 64-bit version ~640mb.

---

### Post by vnpifhf on 2011-02-25
well I suggest that you put a sign up on the website that the version you send out is 32-bit, or make it a little clearer!
Don't you ship 64-bit CD's?

---

### Post by Perfect Storm on 2011-02-25
No, only downloadable form.

---

### Post by vnpifhf on 2011-02-25
Thanks anyway :( 
Back to 7 then...

---

