---
title: "Grub2 - change root partition"
date: 2010-06-11
forum: New to Ubuntu
---

### Post by Snark1994 on 2010-06-11
[FONT=Tahoma]Hello, all...

Firstly, I'm not quite sure on the terminology for what I'm asking, as the extent of my knowledge on the subject a couple of hours ago was next to none... So apologies if it is misleading, I will try to explain what I *actually *mean (if it is different) now. This has also hindered my searching of the fora to try and find existing threads, so I'm sorry if this has already been asked...

Basically, I had a dual-booted 64-bit Ubuntu 10 & 64-bit Windows XP working fine. I then decided that I needed 32-bit Ubuntu 10 as well (a certain programme I wanted only ran under 32-bit). Unfortunately, while installing I forgot to tell it not to install a bootloader, so it overwrote my existing grub2. While this isn't that problematic, it does mean that if I want to edit my grub menu then I need to boot into 32-bit then back into 64-bit Ubuntu (as running update-grub under 64-bit doesn't actually alter the menu). So, my question is: how do I restore 64-bit Ubuntu as being the "controlling" partition for the grub menu?

I understand that under legacy grub you would use:
[/FONT]```

root (hdX,Y)
setup (hdX)
quit
```But under Grub2 *root* is a variable and *setup  *is apparently unnecessary, according to the list of commands... I've tried:
```

set root=hdX,Y
```and when I then type *set* I can see that it has edited the *root* variable, but if I then reboot the value resets itself. How do I make the change permanent?

Again, apologies if this has been asked before but I didn't really know which keywords accurately described what I was trying to do. Thanks in advance.

---

### Post by Jahocolips on 2010-06-11
Sounds like you could just reinstall Grub 2? I told someone how to do this for 9.10 here...

[http://ubuntuforums.org/showthread.php?t=1505818](http://ubuntuforums.org/showthread.php?t=1505818)

Same instructions (except looks for the 64 bit Linux), just use 10.04 live CD

---

### Post by garvinrick4 on 2010-06-11
[http://ubuntuforums.org/showthread.php?t=1506987](http://ubuntuforums.org/showthread.php?t=1506987)

Use comment #2

Use whatever your Ubuntu 64 bit partition # is.  To find out.
Open a Terminal and use this Code:

sudo fdisk -l  ( that is a small L)

After you lable in disk utilititys or gparted found under System/Administration
Use this to check out labels.

sudo blkid  (small L second letter)

If you do not have a seperate boot partition skip that step.

---

### Post by Snark1994 on 2010-06-11
Thanks, Jacoholips!  Thanks, too, to garvinrick4, but Jacoholips' instructions worked first time.

Just a note to anyone else who had this problem: the code given in Jacoholips' thread works, there are just a couple of typos. First, the '-' before 'root-directory' should have been doubled ('--root-directory', not '-root-directory'). Second, it's "umount" not "unmount". And finally, when it says "path", then (for me, at least) it means the /dev/(Linux) bit he referred to earlier on in the post, minus the number at the end... For me this meant:
```

sudo mount /dev/sda7 /mnt
sudo grub-install --root-directory=/mnt /dev/sda

```I managed initially to install grub on /dev/sda7 instead by using the --force option, but hopefully that won't do any lasting damage... #-o

Thanks again to all who responded so rapidly ;)

---

