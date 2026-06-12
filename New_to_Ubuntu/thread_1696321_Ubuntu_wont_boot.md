---
title: "Ubuntu wont boot"
date: 2011-02-27
forum: New to Ubuntu
---

### Post by meteoradew on 2011-02-27
I tried to install Ubuntu 10.10 on my laptop today. I downloaded on both a cd and a usb and neither worked. Now when i boot up Ubuntu it either goes through some code and stops doing anything at "NET: Registered protocol family 1" with a blinking underscore on the next line. Or it just has the black screen with the blinking underscore.

Help!

ive been trying to figure this out for 9 hours now.

---

### Post by Quackers on 2011-02-27
Have you checked the md5sum of the downloaded iso file?
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If that's ok, while booting from the live cd/usb, are you getting to the first purple screen (the one with the little man icon at the bottom)? If so on that screen press Esc key, then choose language and on the next screen you will see some options. Choose the one that checks the cd for errors.
If that finds an error but the md5sum was ok you will need to burn the image again, maybe on a slower setting.

---

### Post by davidmohammed on 2011-02-27
try booting with acpi=off in your grub options


when booting - press shift to display your grub

press e to edit

find the line ending quiet splash

add acpi=off immediately before quiet splash

i.e. the line looks like

... acpi=off quiet splash...

CTRL +X to boot.


You could also try some other common boot options as described [here]("https://help.ubuntu.com/community/BootOptions").

---

