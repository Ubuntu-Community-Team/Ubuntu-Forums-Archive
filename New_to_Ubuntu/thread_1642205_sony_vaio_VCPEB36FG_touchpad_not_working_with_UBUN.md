---
title: "sony vaio VCPEB36FG touchpad not working with UBUNTU 10.10"
date: 2010-12-10
forum: New to Ubuntu
---

### Post by keshav kumar on 2010-12-10
I am using sony, vaio VPCEB36FG laptop. my touchpad is not working when i installed UBUNTU 10.10. MY cursor moves with mouse only.
please help...

---

### Post by elvisd on 2010-12-15
HI, 

I had to add a parameter in grub (vaio vpc-f13Z1e)
enter command
```
sudo nano /etc/default/grub
```
Change the line
```
GRUB_CMDLINE_LINUX=""
```
to
```
GRUB_CMDLINE_LINUX="i8042.nopnp"
```
then issue the command
```
sudo update-grub
```
and reboot.

Hope this helps, kindly

---

### Post by maohacker on 2011-03-07
@elvisd, THANKS VERY MUCH! your tip worked on my VAIO VPCEB3J1E, even the scroll runs well!
 i've been searching for this tip for a month! i subcrive to Ubuntu Forums just to thank you, i hope by the way i will learn and share a lot of things

---

### Post by elvisd on 2011-03-07
> **maohacker said:**
> @elvisd, THANKS VERY MUCH! your tip worked on my VAIO VPCEB3J1E, even the scroll runs well!
 i've been searching for this tip for a month! i subcrive to Ubuntu Forums just to thank you, i hope by the way i will learn and share a lot of things

Thank you maohacker. You're very kind.

---

