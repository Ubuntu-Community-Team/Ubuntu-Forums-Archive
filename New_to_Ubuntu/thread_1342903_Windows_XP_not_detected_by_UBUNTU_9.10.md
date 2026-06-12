---
title: "Windows XP not detected by UBUNTU 9.10"
date: 2009-12-01
forum: New to Ubuntu
---

### Post by williamspajr on 2009-12-01
Just installed 9.10

I have always used an IDE hard drive for the operating systems, and a SATA hard drive for storing data. This has worked for previous versions of UBUNTU.

Windows XP is currently installed on the IDE primary hard drive - dev/sda1 (boot).

As I did not get the option to install 9.10 to the IDE drive I installed it on SATA hard drive - dev/sdb5.

Windows XP does not appear in the GRUB menu.

Any suggestions will be appreciated.

Patrick

---

### Post by kansasnoob on 2009-12-01
The first thing to try is simply go to terminal in Ubuntu and run the command:

```
sudo update-grub
```

---

### Post by Primefalcon on 2009-12-01
2 questions, did you clean install or upgrade from an earlier version, and do you know the version of grub your using

if not try

```
grub --version
```

---

### Post by williamspajr on 2009-12-01
I did a clean install. As usual, I deleted the previous Linux partitions before doing the install.

Prior to posting, I had already executed the command "sudo update-grub"
Following is the latest try:
$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-15-generic-pae
Found initrd image: /boot/initrd.img-2.6.31-15-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
done

The version is 1.97

---

### Post by namok on 2009-12-01
Paste the contents of the terminal after the command:```
dpkg -l | grep -i grub
```

---

### Post by QIII on 2009-12-01
Assuming you did not delete your XP partition ...

You may need to run os-prober.  However, I recently discovered that os-prober had some difficulty on one of my machines.  If the following does not work, you may have to edit 40_custom (not at my machine right now, but I will try to remember to check back in when I get home tonight) and then run update-grub or update-grub2.

But for now...

Install os-prober
```
sudo apt-get install os-prober
```You may be informed you have the latest.  Don't worry.  Just continue on.

Run os-prober
```
sudo os-prober
```Update GRUB2
```
sudo update-grub2
```Let us know if that helps.

Just as an aside, do you have a 64 bit machine or a 32 bit machine?  I noticed that you are using a PAE kernel.

---

### Post by williamspajr on 2009-12-01
Thanks for the input.

I rebooted Windows (used super grub disk) as my wife needed to use the scanner. I then downloaded and ran Western Digital's utility to check the hard drive - no errors were found. I am now erasing the hard drive with Darik's nuke and boot. Will do a fresh install of XP and Ubuntu. Will let you know the results when completed.

For your info, I successfully installed XP and 9.10 on another computer.

---

### Post by williamspajr on 2009-12-01
Success. Darik's N & B cleaned up whatever was causing the problem.

Thanks for your input.

---

### Post by Chame_Wizard on 2009-12-01
```
sudo fdisk -l 
```

always handy.

---

