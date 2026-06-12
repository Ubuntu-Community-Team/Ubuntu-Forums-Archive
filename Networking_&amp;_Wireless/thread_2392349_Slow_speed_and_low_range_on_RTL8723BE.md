---
title: "Slow speed and low range on RTL8723BE"
date: 2018-05-20
forum: Networking &amp; Wireless
---

### Post by kaldrox on 2018-05-20
Hello,
I'm experiencing the issues mentioned above. I looked up for information on the forum and I tried to apply what user [chili555]("https://ubuntuforums.org/member.php?u=35909") had given [here]("https://ubuntuforums.org/showthread.php?t=2312075&p=13433013#post13433013") but upon ```
make
``` I end up with
```
 #error "This branch is abandoned. Please do not use"
```
Some sources say that this branch had already been merged to the kernel (or smth like that lol) but then I have no idea what else to do. Hope you guys can enlighten me on this
Peace

---

### Post by jeremy31 on 2018-05-20
Try ```
sudo modprobe -r rtl8723be
sudo modprobe rtl8723be ant_sel=2
```
If it is better
```
echo "options rtl8723be ant_sel=2" | sudo tee /etc/modprobe.d/rtl8723be-ant.conf
```

---

### Post by kaldrox on 2018-05-21
That worked, Thank you :)

---

