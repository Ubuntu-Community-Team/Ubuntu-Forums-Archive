---
title: "Can`t remove home directory"
date: 2009-01-16
forum: New to Ubuntu
---

### Post by nothingspecial on 2009-01-16
After giving the wife my netbook I have created her account and pimped it to her liking but I can`t remove myself completely.

I`ve done a ```
sudo rm -rf /home/me
```but I get ```
rm: cannot remove `/home/me/.gvfs': Permission denied
```

What`s up.

Thanks

---

### Post by logos34 on 2009-01-16
You can disregard that error message (-> .gvfs = 'gnome virtual file system') I get it too when trying to copy content of /home.  

Try booting into the live cd, mount the partition and then run the command again.

---

### Post by taurus on 2009-01-16
```
sudo chmod 755 /home/me/.gvfs
sudo rm -rf /home/me
```

---

### Post by nothingspecial on 2009-01-16
I`m not that bothered really. I just like everything clean.

She wouldn`t even know /home/me was there.

Thanks for your reply:)

---

### Post by nothingspecial on 2009-01-16
> **taurus said:**
> ```
sudo chmod 755 /home/me/.gvfs
sudo rm -rf /home/me
```

Permission denied, didn`t ask for a password or anything.

Thanks for your reply.:)

---

### Post by logos34 on 2009-01-16
> **taurus said:**
> [code]sudo chmod 755 /home/me/.gvfs

what's the default permissions on that folder?

---

### Post by nothingspecial on 2009-01-16
> **logos34 said:**
> what's the default permissions on that folder?

It`s asthough it doesn`t exist

```
d????????? ?    ?      ?              ?.gvfs
```

---

### Post by nothingspecial on 2009-01-16
Well, I`ve done it.

Reboot, press escape at grub.

Log in to a r*** s***l

And do it from there

Thanks guys.

---

