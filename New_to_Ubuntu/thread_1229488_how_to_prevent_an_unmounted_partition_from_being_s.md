---
title: "how to prevent an unmounted partition from being shown in nautilus?"
date: 2009-08-02
forum: New to Ubuntu
---

### Post by legolas_w on 2009-08-02
Hi
I have some partitions which I have not included them in the fstab file so they are not mounted by default.

I just fo not like them to be shown in nautilus, any configuration parameter around?

Thanks

---

### Post by hellmet on 2009-08-02
I think they are added by default into fstab during install, but I cannot be sure. Just check the /dev/*da devices in fstab. 

I'm on a Win box right now so sorry if I'm wrong. I'd like to know the answer to this too.

---

### Post by credobyte on 2009-08-02
Not sure if this is what you need, but .. maybe it helps.

As root ( sudo -i ):
```
echo "sdaX" >> /dev/.hidden

```

Replace X with what you need to hide ( eg. sda6 partition ).

---

### Post by firen on 2009-08-02
I believe it is due to automount (autofs) will update soon, on M$ right now :(

---

### Post by lswb on 2009-08-02
Actually, if they are mounted in fstab, they *won't* show up in the nautilus sidebar, though they can be accessed by clicking in the "filesystem" selection in the sidebar, or by using the up arrow and following the filesystem tree.

---

