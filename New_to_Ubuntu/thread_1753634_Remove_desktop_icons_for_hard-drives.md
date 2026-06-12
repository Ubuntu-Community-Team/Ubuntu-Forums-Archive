---
title: "Remove desktop icons for hard-drives ?"
date: 2011-05-09
forum: New to Ubuntu
---

### Post by cyb3r_sn4k3 on 2011-05-09
Is it possible to remove some of the icons present in the xubuntu desktop ?
Because there are some partitions which I rarely use so I dont want them on the desktop.
Even showing only mounted devices is good enough for me :)

---

### Post by pinballwizard on 2011-05-09
Probably not the most eloquent solution, but I achieve that using ubuntu tweak.

---

### Post by cyb3r_sn4k3 on 2011-05-09
Seems it doesn't work with Xfce4.

---

### Post by klytu on 2011-05-09
> **cyb3r_sn4k3 said:**
> Is it possible to remove some of the icons present in the xubuntu desktop ?
Because there are some partitions which I rarely use so I dont want them on the desktop.
Even showing only mounted devices is good enough for me :)

In Settings Manager>Desktop, click the "Icons" tab. Clear the checkbox for "Removable Devices". I think this will remove all of the extra drive icons from your desktop.

---

### Post by cyb3r_sn4k3 on 2011-05-09
> **klytu said:**
> In Settings Manager>Desktop, click the "Icons" tab. Clear the checkbox for "Removable Devices". I think this will remove all of the extra drive icons from your desktop.

But that removes all the icons including flash devices which are connected :(

---

### Post by anaconda on 2012-06-21
A bit old thread, but I just had the same problem, and found a solution (with xubuntu 12.04)

I had a windows partition showing as a icon on desktop. It was showing as a removable device and I didnt want to lose flash devices from desktop just like you.

After adding that windows partition to /etc/fstab and rebooting it vanished from desktop. 
I added it with option "noauto" so it wont be mounted at boot time...

---

### Post by Peripheral Visionary on 2012-06-21
Right-click on the desktop. Select [COLOR=Navy]**Desktop Settings**[/COLOR] and click the [COLOR=Navy]**Icons**[/COLOR] tab. At the bottom of that menu you can choose your [COLOR=Navy]**Default Icons**[/COLOR]. Simply un-check all of them except the Removable Devices. Close, done!

---

