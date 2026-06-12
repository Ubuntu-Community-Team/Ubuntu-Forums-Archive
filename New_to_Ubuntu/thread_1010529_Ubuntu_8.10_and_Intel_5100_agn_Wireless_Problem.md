---
title: "Ubuntu 8.10 and Intel 5100 agn Wireless Problem"
date: 2008-12-13
forum: New to Ubuntu
---

### Post by uniqueumang on 2008-12-13
Hello Everyone,
Ok I have installed Ubuntu 8.10 on my laptop , and my wireless doesn't work, what I mean by dosen't work is that I am not able to scan and connect to the preffered connection. Have a look at the attachment picture. Please Help. Thanks

---

### Post by bsharp on 2008-12-13
Could you post the output of:
```
ifconfig
```

and

```
lspci | grep Ethernet
```

---

### Post by uniqueumang on 2008-12-13
Umm...I currently uninstalled ubuntu 8.10 . I have both 32 bit and 64 bit. Does it matter which one I install? It is unfortunate that  only option internet option available is wireless. But I back asap.

---

### Post by bsharp on 2008-12-13
If you have a 64-bit processor, go ahead and install the 64-bit version. I've been using 64 bit for 2 year now and they've worked out the problems an average user will run into.

Basically it isn't detecting your wireless card, and the above commands are to find out what model you have so I can help direct you to the correct driver.

---

### Post by uniqueumang on 2008-12-13
> **bsharp said:**
> If you have a 64-bit processor, go ahead and install the 64-bit version. I've been using 64 bit for 2 year now and they've worked out the problems an average user will run into.

Basically it isn't detecting your wireless card, and the above commands are to find out what model you have so I can help direct you to the correct driver.

Thanks I would just do that and reply back

---

### Post by uniqueumang on 2008-12-13
[UPDATE] Ok this is quite weird, I am currently in Live cd mode of ubuntu 8.10 x64 bit, and everything worked , including wireless. I am attaching the screenshot.

---

### Post by bsharp on 2008-12-13
Well there you go!

When you install it than it should work from the vanilla install without any fiddling around.

---

### Post by uniqueumang on 2008-12-13
U know I went from ubuntu 7.10( x64) to 8.04 (x64)and 8.04(x64) to 8.10(x64), I then tried x32 bits. I have compiled latest kernel so that it can work , and yet had no sucess. I am not sure how it is working now. I think something nice happened when I installed Mandriva 2009. Yes Wireless worked with Mandriva , but not with opensuse. I am not sure how it is working.

---

