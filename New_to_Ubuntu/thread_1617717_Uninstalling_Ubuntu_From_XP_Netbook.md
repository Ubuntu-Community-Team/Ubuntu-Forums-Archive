---
title: "Uninstalling Ubuntu From XP Netbook"
date: 2010-11-09
forum: New to Ubuntu
---

### Post by xswayx on 2010-11-09
Hi all,
Just new here and having difficulty with uninstalling ubuntu netbook from an acer aspire one netbook with xp.
I have no problems installing and running ubuntu/puppy(have a desktop with hardy heron and a laptop with puppy), however I have never had to remove it before!
I loaded it onto the netbook because xp was stuck in a continuos reboot loop.
Fixed the windows problem and I now need to remove the ubuntu, and have looked at loads of websites, but there all a bit too techy for me. (it's not my netbook otherwise I would just get rid of xp on it)

Can anyone please explain in simpleton terms how to remove it?
(I followed instructions from a couple of website and deleted it from disk management through xp.... then nothing would load - grub not found ... so reinstalled it)

There is no cd/dvd drive or xp disc etc, only a usb stick.

Any help would be greatly appreciated.

Many Thanks

---

### Post by wilee-nilee on 2010-11-09
You need to get a XP disc a legit one of course, and you can load a thumb with it fairly easily. What your trying to do without a XP disc is not good practice.

---

### Post by ppv on 2010-11-09
The MBR needs to be fixed. If XP is the only OS you intend to keep then you could give the following a try.

Create a bootable USB thumb drive for XP. You could google for this and only involves formatting the USB drive and running a utility.

After removing Ubuntu's partition from diskmgmt, boot using the thumb drive and use the recovery mode. At the prompt type FIXMBR.

Use proper caution with the commands as they overwrite the Master Boot Record.

---

### Post by wilee-nilee on 2010-11-09
> **ppv said:**
> The MBR needs to be fixed. If XP is the only OS you intend to keep then you could give the following a try.

Create a bootable USB thumb drive for XP. You could google for this and only involves formatting the USB drive and running a utility.

After removing Ubuntu's partition from diskmgmt, boot using the thumb drive and use the recovery mode. At the prompt type FIXMBR.

Use proper caution with the commands as they overwrite the Master Boot Record.

It is just best to have a XP disc/ISO you can actually do some very interesting things with it. Besides repairs you can also reload the XP install while saving the stuff on it, pretty cool really, if you like MS products.

Geez I missed the acer aspire one check this out.
[http://www.aspireoneguide.com/xpinstallu3.html](http://www.aspireoneguide.com/xpinstallu3.html)

You can load the thumb with this using this program
[http://wintoflash.com/home/en/](http://wintoflash.com/home/en/)

---

### Post by garvinrick4 on 2010-11-09
If you loaded Ubuntu from a USB stick. Take the USB stick and boot off of it.
Go to gparted right click on Ubuntu install and delete. Which will delete your ability
to boot using grub2. Right click on XP install and resize to take up the deleted partition
left by Ubuntu. Remember you must hit green apply arrow in gparted to initiate your commands. Now get out of gparted and then open a terminal in Ubuntu USB  and copy and paste these commands;
```
sudo apt-get install lilo
``````
sudo lilo -M /dev/sda mbr
```Will get an error ignore only need mbr
Now will boot boot into XP and drive is resized to take up complete drive.

If you want you can even install the lilo before you delete Ubuntu to secure fact you can boot into XP before you delete Ubuntu and resize XP. 
 Always back-up your personals before using partitioning tool on your HDD.

This is only if you do not have a XP disc or usb to install off of. And anytime you resize and do not have a install method for your Operating System, taking a chance.

---

