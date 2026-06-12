---
title: "How to split files into two halves?"
date: 2011-07-04
forum: New to Ubuntu
---

### Post by karthick87 on 2011-07-04
I have a 7.5 GB file which i would like to split into two halves and then i have to join it later. What commands i wanna use to do this task?

---

### Post by nzjethro on 2011-07-04
What kind of file? The steps for splitting/rejoining, and even whether or not it can be done will depend on the file type.

---

### Post by hsweet on 2011-07-04
To split (from terminal)

```
split -b4g bigfile littlefile
```

This will make a 4 gig and a 3.5.  Or do the math if you want to split in half exactly

To reassemble.  

```
cat littlefile* > newbigfile
```

It should not matter what is in the file, but I would try it out to be sure before I deleted the original

---

### Post by Wim Sturkenboom on 2011-07-05
> **nzjethro said:**
> What kind of file? The steps for splitting/rejoining, and even whether or not it can be done will depend on the file type.As shown in the post #3, that's not true. You can split any file to your liking.

---

### Post by nzjethro on 2011-07-05
> **Wim Sturkenboom said:**
> As shown in the post #3, that's not true. You can split any file to your liking.

Apologies, I was always taught that only some file types could be split. But I'm happily proven wrong by hsweet to increase my Ubuntu expertise. :D

---

### Post by karthick87 on 2011-07-05
It is showing an error,
```

karthick@karthick:/media/Datas/Extension List/Fedora$ split -b4g Fedora\ -\ 16.iso littlefile
split: 4g: invalid number of bytes
Try `split --help' for more information.

```

---

### Post by abybaddi on 2011-07-05
Try this its free and also for linux!!!

[HJSPLIT]("http://www.hjsplit.org/linux/")

---

### Post by Wim Sturkenboom on 2011-07-05
read man split
try *-b4000000* or *--bytes=4000000*

---

### Post by aeiah on 2011-07-05
> **karthick87 said:**
> It is showing an error,
```

karthick@karthick:/media/Datas/Extension List/Fedora$ split -b4g Fedora\ -\ 16.iso littlefile
split: 4g: invalid number of bytes
Try `split --help' for more information.

```

doesnt look like g is supported, only b, k and m. try -b4000m

---

### Post by karthick87 on 2011-07-06
Yeah that does the trick :) Thank you :)

---

### Post by Wim Sturkenboom on 2011-07-06
Please mark your thread as solved using the thread tools just above the first post on a page.

---

### Post by hsweet on 2011-07-06
From the man page .. G and GB are both valid, but g (lower case) is not.  My bad.


```
 SIZE may have  a  multiplier  suffix:  b  512,  kB  1000,  K  1024,  MB
       1000*1000,  M 1024*1024, GB 1000*1000*1000, G 1024*1024*1024, and so on
       for T, P, E, Z, Y.
```my bad.  should be gb for gig

---

### Post by nzjethro on 2011-07-06
> **hsweet said:**
> my bad.  should be gb for gig

Shouldn't it be "GB" for gig, not "gb"?

---

