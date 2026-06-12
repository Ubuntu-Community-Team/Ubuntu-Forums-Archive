---
title: "getting my built in web cam to work"
date: 2009-11-11
forum: New to Ubuntu
---

### Post by Burningwater87 on 2009-11-11
my laptop is a toshiba sat. a505-s6960.  came with a built in 1.3 mp web cam.  i can't get it to work.  i downloaded cheese webcam booth, but it's not finding my cam.  am i missing a driver or something?  i'm using ubuntu 9.10 64 bit

thanks in advance

---

### Post by earthpigg on 2009-11-11
hi,

i have found that sometimes one webcam program will work fine, while others will not. search synaptic or software center for 'webcam' or 'web cam' and try a few. let us know how it works out.

---

### Post by Burningwater87 on 2009-11-11
hi,
i downloaded another program that seemed to be basically the same as cheese, but it didn't work either.  i'm a noob to unbuntu and linux in general.  i keep seeing video4linux pop up in the searches i've done.  is there something i need to do with that?

i've also come across a couple other problems that i can't seem to resolve.  

i can't play any flash game online and most of the time i don't have any control over any videos i watch on youtube, and i can't get any videos on other sites to even start(i'm guessing because youtube videos start automatically is the only reason i can watch them).  i downloaded the adobe flash listed in the ubuntu software application.  maybe it's the 32-bit one?  like i said, i'm running 64-bit 9.10.  i've tried a couple things i've found in other threads, but nothing has worked so far. maybe i should put these problems in another thread.

---

### Post by Burningwater87 on 2009-11-14
ok, so i've gotten it to work, so the webcam problem is solved.

---

### Post by sandyd on 2009-11-14
have you tried nspluginwrapper?

---

### Post by empty_spaces on 2009-11-14
> **Burningwater87 said:**
> ok, so i've gotten it to work, so the webcam problem is solved.

Please post what worked for you, so that it may help others with the same hardware

---

### Post by nicktuft on 2009-11-14
New to ubuntu and I also can't get my web cam to work.
It is a logitech 7500 and having asked logitech support if they could help with software they said it was not compatiable. I was wondering if any one had other ideas how I might get it to work. I want to use it with Skype.

---

### Post by sandyd on 2009-11-14
> **nicktuft said:**
> New to ubuntu and I also can't get my web cam to work.
It is a logitech 7500 and having asked logitech support if they could help with software they said it was not compatiable. I was wondering if any one had other ideas how I might get it to work. I want to use it with Skype.
read
[https://wiki.ubuntu.com/SkypeWebCams](https://wiki.ubuntu.com/SkypeWebCams)
it says it works out of the box.

try 
```

sudo echo "uvcvideo" >> /etc/modules

```
then restart your computer
if that still doesn't work, run 
```

ls /dev/video*

```

---

### Post by nicktuft on 2009-11-14
Thanks carlee will have a go tomorrow and let you know how it went.
Regards Nick R

---

### Post by Burningwater87 on 2009-11-14
not sure how i got mine to work.  ran a system update yesterday, and tried Cheese again today.  picked my cam right up, but i don't remember any of the updates having anything to do with my webcam...   sorry i can't offer any more help

---

