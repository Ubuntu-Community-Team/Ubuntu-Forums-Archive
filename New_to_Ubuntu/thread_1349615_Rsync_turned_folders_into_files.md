---
title: "Rsync turned folders into files"
date: 2009-12-08
forum: New to Ubuntu
---

### Post by geckoguykc on 2009-12-08
The ubuntu installation on my netbook crashed when trying to hibernate, but my personal files all seemed totally intact when mounting from the live-usb. This is the third time I've tried to use ext4, on different operating systems too, and it always freezes up for some reason, and after hard-restart everything is kaput. Anyways, I decided to "rsync -av" my home directory onto a USB hard drive, and did a fresh install on the netbook. So I reverse the rsync back onto my new home directory, to find that all of my personal folders turned into different kinds of vague files. For instance, my Videos directory, which has many seasons of shows I'd hate to have to re-download, is now an "executable text file", and my Documents folder is some kind of "compressed archive". I don't know what could have gone wrong, but the copy on the USB drive is in the same state. I really need to recover what's in these folders if at all possible! any help would be greatly appreciated. All I used was "rsync -av" from root both times...](*,)

---

### Post by geckoguykc on 2009-12-08
Never mind, I think it was just corrupted from the start. I just found a bunch of my damaged video files obscurely located in the hidden ".tomboy" directory... I'll just have to start from scratch.

---

