---
title: "Desktop"
date: 2010-01-06
forum: New to Ubuntu
---

### Post by ksrijith on 2010-01-06
Hi,
I'm a total noobi so please don't think low of me :)... I just installed ubuntu 9.10 and logged in using Gnome. The desktop looks something like the screenshot attached. The desktop basically is showing the main ubuntu menu items all arranged. I'm not sure how to remote this and get a plain desktop showing all the files in my $HOME/Desktop folder instead.

It would be a great help if someone could help out on how this can be done.

Thanks,
Srijith

---

### Post by oldos2er on 2010-01-06
Looks like the netbook version of Ubuntu, Ubuntu UNR.

---

### Post by ksrijith on 2010-01-06
ya its the notebook version. i've installed it in my laptop. is there anyway to get the normal look?

---

### Post by ksrijith on 2010-01-06
Thanks using the following command UNR gets removed:

**sudo apt-get remove ubuntu-netbook-remix ubuntu-netbook-remix-default-settings maximus**

---

### Post by ksrijith on 2010-01-06
sorry didn't work. after the restart the desktop came back and again i can't right click or change anything. even though the UNR is removed the desktop still remains the same. :(

---

### Post by oldos2er on 2010-01-06
Have you tried installing ubuntu-desktop?
```
sudo apt-get update && sudo apt-get install ubuntu-desktop
```

---

### Post by ksrijith on 2010-01-06
hi,
thanks. I was able to remove desktop launcher. Had missed notebook-launcher package. Once I removed that using Synaptic I was able to get the default Gnome desktop. :) :)

Thanks
Srijith

---

### Post by oldos2er on 2010-01-06
Nice wallpaper. Glad you got it working!

---

### Post by RedRat on 2010-01-06
Love that Desktop wallpaper. Where did you get it?

---

