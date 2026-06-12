---
title: "Startup errors"
date: 2009-11-11
forum: New to Ubuntu
---

### Post by szsaifi on 2009-11-11
I installed Ubuntu 9.10 parallel with Windows XP on a ext4 file system partition. whenever i boot ubuntu, after a few moments, a huge number of errors come on the screen scrolling down stating something like
Unable to resolve ctc configuration
I am not quite sure about that what is it. However, if i load ubuntu from inside windows xp in vmware workstation 7, there comes no problem. Ubuntu loads smoothly and correctly. Can any one tell me what is the problem and how it can be resolved. Furthermore, when i upgraded grub to update 4, my windows xp disappeared from the boot options. can anyone tell how can i restore the windows xp in boot options.

---

### Post by lavinog on 2009-11-11
for grub issue try:
```
sudo update-grub2
```
more info: [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

for the error message:
Does the rest of ubuntu work fine?  Many motherboards can show some warnings, but shouldn't cause a problem.
it would be helpfull to give some information on your system:
```
lshw
```
```
dmesg
```
```
lspci
```

Running ubuntu in a vm isn't going to give the same errors because the vm offers completly different hardware specs.

---

### Post by szsaifi on 2009-12-23
Ubuntu does not work quite well. It gives errors in some packages but not often. The board I'm using is Intel DG31PR. I installed Ubuntu on another computer system with similar board (Intel DG31GL) and it works fine. There is no problem. Does support of my board is tested for Ubuntu 9.10?

---

### Post by lavinog on 2009-12-23
> **szsaifi said:**
> Ubuntu does not work quite well. It gives errors in some packages but not often. The board I'm using is Intel DG31PR. I installed Ubuntu on another computer system with similar board (Intel DG31GL) and it works fine. There is no problem. Does support of my board is tested for Ubuntu 9.10?

It should work...what are the errors you are getting?
It could be that you are using different repositories.
I have recently started having issues with some repositories...malformed Release file errors.

---

