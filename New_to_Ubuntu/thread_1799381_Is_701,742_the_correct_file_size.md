---
title: "Is 701,742 the correct file size??"
date: 2011-07-07
forum: New to Ubuntu
---

### Post by rwscid on 2011-07-07
Can someone tell me if ubuntu-11.04-desktop-i386.iso filesize is 701,742 KB please. Crappy Bolivian internet connection takes 7 hrs to download file, universal USB installer is not making me a bootable USB, need to know if I should start over. Thanks.

---

### Post by Wim Sturkenboom on 2011-07-07
Check the md5 hash instead of the filesize. More reliable as it will also indicate if the download isn't corrupted somewhere.

---

### Post by nmaster on 2011-07-07
you should verify the md5 hash value.  you should be able to find the correct value on the download site somewhere.  then just follow the instructions to calculate it locally.  this will tell you if the image is correct.
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by rwscid on 2011-07-07
OK, my md5 hash checks out, any suggestions on why my usb drive won't boot on either my netbook (ASUS 1000HE) or on this generic desktop with a Foxconn bios. About 6 months ago I successfully downloaded and could boot up ubuntu 10.10, used the same universal usb installer and the same usb drive. When I tried the same usb drive on both computers I could get nothing, so I downloaded ubuntu 11.4 hoping to have better luck but so far so bad.

My boot sequence on both computers is usb drive first (and only) but only get 'disk boot failure' messages.

any ideas greatly appreciated. I ran a virus check on all the usb drives and found nothing.

---

### Post by Wim Sturkenboom on 2011-07-08
If it used to work with 10.10, next it no longer works with 10.10, I strongly suspect a bad USB stick. The fact that 11.04 also does not work on it as well as the fact that it does not work on 2 computers makes my suspicions stronger.

---

