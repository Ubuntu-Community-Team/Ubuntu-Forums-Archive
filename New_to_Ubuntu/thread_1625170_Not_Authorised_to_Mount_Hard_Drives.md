---
title: "Not Authorised to Mount Hard Drives"
date: 2010-11-18
forum: New to Ubuntu
---

### Post by cpcpcp on 2010-11-18
having rebooted I can see my two , not ubuntu, hard drives in Places  but when clicking to mount I am told I am not authorised to mount the  devices. Why has it started saying this and how to I fix it ?

---

### Post by pizza-is-good on 2010-11-18
Strange. What version of Ubuntu?
From your post, I assume that this was working before you rebooted, correct? Did you reboot for a particular reason (updates or such) or had you done any changes to your system before you rebooted?

Lets begin the troubleshooting. What format are these hard drives? How are they connected? External or internal?
Type```
sudo fdisk -l
``` in your terminal (just copy it from the code box), and post the output. It *might* give us some info, but not likely. It's a start anyway.

~pizza

---

### Post by cpcpcp on 2010-12-12
rebooting solved the problem,

I still don't know what caused it though <g>

---

