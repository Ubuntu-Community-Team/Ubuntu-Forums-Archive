---
title: "Kubuntu?"
date: 2009-04-09
forum: New to Ubuntu
---

### Post by eilios on 2009-04-09
I recently installed KDE for my family to have a more windows-like desktop, and now every time I log in it shows Kubuntu loading. I would prefer to have the original Ubuntu loading bar. Any way to fix this?

---

### Post by x33a on 2009-04-09
open a terminal, and paste this
```
sudo update-alternatives --config usplash-artwork.so
```

enter the number at which ubuntu loading screen is listed. it should be at 1.

after that
```
sudo update-initramfs -u
```

---

