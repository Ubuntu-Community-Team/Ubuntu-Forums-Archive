---
title: "Bootable USB question"
date: 2011-03-04
forum: New to Ubuntu
---

### Post by jyrous on 2011-03-04
I have a dell mini 9 that is has a failed ssd. It is fried and I am not planning to replace it.

PXE-E61:  Media test failure, check cable 
PXE-M0F:  Exiting PXE ROM. 
Operating System not found

However I wanted to donate this to my aunt who isn't as well off, and simply wants to use this netbook to surf and check email. I was thinking that I could boot from usb, so I tried both the desktop and netbook .iso, and made them bootable from usb. 

The desktop version booted fine, but the wireless network card needed drivers, and it only worked after I activated the broadband STA wireless drivers from my lan line. The netbook remix .iso took way to long to load and had the same problem.

My aunt only has a wireless connection. So I was wondering if it was possible to boot with the wireless drivers included? Could I use the Ubuntu Customization Kit?

Any suggestions are greatly appreciated!
thanks

---

### Post by NCLI on 2011-03-04
> **jyrous said:**
> I have a dell mini 9 that is has a failed ssd. It is fried and I am not planning to replace it.

PXE-E61:  Media test failure, check cable 
PXE-M0F:  Exiting PXE ROM. 
Operating System not found

However I wanted to donate this to my aunt who isn't as well off, and simply wants to use this netbook to surf and check email. I was thinking that I could boot from usb, so I tried both the desktop and netbook .iso, and made them bootable from usb. 

The desktop version booted fine, but the wireless network card needed drivers, and it only worked after I activated the broadband STA wireless drivers from my lan line. The netbook remix .iso took way to long to load and had the same problem.

My aunt only has a wireless connection. So I was wondering if it was possible to boot with the wireless drivers included? Could I use the Ubuntu Customization Kit?

Any suggestions are greatly appreciated!
thanks
Yes, it is possible. You just need to actually install Ubuntu on the USB key, using it as an ordinary SSD. Just plug it in to a computer, then boot the Ubuntu installer from another USB stick, or a CD, and choose to install Ubuntu on the USB stick instead of the internal HDD.

Also, make sure to tell the installer to put the bootloader on your USB drive.

---

### Post by jyrous on 2011-03-04
Thanks it worked! 

I ended up connecting it to my lan line and using these to get the wireless working

sudo apt-get update

sudo apt-get install bcmwl-kernel-source

I actually used the ubuntu desktop and it runs ok....., would it be faster if I used ubuntu Netbook? (or another lighter distro to try?)

thks for the help NCLI

---

