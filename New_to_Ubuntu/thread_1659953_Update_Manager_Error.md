---
title: "Update Manager Error"
date: 2011-01-04
forum: New to Ubuntu
---

### Post by RichieB07 on 2011-01-04
So I got this error when opening Update Manager and I have no idea what it means.  Any help would be greatly appreciated.
[IMG]http://i61.photobucket.com/albums/h66/BrokenSilences07/Screenshot.png[/IMG]

---

### Post by wojox on 2011-01-04
Go into Software Sources > Other Software and remove the tualatrix ppa

---

### Post by RichieB07 on 2011-01-04
> **wojox said:**
> Go into Software Sources > Other Software and remove the tualatrix ppa

I try to get into it via Synaptic and it won't allow me, the same error pops up.  Is there another way to get into it?

---

### Post by wojox on 2011-01-04
System > Administration > Software Sources > Other Software

---

### Post by RichieB07 on 2011-01-04
> **wojox said:**
> System > Administration > Software Sources > Other Software

I don't have Software Sources under Administration and Ubuntu Software Center will not open either.

Okay, I got into it through /etc/apt/sources.list.  I deleted the tualatrix PPA, but it's still in the sources list:
[IMG]http://i61.photobucket.com/albums/h66/BrokenSilences07/Screenshot-1.png[/IMG]

---

### Post by wojox on 2011-01-04
```
gksudo nautilus
```

Will let you remove it. Just be careful.

---

### Post by RichieB07 on 2011-01-04
> **wojox said:**
> ```
gksudo nautilus
```Will let you remove it. Just be careful.

I think what happened is when I installed Macbuntu something didn't install right, as I uninstalled it, reinstalled it, restarted (again) and now it works just fine.  Don't know what was wrong, but thanks for all the help!

---

### Post by wojox on 2011-01-05
Your welcome.

---

