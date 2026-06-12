---
title: "Grub loading error 17..."
date: 2011-06-16
forum: New to Ubuntu
---

### Post by Rician on 2011-06-16
i recently formatted my HDD, now when i try to boot i get grub loading error 17... i get the same error when trying live usb. i dont have a cd drive. dont knowh what to try anymore. help is appreciated. 


Thanks.

---

### Post by Peter09 on 2011-06-16
Are you sure that you are booting from your live USB. Getting the same Grub error on both sounds a bit iffy. 

It looks like you have removed a bootable O/S from your HD.

---

### Post by Rician on 2011-06-16
Yes i am booting from my live usb. i have tried various live distrobutions but all i get is grub loading error 17 everytime i insert the usb drive.

---

### Post by dcsoldschool53 on 2011-06-16
> **Rician said:**
> Yes i am booting from my live usb. i have tried various live distrobutions but all i get is grub loading error 17 everytime i insert the usb drive.

When you tried to boot from the USB, did you on (start up) hit the F12 key for the boot menu or F2 to go into the BIOS to change your configuration to boot to USB?

---

### Post by oldfred on 2011-06-16
Grub error 17 is from grub legacy. Grub2 does not have error numbers.
[http://members.iinet.net.au/~herman546/p15.html#17](http://members.iinet.net.au/~herman546/p15.html#17)

Post this from liveCD:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

