---
title: "Less memory is shown wonder why ?"
date: 2009-07-02
forum: New to Ubuntu
---

### Post by sadaruwan12 on 2009-07-02
Hi,

Well I managed to customize and install conky grate system info tool and it's working but in my PC I've around 3072Mb's of RAM (3Gb). But in conky maximum amount of memory available is 0.99Gbs I'm not using any shard VGA card but what I wonder is where is my other free memory has gone. Is there a way to fix this and I'm using hardy haron 8.04 LTS 32Bit I used top to see this a program hiccup but that also show around 1Gb of memory what happened to my memory can some one help THX.

---

### Post by credobyte on 2009-07-02
Not sure if that's the case, but .. take a look at this post : [http://ubuntuforums.org/showpost.php?p=7546595&postcount=7819](http://ubuntuforums.org/showpost.php?p=7546595&postcount=7819)

---

### Post by halitech on 2009-07-02
in a terminal, what does
```
free -m
```give for info?

---

### Post by sadaruwan12 on 2009-07-02
> **halitech said:**
> in a terminal, what does
```
free -m
```give for info?

The out put is,

```
sinux@sinux-desktop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          1010        972         38          0         16        370
-/+ buffers/cache:        584        425
Swap:         5859          0       5859
sinux@sinux-desktop:~$ 

```

---

### Post by halitech on 2009-07-02
its only seeing 1gig of ram. Do you have an Ubuntu live cd you could boot from and run the memtest86+? It will tell you if there is a problem with the ram

---

### Post by sadaruwan12 on 2009-07-02
> **halitech said:**
> its only seeing 1gig of ram. Do you have an Ubuntu live cd you could boot from and run the memtest86+? It will tell you if there is a problem with the ram

OK thx but I've windows that shows me full 3Gbs and even from the BIOS it shows 3Gb.

---

### Post by halitech on 2009-07-02
ok, you didn't mention that earlier. I know there is a limit in the 32bit linux but I'm pretty sure its 4gig so not sure why its only showing 1gig.

whats the output of
```
uname -a
```

---

### Post by sadaruwan12 on 2009-07-02
> **halitech said:**
> ok, you didn't mention that earlier. I know there is a limit in the 32bit linux but I'm pretty sure its 4gig so not sure why its only showing 1gig.

whats the output of
```
uname -a
```

The out put is,

```
sinux@sinux-desktop:~$ uname -a
Linux sinux-desktop 2.6.24-24-generic #1 SMP Tue Jun 30 20:28:53 UTC 2009 i686 GNU/Linux
```

---

### Post by halitech on 2009-07-02
kernel 2.6.24 on i686 should show 4gig no problem. Have you checked recently (today) that windows and the bios are seeing all 3 gig?

---

### Post by sadaruwan12 on 2009-07-02
> **halitech said:**
> kernel 2.6.24 on i686 should show 4gig no problem. Have you checked recently (today) that windows and the bios are seeing all 3 gig?

No, But when the PC was booting it showed available memory as 3Gb. Hmmmmmmm


Yo, THX I got it solved my 2Gb RAM was loose from DIMM slot thats why it was showing as 1Gb now it's ok. THx every one. And specially you halitech

---

