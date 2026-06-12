---
title: "Lsmod: how to know for what is each module for?"
date: 2010-01-28
forum: New to Ubuntu
---

### Post by frenchn00b on 2010-01-28
Hello,

In order to list them, and know their use, is there a manager or lsmod viewer than tells a bit more information as lsmod or dmesg?

Thanks
Best regards

---

### Post by inobe on 2010-01-28
```
sudo modinfo module name
```


that is for individual modules

---

### Post by frenchn00b on 2010-01-28
> **inobe said:**
> ```
sudo modinfo module name
```


that is for individual modules



Thanks 

here the lsmod_info.sh script:
```

 lsmod  | while read i ; do echo " ******* $i  ****************  " ; echo $i | cut -d" " -f1 ;  modinfo `echo $i | cut -d" " -f1`    ;  done



```

  lsmod_info.sh does not require sudo

---

### Post by falconindy on 2010-01-28
FYI reading lsmod and modinfo doesn't require sudo, nor does it get you any additional info.

---

### Post by frenchn00b on 2010-01-28
> **falconindy said:**
> FYI reading lsmod and modinfo doesn't require sudo, nor does it get you any additional info.

thank you, that's right indeed

---

