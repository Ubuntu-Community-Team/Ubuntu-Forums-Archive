---
title: "New HDD install to netbook not accepting Ubuntu 10.10"
date: 2011-02-25
forum: New to Ubuntu
---

### Post by Herbiesmate on 2011-02-25
Hi,

I have a good level of understanding when it comes to pc (not expert by any means though!) and so I decided to fit a new HDD and extra RAM to my Samsung NC10 when it stopped recognising the old HDD. This Imthough would be easy as I had read up on creating a bootable USB Stick etc.

Far from easy is how I would describe this experience so far! A friend suggested installing Ubuntu 10.10 to me which sounded like a good idea. So I duly proceeded to prepare the USB with Ubuntu. Everything is fine and dandy up until this point. Then I booted the netbook from the USB and was asked if I wanted to partition the drive, use the whole drive or copy to HDD etc. to which I chose to copy to HDD. The install appeared to be going fine. Once completed, I kept the USB in and used the netbook which was quality. So I then shutdown and took the USB out, cranked up the netbook and was promptly advised "Operating System Not Found" once again. So repeated the procedure as above and once again we are working fine as long as the USB is left in.

I know I said I had a good level of understanding but when it comes to partioning drives etc. I really have no clue what they are talking about (not strictly true as I understand the terminology just not how to do it etc.).

Can anyone on here help me get this poorly netbook operating with Ubuntu on its new HDD please?! (It's been out of action for 6 weeks or so now, whilst I have been tearing my hair out!!!)

:confused::confused::confused::confused::confused::confused::confused::confused:

---

### Post by kareempharmacist on 2011-02-25
may be you chose an option which copies the files to the hard disk but still they need the usb to boot (boot sector is on the usb) the usb now is the boot device.... 
try to boot form the usb again and post the contents of /etc/fstab here please 
to understand the terminology which is very importand you have to read about linux
if you want to do so just tell me and will give u some cool links to begin with.
In linux the more you know.....the better....

---

### Post by bug67 on 2011-02-25
When asked, instead of selecting "copy" choose instead the "use entire disk".

---

