---
title: "pc crashed..."
date: 2010-02-02
forum: New to Ubuntu
---

### Post by pous on 2010-02-02
hi everyone, i need some help here, i´m relativeley new to linux, have been using it in a wubi install for round 6 months now and since i tried it haven´t used windows, i was thinking on making a backup and installing it proper when my pc crashed, now i cant open windows ( which i couldnt care less for) neither ubuntu... 

When i try to open ubuntu it opens in grub, and i have no clue to do from tnere to solve anything... 
Any ideas?? I´d apreciate any help, thanks!

---

### Post by J V on 2010-02-02
It can't open in grub, wubi uses windows bootloader... Are you sure you are on a wubi install?

---

### Post by chaanakya_chiraag on 2010-02-02
What exactly do you mean by "a grub prompt"?  Since you used a wubi install, grub is not installed.  Do you mean a black screen with a blinking cursor?

---

### Post by pous on 2010-02-02
well i have no idea what it is, but looks like dos, but instead of "C:\" or whatever says grub, and yes it was a wubi virtual partition inside windows

---

### Post by pous on 2010-02-02
well i have no idea what it is, but looks like dos, but instead of "C:\" or whatever says grub, and yes it was a wubi virtual partition inside windows

---

### Post by chaanakya_chiraag on 2010-02-02
Hmmm...again, that really doesn't make sense because you installed via wubi, which hooks into the Windows bootloader...
If you can, burn a cd on another computer, boot it up, select "Try without any change to your computer", and copy all files (from Windows) that you want to keep.  I'm not sure, but I don't think you can save the files in your wubi thing.  I hope I'm wrong :D
Then, install Ubuntu and select "Use entire disk" at the partitioning stage to overwrite Windows.  You're done.

---

### Post by pous on 2010-02-02
i tried the live disc and i cant open the stuff i had in ubuntu... It only recognised windows... So i guess ill just have to let go the stuff i had there... Thanks for all...

---

### Post by chaanakya_chiraag on 2010-02-02
Just out of interest, what exactly crashed?

---

### Post by pous on 2010-02-02
i really dont know, but i guess it had to do with the last recomended update... I had just downloaded some updates witnout restarting a day or two before...

---

### Post by chaanakya_chiraag on 2010-02-02
Windows or Ubuntu?
Edit: silly question :D  Of course it must be Windows :D (Right??? :P)

---

### Post by pous on 2010-02-02
unfortunatley not, i havent used windows at home in the last 6 or so months... I was running 9.04 and installed the recomended updates that popped out while watching some movie online the last time I could actually log in...

---

### Post by themusicalduck on 2010-02-02
Actually wubi does use grub. It chainloads grub from the windows bootloader. I had this same problem with a laptop recently after updates.

I was able to fix it following the steps outlined here - [http://ubuntuforums.org/showpost.php?p=8444565&postcount=10](http://ubuntuforums.org/showpost.php?p=8444565&postcount=10)

But instead of using the command ```
sudo update-grub2
``` after booting in, it should work with just ```
sudo update-grub
```

EDIT: Just realised you have 9.04 so you probably have the old grub installed.

Those commands might let you boot into ubuntu, but you might need to do something other than sudo update-grub to fix the problem.

---

