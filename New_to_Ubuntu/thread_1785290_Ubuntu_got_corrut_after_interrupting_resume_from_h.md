---
title: "Ubuntu got corrut after interrupting resume from hibernation"
date: 2011-06-18
forum: New to Ubuntu
---

### Post by JnkPanchal008 on 2011-06-18
Hi All,

Few days ago I accidently interrupted resume from hibernation and now it does not boot. I am using Ubuntu 10.10.

it shows boot menu which shows different versions of kernals.
It can't boot from older kernals or even in recovery mode.
it just shows busybox command prompt.
And error is it can not mount device.

I tried fsck and install grub commands using live CD.

Did not work.
Also busybox says fstab is missing. and grub-install says that it can not open /dev/sda3

Please help what to do i don't want to re-install.

Thanx in advance.

---

### Post by wildmanne39 on 2011-06-18
> **JnkPanchal008 said:**
> Hi All,

Few days ago I accidently interrupted resume from hibernation and now it does not boot. I am using Ubuntu 10.10.

it shows boot menu which shows different versions of kernals.
It can't boot from older kernals or even in recovery mode.
it just shows busybox command prompt.
And error is it can not mount device.

I tried fsck and install grub commands using live CD.

Did not work.
Also busybox says fstab is missing. and grub-install says that it can not open /dev/sda3

Please help what to do i don't want to re-install.

Thanx in advance.Hi, run this boot script in a terminal and post the information from this script so we can see where everything is located:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans

Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.

---

### Post by JnkPanchal008 on 2011-06-18
Hi,

I ran that script and result is attached please find in attachments.

---

### Post by JnkPanchal008 on 2011-06-18
Also following is result of doing grub-install:

ubuntu@ubuntu:~$ sudo grub-install /dev/sda
/usr/sbin/grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?).

---

### Post by wildmanne39 on 2011-06-18
> **JnkPanchal008 said:**
> Also following is result of doing grub-install:

ubuntu@ubuntu:~$ sudo grub-install /dev/sda
/usr/sbin/grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?).Hi, I am doing some research on your problem, the boot script is not complete, it does not show fstab, so that is a problem that is what I am looking into.

---

### Post by wildmanne39 on 2011-06-18
> **JnkPanchal008 said:**
> Also following is result of doing grub-install:

ubuntu@ubuntu:~$ sudo grub-install /dev/sda
/usr/sbin/grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?).Hi, have you opened your fstab file to see what it looks like using the livecd?

---

### Post by JnkPanchal008 on 2011-06-18
Hi,

Actually from lice CD I can mount my other ntfs partitions but I can not mount my Ubuntu partition. SO I am not able to find what is wrong in there.

---

### Post by JnkPanchal008 on 2011-06-18
> **wildmanne39 said:**
> Hi, have you opened your fstab file to see what it looks like using the livecd?

I tried to access  /etc directory from busybox but I did not find fstab there. I think fstab has been deleted somehow.

---

### Post by wildmanne39 on 2011-06-19
> **JnkPanchal008 said:**
> I tried to access  /etc directory from busybox but I did not find fstab there. I think fstab has been deleted somehow.
Hi, I do too, I am going to ask a friend to take a look who is much more experienced then I am with this kind of  problem.

---

### Post by oldfred on 2011-06-19
It looks like boot script could not open sda6 either and if not able to mount it you cannot see if files are correct or not.

Try this from liveCD.

From liveCD so everything is unmounted,swap off if necessary, change sdb1 to your partition(s)
e2fsck is used to check the ext2/ext3/ext4 family of file systems.
sudo e2fsck -C0 -p -f -v /dev/sda6
if errors:
sudo e2fsck -f -y -v /dev/sda6

---

### Post by JnkPanchal008 on 2011-06-21
Thank u all for replying. :D

I used Smart Boot Manager software from [Hiren's Boot CD 14.]("http://www.hiren.info/pages/bootcd")

and it solved my problem.

Now everything is perfect.

---

