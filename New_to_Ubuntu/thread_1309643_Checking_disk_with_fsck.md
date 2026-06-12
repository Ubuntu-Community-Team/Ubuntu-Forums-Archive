---
title: "Checking disk with fsck"
date: 2009-11-01
forum: New to Ubuntu
---

### Post by alpha_lt on 2009-11-01
Hello all,

I have question on using fsck. As its not possible to run it on mounted system I want to know how its possible to do. Booting other system from USB is not an option for me. As I kn ow its possible to use *shutdown -F -r now *, but will it work on Ubuntu ? I'm asking because *man shutdown* does not show such option as *-F*. Other question how can I change fsck option for boot checking ? Also I know that fsck will run automatically on system after some boot times. How can I control boot number after which fsk will run and with what options it will run ?
Thanks in advance.

Best regards,
alpha

---

### Post by Liolikas on 2009-11-01
As I kn ow its possible to use shutdown -F -r now , but will it work on Ubuntu ? 
Yes. 

Other option is sudo touch /forcefsck
And reboot.

---

### Post by alpha_lt on 2009-11-01
with what parameters will run fsck ? Is there any config file for it or smth ?

Regards,
alpha

---

