---
title: "Getting bootup Ubuntu graphics back"
date: 2009-01-04
forum: New to Ubuntu
---

### Post by Charlie Chick on 2009-01-04
Hello Everybody,

I have a silly problem! After running out of space with my 160Gb drive I bought a 750Gb drive and used dd to clone everything over, thanks to the helpful people on this forum.

Unfortunately, when I boot up, I get a screen full of B&W text instead of the nice colourful Ubuntu graphics. Is there any way of getting that back?

Thanks,

Charlie

---

### Post by gettinoriginal on 2009-01-04
Install "startup manager" from synaptic, it will allow you to edit the preferences of boot and login screens.  :P

---

### Post by kansasnoob on 2009-01-04
I rather suspect a UUID problem. Post the following outputs from terminal:

```
sudo blkid -c /dev/null
```

Then:

```
cat /etc/fstab
```

And finally:

```
cat /etc/initramfs-tools/conf.d/resume
```

---

### Post by Charlie Chick on 2009-01-07
Thanks, people, I'll try your suggestions at the weekend.

---

