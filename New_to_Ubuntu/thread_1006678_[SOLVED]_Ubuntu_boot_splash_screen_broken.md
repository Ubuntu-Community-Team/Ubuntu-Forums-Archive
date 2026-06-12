---
title: "[SOLVED] Ubuntu boot splash screen broken"
date: 2008-12-09
forum: New to Ubuntu
---

### Post by dansan on 2008-12-09
I run Ubuntu Studio 8.04. One day part of the splash screen disappeared. The first part, where the white sweeps back and forth through the blue letters, is the same, but the second sequence, where white fills in one letter at time, is gone. The screen goes black.

I still get to the login screen ok, so it's not major. Can't I download a new copy of the ubuntu-studio-splash file? Where?

Edit: Forget the above questions. I found [https://help.ubuntu.com/community/USplash]("https://help.ubuntu.com/community/USplash") and tried removing and reinstalling ubuntustudio-theme as well as installing a couple of others. Part 1 of all of them works fine, but Part 2 won't play.

Does a boot script control this? Maybe it got damaged. How do I find and fix this?

---

### Post by dansan on 2008-12-10
I posted this problem on the desktop environments forum [http://ubuntuforums.org/showthread.php?t=1006678]("http://ubuntuforums.org/showthread.php?t=1006678"), but maybe this one is more appropriate. I run Ubuntu Studio 8.04. One day the second part of the splash screen sequence stopped working. The first part, where the white sweeps back and forth through the black letters, is the same, but the second part, where white fills in one letter at time, is gone. The screen goes black, but I still get to the logon screen, so this isn't a major issue.

I tried removing the ubuntu usplash theme using SUM and replacing it with the Kubuntu theme. The pattern was the same. The first sequence with Kubuntu logo and bouncing bubble in the progress bar runs fine, but the second sequence with the progress bar slowing filling never happens. Just black screen and then the logon screen.

What controls the splash screen sequence? A script? Can someone tell me where to find it and perhaps show me what it should look like?

---

### Post by sayakb on 2008-12-10
Try:
```
sudo apt-get purge usplash && sudo apt-get install usplash usplash-theme-ubuntu
```

---

### Post by overdrank on 2008-12-10
Threads merged. :)

---

### Post by caljohnsmith on 2008-12-10
One cause of losing the usplash screen is if for some reason the UUID of your swap partition changed. You can check by doing:
```
sudo blkid -c /dev/null
cat /etc/fstab
cat /etc/initramfs-tools/conf.d/resume
```
Then check to see that the UUID of your swap partition, as given by the first command, matches that in the resume and fstab files. If it doesn't agree, the easiest solution I think is to simply change the UUID back to what it was originally:
```
sudo tune2fs -U $(awk -F"=" '{print $3}' /etc/initramfs-tools/conf.d/resume) /dev/[COLOR="Blue"]sdXY[/COLOR]
```
And replace sdXY above with the swap partition. That way you don't have to modify your fstab, resume file, and also you would need to update your initrd images after changing the resume file.

---

### Post by dansan on 2008-12-10
This looks like a promising approach. The first command spit out a UUID different from the second and third commands:

```
/dev/sda5: TYPE="swap" UUID="1b9a6515-563d-491f-a2fd-a30dbf039a14"
UUID=e9e79c70-228d-4c0d-87e9-a47ce68af0ff none            swap
RESUME=UUID=e9e79c70-228d-4c0d-87e9-a47ce68af0ff
```

From this I gather that the swap UUID was originally e9e79c70-228d-4c0d-87e9-a47ce68af0ff.

But when I run the tune2fs command, here is what comes back:

```
tune2fs 1.40.8 (13-Mar-2008)
tune2fs: Bad magic number in super-block while trying to open /dev/sda5
Couldn't find valid filesystem superblock.
```

What do I do about a bad magic number?


> **caljohnsmith said:**
> One cause of losing the usplash screen is if for some reason the UUID of your swap partition changed. You can check by doing:
```
sudo blkid -c /dev/null
cat /etc/fstab
cat /etc/initramfs-tools/conf.d/resume
```
Then check to see that the UUID of your swap partition, as given by the first command, matches that in the resume and fstab files. If it doesn't agree, the easiest solution I think is to simply change the UUID back to what it was originally:
```
sudo tune2fs -U $(awk -F"=" '{print $3}' /etc/initramfs-tools/conf.d/resume) /dev/[COLOR="Blue"]sdXY[/COLOR]
```
And replace sdXY above with the swap partition. That way you don't have to modify your fstab, resume file, and also you would need to update your initrd images after changing the resume file.

---

### Post by caljohnsmith on 2008-12-10
My mistake, I forgot you can only use "tune2fs" for ext2/ext3 partitions, so instead do:
```
sudo swapoff -a
sudo mkswap -U $(awk -F"=" '{print $3}' /etc/initramfs-tools/conf.d/resume) /dev/[COLOR="Blue"]sdXY[/COLOR]
sudo swapon /dev/[COLOR="Blue"]sdXY[/COLOR]
```
And replace "sdXY" with the swap partition. After doing the above commands, check with "blkid" again that the swap partition now has the same UUID as in the resume/fstab files. Let me know how it goes.

---

### Post by dansan on 2008-12-10
Yep, caljohnsmith, that worked perfectly. The boot splash returned to normal.

Many thanks!

---

### Post by dansan on 2008-12-10
> **LinuxIsInnovation said:**
> Try:
```
sudo apt-get purge usplash && sudo apt-get install usplash usplash-theme-ubuntu
```

Thanks for the suggestion. Since I'd just done a major simplification of my disk, including moving swap, I followed caljohnsmith's tip, and it worked.

Love the avatar, :lol:

---

### Post by caljohnsmith on 2008-12-10
That's great news, glad you have your splash back. Cheers and have fun with Ubuntu. :)

---

