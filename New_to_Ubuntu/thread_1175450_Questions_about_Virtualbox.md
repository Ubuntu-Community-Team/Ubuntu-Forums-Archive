---
title: "Questions about Virtualbox"
date: 2009-06-01
forum: New to Ubuntu
---

### Post by Gp. on 2009-06-01
Hi,
I was just wondering if I run XP in a VM can it talk to my devices like webcam and dvd burner?

Will I be able to route the devices access to the VM basically so I can use the dvd burner and webcam inside xp (virtually)...

Thanks.

---

### Post by philinux on 2009-06-01
You will need to install the guest additions package then the answer is yes.

See virtualbox's website faq's

---

### Post by Jazzy_Jeff on 2009-06-01
I believe you will need to download the non free version from their website if you need USB support.

---

### Post by clive littlewood on 2009-06-01
Hi

Download the NON ose version from the Sun site, this gives you USB support where the ose version in the repos does not.

As philinux says use the guest addon for better control, you do this from the guest system menus.

Hope this helps

Clive

---

### Post by 3rdalbum on 2009-06-01
I'm not sure if you can forward your DVD burner. Your webcam can be used in the guest OS, but while it is being forwarded to the guest OS it will not be able to be used in the host.

---

### Post by tarps87 on 2009-06-01
You can use your dvd drive and webcam with the guest os (in your case xp), however you can not use them in the guest and host os's or in multiple guest os's at the same time. Imagine the confusion it could cause :)
The guest additions are not necessary for this, or at least in my case they are not but they do make for a nicer user experience. Try installing them and pressing "alt gr + l" (the right alt key) ;)

---

