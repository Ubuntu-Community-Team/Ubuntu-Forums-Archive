---
title: "virtualbox usb has a problem, HELP PLEASE!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!"
date: 2009-02-25
forum: New to Ubuntu
---

### Post by antez on 2009-02-25
HELLO

i use ubuntu ultimate edition 2.0
and i use virtualbox for windows, it runs fine but the only problem is usb.
i wont to use the bluetooth on windows and its not that it doesn't find it but it says that it is unavailable. actually the only thing that can read is an HP printer and an HP camera! 
So what i have to do to enable them?

                                         please respond
                                        THNX in advance

---

### Post by mlentink on 2009-02-25
A few questions:

- are you running ubuntu in a virtual machine within windows, or rather the oither way around?
- which version (OSE, or closed source?)
- do you really mean accessing bluetooth in a VM or USB?

---

### Post by fishman78 on 2009-02-25
This is what I used to get usb working well in Virtual Box:

Add this line to the bottom of /etc/fstab, replace the devgid number with your devgid:
none /proc/bus/usb usbfs devgid=123,devmode=664 0 0

Linky:  [http://www.samlesher.com/ubuntu/virtualbox-with-usb-support-on-ubuntu-810-intrepid-ibex/](http://www.samlesher.com/ubuntu/virtualbox-with-usb-support-on-ubuntu-810-intrepid-ibex/)

---

### Post by antez on 2009-02-25
my OS is ubuntu and i use virtualbox for running windows xp sp2

about the version it says "Virtualbox 2.1.4" (i don't know if that helps you)

I don't know what VM is but my bluetooth is USB


                              thnx

---

### Post by antez on 2009-02-25
> Add this line to the bottom of /etc/fstab, replace the devgid number with your devgid:
none /proc/bus/usb usbfs devgid=123,devmode=664 0 0

Linky: [http://www.samlesher.com/ubuntu/virt...intrepid-ibex/](http://www.samlesher.com/ubuntu/virt...intrepid-ibex/)

I don't understand nothing  sorry!!!!!!!!!!
but can yo explain it????????

---

### Post by antez on 2009-02-25
aaaaaaaaaaaaaaaaaaaaaaaaa

i fallowed the link to change from OSE to CSE but if i change my virtualbox will i have problem with my virtual machine?

---

### Post by antez on 2009-02-25
will it read the my virtual disks?

---

### Post by fishman78 on 2009-02-25
> **antez said:**
> aaaaaaaaaaaaaaaaaaaaaaaaa

i fallowed the link to change from OSE to CSE but if i change my virtualbox will i have problem with my virtual machine?

That i'm no 100% sure on.  I've never tried.  Does anyone else know??

---

### Post by antez on 2009-02-25
i will try it

but when you say

> Add this line to the bottom of /etc/fstab, replace the devgid number with your devgid:
none /proc/bus/usb usbfs devgid=123,devmode=664 0 0

what i add where????????????????????????????????????????

---

### Post by antez on 2009-02-25
ok found what it is but knw i have to findout how to became a super user

i wrote sudo but it didn't help

---

### Post by fishman78 on 2009-02-25
> **antez said:**
> ok found what it is but knw i have to findout how to became a super user

i wrote sudo but it didn't help

Try this:

```
sudo gedit /etc/fstab
```

Maybe make a copy of your old fstab, just incase...

---

