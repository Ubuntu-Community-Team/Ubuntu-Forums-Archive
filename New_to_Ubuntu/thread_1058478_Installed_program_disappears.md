---
title: "Installed program disappears"
date: 2009-02-02
forum: New to Ubuntu
---

### Post by Spitting Crows on 2009-02-02
Hi. I just reformatted my linux partition and reinstalled intrepid.  Among the programs I regularly use is Vlan audio/video for radio/net stream tv/movies what have you.  It's versatile and lovely.  I installed it through Synaptic Package Manager (and it shows as currently installed), but I can't find it in any of my menu's or menu-editing options.  I tried searching my root and found some vlan files, but none of them appear to be the actual program, as none have the traffic cone icon.  I'm used to working dos-based, so maybe i'm going about it wrong.  But Ubuntu thinks it's on my computer and updated (according to SPM).  Ideas?  Thanks.

---

### Post by 2hot6ft2 on 2009-02-02
I don't see anything about a gui for it in synaptic so have you tried the terminal?
Applications>Accessories>Terminal
```
vlan
```
or
```
sudo vlan
```

---

### Post by handydan918 on 2009-02-02
assuming that the name of the application is actually vlan, do ```
which vlan
```to find out where the executable resides.

---

### Post by Spitting Crows on 2009-02-02
I'm a bit embarrassed.  I had a similar problem with a program (nicotene+) before I reinstalled intrepid, so I figured one try at reinstalling the package was enough.  I tried again to reinstall the package through SPM just now and VLC shows up in my menus.  Thanks so much for the prompt responses!

---

