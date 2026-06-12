---
title: "[SOLVED] sbackup and remastersys problems"
date: 2008-12-04
forum: New to Ubuntu
---

### Post by capnthommo on 2008-12-04
hi everone.  i have tried using both of the above apps to try and backup my home foler/drive.
after using sbackup a couple of times i noticed that according to 'system monitor' the 'device'or file  /dev/sda /  no longer had 37 of 50 GB available and in fact now has only 20 GB - quite a substantial loss im sure you will agree.  
according to the disk usage analyser the total file system usage is 55%, the file system has over 30 GB taken up by casper,  ISOTMP and remastersys.
i have removed both these apps from the synaptic packag manager and also ttried a reboot but the system still seems clogged with these backup related files.  how can i get rid of them and reclaim my disk space?
this one is proving to be much tougher than expected.  any help will be really appreciated.  thanks
nigel

---

### Post by capnthommo on 2008-12-05
Okay anybody reading this one, i think i have got around what was bothering me and used GParted to alter round my partitions and get rid of windows which takes the pressure off.  and in future i shall burn a dvd disk of my /home folder with all the hidden files using K3b.  that allied with the live cd should give me the cover i need till i get a usb hard drive for backing up.  
cheers folks
nigel
):P

---

