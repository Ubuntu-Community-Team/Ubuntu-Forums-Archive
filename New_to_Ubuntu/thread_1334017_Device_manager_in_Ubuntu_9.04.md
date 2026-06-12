---
title: "Device manager in Ubuntu 9.04"
date: 2009-11-22
forum: New to Ubuntu
---

### Post by djftl on 2009-11-22
Hi All,

I want to view my hardware, and I looked at the admin and preferences I can't find it there. Where can I find it? I want to view my tv card.

Regards,

---

### Post by Darce on 2009-11-22
You can install 'Device Manager' from Add/Remove or Synaptic Package Manager. After installation, you will find it under Applications -> System Tools.

If your just after your hardware info, punch the following into terminal :

sudo lshw -html > ~/hardware_info.html && firefox ~/hardware_info.html

Cheers,

Tim

---

### Post by djftl on 2009-11-22
Thanks Tim,

Installed it.

Regards

---

### Post by saadlulu on 2009-11-22
was looking for this, thanks Tim :)
and yeah this device manager is a bit complicated to the one i used to deal with in windows

---

### Post by NoaHall on 2009-11-22
There's also a tool called hardinfo, which you'll have to run from the terminal, but it's a GUI application.

---

