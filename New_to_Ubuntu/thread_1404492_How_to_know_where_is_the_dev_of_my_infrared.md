---
title: "How to know where is the /dev/? of my infrared?"
date: 2010-02-11
forum: New to Ubuntu
---

### Post by frenchn00b on 2010-02-11
Hello,

I am running irdadump and it works, but how to achieve to know which dev? 
Is there some test?

Cheers

---

### Post by undecim on 2010-02-11
Usually when I don't know what the dev of a device is, I will run "ls /dev/ > ls.out.1" without the device connected, and "ls /dev/ > ls.out.2" with it connected and use "diff ls.out.*" to see what device appeared when it was connected.

It's a kludgey way of doing it, but it's simple and easy.

---

### Post by frenchn00b on 2010-02-11
> **undecim said:**
> Usually when I don't know what the dev of a device is, I will run "ls /dev/ > ls.out.1" without the device connected, and "ls /dev/ > ls.out.2" with it connected and use "diff ls.out.*" to see what device appeared when it was connected.

It's a kludgey way of doing it, but it's simple and easy.

thanks a  LOT !

 cat detectnewdevice.sh
```
#!/bin/sh

echo "Remove the device"
read lkjfdsldf
ls /dev/ > /tmp/devils.out.1

echo "Plug the device"
read lkjfdsldf
ls /dev/ > /tmp/devils.out.2
 
echo "***>"
echo "  " 

cd /tmp
diff devils.out.*

```

---

