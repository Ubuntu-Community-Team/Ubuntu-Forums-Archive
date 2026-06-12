---
title: "How to stop unity showing HDD's on desktop"
date: 2011-05-26
forum: New to Ubuntu
---

### Post by CaptainMark on 2011-05-26
Since unity has been developed a little since its awful early days im really beginning to enjoy it and glad i didnt give up on unity in the early natty alpha days. one little thing thats getting to me is that when you plug in any external media it still appears on the desktop even though it appears in the unity launcher, i dont need both and it just looks lame, ive tried mounting to /mnt instead of /media and my external hdd doesnt show on the desktop but neither does it on the launcher, can i have it show in the launcher and not the desktop, anyone know a way around this?

---

### Post by wildmanne39 on 2011-05-26
> **CaptainMark said:**
> Since unity has been developed a little since its awful early days im really beginning to enjoy it and glad i didnt give up on unity in the early natty alpha days. one little thing thats getting to me is that when you plug in any external media it still appears on the desktop even though it appears in the unity launcher, i dont need both and it just looks lame, ive tried mounting to /mnt instead of /media and my external hdd doesnt show on the desktop but neither does it on the launcher, can i have it show in the launcher and not the desktop, anyone know a way around this?Hi, the only way I know of is to right click and unmount the drive.

---

### Post by wojox on 2011-05-26
Gconf-editor > apps > nautilus > desktop > volumes_visible

---

### Post by warfacegod on 2011-05-26
Ubuntu Tweak has an option for showing or not showing Volumes on the desktop.

---

### Post by mc4man on 2011-05-26
Try setting  in gconf-editor as shown in screen (volumes visible disabled
or from cli
```
gconftool-2 -s -t boolean /apps/nautilus/desktop/volumes_visible false
```

---

### Post by quarkhirad on 2011-05-27
> **warfacegod said:**
> Ubuntu Tweak has an option for showing or not showing Volumes on the desktop.

Thanks man. That worked

---

### Post by CaptainMark on 2011-05-27
> **wojox said:**
> Gconf-editor > apps > nautilus > desktop > volumes_visible
This worked perfectly thank you

---

### Post by hakermania on 2011-05-27
Well what I know is that you can stretch the icons of the HDDs on a preferable size and move them to a position where they wont be annoying... Small and in the corner..... That's an option :P

---

### Post by warfacegod on 2011-05-27
> **quarkhirad said:**
> Thanks man. That worked

Sure thing.

---

