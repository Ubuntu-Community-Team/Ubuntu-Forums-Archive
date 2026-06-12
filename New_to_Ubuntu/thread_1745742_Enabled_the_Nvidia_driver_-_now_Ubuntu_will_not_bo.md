---
title: "Enabled the Nvidia driver - now Ubuntu will not boot!"
date: 2011-05-01
forum: New to Ubuntu
---

### Post by mr_luksom on 2011-05-01
I enabled the Nvidia driver in my 11.04 install, as I had previously used it in 10.10, however it is now stopping ubuntu from booting.

I am not so interested in getting too the bottom of why it doesn't work, but I would like too disable it so I can use my computer again.

I can get to a cli by using the tty's 1-6. Is it possible to remove the Nvidia driver in thee terminal?

---

### Post by mikewhatever on 2011-05-01
Yes, it is possible to remove the driver. For example, if you installed the latest one:
```
sudo apt-get purge nvidia-current
```

...and if the legacy:
```
sudo apt-get purge nvidia-173
```

---

### Post by mr_luksom on 2011-05-01
Success! Thank you very much.

---

