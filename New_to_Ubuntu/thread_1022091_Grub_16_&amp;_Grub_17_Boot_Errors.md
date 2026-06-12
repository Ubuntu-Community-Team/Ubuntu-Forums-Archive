---
title: "Grub 16 &amp; Grub 17 Boot Errors"
date: 2008-12-26
forum: New to Ubuntu
---

### Post by Doug11987 on 2008-12-26
Hi all,

I have just installed Ubuntu HH on my desktop computer, but when I rebooted it for the first HHD boot it came up with Grub error 16. I decided to restart it and then it came up with Grub error 17, then Grub error 16 again (on the third attempt to boot). 

Any ideas as to why this is? Please bear in mind that I am a complete beginner at this.

Thanks, Doug.

---

### Post by bumanie on 2008-12-26
The most common cure for a grub error 17 is to boot a live ubuntu cd  and follow [this thread]("http://ubuntuforums.org/showthread.php?t=224351")Prior to doing that, the grub 16 error needs to sorted out. The grub manual states that grub error 16 : > Inconsistent filesystem structure 
This error is returned by the filesystem code to denote an internal error caused by the sanity checks of the filesystem structure on disk not matching what it expects. This is usually caused by a corrupt filesystem or bugs in the code handling it in GRUB. There are two possible ways to fix this, that I know of;
A) Download gparted live cd and boot with it. Once opened, gparted should be able to do a check of your filesystem. Right click on your your hard drive  and choose the option "check" - gparterd will check your file system for errors.
B) If you have SATA hard drive/s, check that the cables are properly secured, poorly plugged in SATA cables have been known to cause this error.
Post back if you have any queries and someone will help. I'm at work and sometimes am called away.

---

### Post by Doug11987 on 2008-12-26
> **bumanie said:**
> Download gparted live cd and boot with it. Once opened, gparted should be able to do a check of your filesystem. Right click on your your hard drive  and choose the option "check" - gparterd will check your file system for errors.

What exactly should I be looking for here...? 

Thanks, Doug.

---

### Post by logos34 on 2008-12-26
You don't even need the gparted cd--just boot your ubuntu live cd and run this in a terminal:

sudo fsck /dev/sda1

or whatever the / partition is

---

### Post by caljohnsmith on 2008-12-26
You could do a file system check (fsck) from your Live CD; if you open a terminal (Applications > Accessories > Terminal), do:
```
sudo fdisk -l
```
That will show your drives and partitions, pick the one that is your Ubuntu install and do:
```
sudo fsck -yCM /dev/sdXY
```
And replace sdXY with the Ubuntu partition, for example sda2. Also, to get a clearer picture of your setup and what might be causing the problem, how about doing:```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post. That will help clarify your setup and hopefully what your problem might be.

---

### Post by kansasnoob on 2008-12-26
> Originally Posted by bumanie View Post
Download gparted live cd and boot with it. Once opened, gparted should be able to do a check of your filesystem. Right click on your your hard drive and choose the option "check" - gparterd will check your file system for errors.


What exactly should I be looking for here...?


Look at this screenshot:

[ATTACH]97659[/ATTACH]

You should note that I'm using Gparted (aka: Partition Editor) installed to my Ubuntu 8.10 **which you do NOT want to do!** You'll want to use Gparted either from an Ubuntu Live CD or burn a Gparted Live CD itself. On the Ubuntu Live CD environment it's at System > Administration > Partition Editor.

But you see in the upper right hand corner you can select which drive to work on (mine is on /dev/sda), then you see I've right clicked an unmounted partition and pointed to "check".

---

### Post by kansasnoob on 2008-12-26
> **caljohnsmith said:**
> You could do a file system check (fsck) from your Live CD; if you open a terminal (Applications > Accessories > Terminal), do:
```
sudo fdisk -l
```
That will show your drives and partitions, pick the one that is your Ubuntu install and do:
```
sudo fsck -yCM /dev/sdXY
```
And replace sdXY with the Ubuntu partition, for example sda2. Also, to get a clearer picture of your setup and what might be causing the problem, how about doing:```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post. That will help clarify your setup and hopefully what your problem might be.

Ah, always good to see you on the scene!

By all means, my best advice is listen to caljohnsmith!

---

### Post by egalvan on 2008-12-26
> **kansasnoob said:**
> Ah, always good to see you on the scene!

By all means, my best advice is listen to caljohnsmith!

+1 :KS

When it comes to boot problems, Mr caljohnsmith is THE MAN TO HEED!

Every bad boot I had was cured by his advice...

Much honor to Yoda, er, caljohnsmith!


All kidding aside, he is good.

---

### Post by egalvan on 2008-12-26
Of course, kansasnoob has been know to hand out sage advice.

From time to time.

Yes.

ErnestG

---

### Post by caljohnsmith on 2008-12-26
> **egalvan said:**
> +1 :KS

When it comes to boot problems, Mr caljohnsmith is THE MAN TO HEED!

Every bad boot I had was cured by his advice...

Much honor to Yoda, er, caljohnsmith!


All kidding aside, he is good.
Thanks Ernest, you are being too kind, because I certainly make my share of mistakes. Hope you had a wonderful Christmas, and hope your New Year will be even better. :)

---

### Post by Doug11987 on 2008-12-27
OK guys. The problem was that it wasn't working with my two HDDs. I removed the second one for the first boot and it worked fine. I have now re-attached it and it shows up as a media device. 

It's all working, so its fine!

Cheers, Doug!

---

### Post by egalvan on 2008-12-27
> **caljohnsmith said:**
> Thanks Ernest, you are being too kind, because I certainly make my share of mistakes. Hope you had a wonderful Christmas, and hope your New Year will be even better. :)

Well, it may be true that you make your share of mistakes,
but when the Good Lord was handing out shares, somehow or another, yours must have had a hole in the bottom, 'cause most of them leaked out.
Seem to have landed in my bag. I got more of them. Durned mistkaes..

:lolflag:

Seriously, many thanks for your insight into the arcane corners of boot, root and GRUB.

And Many Happy Returns
And may the New Year bring you New Hope, New Joy, and more Life to Love.

ErnestG

---

