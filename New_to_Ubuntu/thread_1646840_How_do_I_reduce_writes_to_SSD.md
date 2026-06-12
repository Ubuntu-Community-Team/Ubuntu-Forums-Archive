---
title: "How do I reduce writes to SSD?"
date: 2010-12-16
forum: New to Ubuntu
---

### Post by IXpike on 2010-12-16
I have a asus eeepc 901 with ubuntu 10.10 installed on the 16 gb SSD

I understand I can improve performance and life of thee SSD by reducing the need of ubuntu to access the SSD.

Is there an easy way to do this - I am new to ubuntu.

Thanks

---

### Post by Paqman on 2010-12-16
Sure, there's a few things you can do. You can shunt stuff like your /tmp folder onto a ramdisk:
```
gksu gedit /etc/fstab
```
and add:
```
tmpfs /tmp tmpfs defaults,noexec,nosuid 0 0
```
then:
```
sudo mount -a
```

Once you've done that you can start doing other tweaks like moving your browser cache into /tmp, you'll have to Google for that, it depends on what browser you use. I'd also wind the swappiness waaaay down, it's set too high by default. 10 should be fine for a desktop system, I have some of mine at zero.

---

