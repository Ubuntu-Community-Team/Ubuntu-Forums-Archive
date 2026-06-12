---
title: "webcam installation howto"
date: 2009-03-16
forum: New to Ubuntu
---

### Post by iam_newhere on 2009-03-16
hi, 
how do i install my webcam microsoft vx1000 on my xubuntu 8.10.

thanks!

---

### Post by Sealbhach on 2009-03-16
Looks like its a tricky one but someone found a way. Ask if you have any problems.

[http://ubuntuforums.org/showthread.php?t=942915](http://ubuntuforums.org/showthread.php?t=942915)


.

---

### Post by iam_newhere on 2009-03-16
thanks for the sugestion. i will post another reply if it would work.

---

### Post by Crafty Kisses on 2009-03-16
Doesn't seem all that tricky, basically just grab the driver and compile it from source, just remember to have the following package installed before you attempt to compile the driver:
```
sudo apt-get install build-essential
```
Once you have the driver, save it to your desktop, then extract the bzip file and then open a Terminal and navigate to that folder, once your in the driver folder, run the following:
```
make
```
Then once you have done that, run the following:
```
sudo make install
```
Then reboot and you should be set. I'd also like to know if you have tried this already with Ekiga or Cheese? Has it worked? You may have to work with the settings. Open Ekiga then go to **Edit ->Preferences->Devices->Video Devices.** Then try changing some of the settings, (try both V4L and V4L2).

---

### Post by iam_newhere on 2009-03-16
i will just probably go back to my ubuntu8.04. tried everything.
the problem is everytime i turn on my xubuntu8.10 my webcam(microsoft vx1000) is always turned on. i dont know why. i feel like somebodys spying on me. so i will probably uninstall xubuntu8.10 for now and install ubuntu8.04 instead for it doesnt have that kind of behavior with my webcam. however i tested my webcam on cheese on ubuntu8.04 it turns out to be too dark. i dont know how to fix it. if you could help me again with this. thanks! i really appreciate your help and the ubuntu community!

im just frustrated with my webcam. 
but xubuntu and ubuntu are great!

---

