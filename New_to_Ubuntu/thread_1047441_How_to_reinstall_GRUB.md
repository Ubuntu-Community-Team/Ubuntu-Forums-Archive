---
title: "How to reinstall GRUB"
date: 2009-01-22
forum: New to Ubuntu
---

### Post by Gerinych on 2009-01-22
I've looked for something like this, but I haven't found anything for my problem. I screwed up my GRUB and I need to reinstall it. I have a Ubuntu Live CD with internet access. Now don't get me wrong, all those tutorials that tell you to use "sudo grub" and all those "find", "root (hdx,y)", "setup (hd0)" don't help me, they just tell you how to make MBR load GRUB instead of Windows' or anything else's bootloader. I actually screwed up the files in /boot/grub directory.
It started with me installing GRUB2. However, I didn't like it and replaced it with Legacy GRUB. For some strange reason, GRUB2 was still loading, so I did a complete removal of all GRUB2 packages, and it was still loading GRUB2, only now there was only one entry for memtest86+. So I used a Live CD to try to repair it using Super GRUB CD and now it gives me an error 21 (and sometimes error 2). In desperation, I booted Live CD again went into GRUB and used a bunch of root and setup commands and now I fear that the files in my /boot/grub directory are corrupted because of that. How do I repair those files?

---

### Post by Locke_99GS on 2009-01-22
Did you try *grub-install* with Legacy, yet?

---

### Post by cariboo on 2009-01-22
If you had followed the instruction to install grub from a LiveCD exactly, you wouldn't be in the state you are in now. Do you have a copy of /boot/grub/menu.list? There should also be a backup menu.lst file called menu.lst~. What was the problem with grub2? I have used it, but it is a pain to setup.

Could you paste a copy of /boot/grub/menu.lst in your next post.

Jim

---

### Post by caljohnsmith on 2009-01-22
> **cariboo907 said:**
> If you had followed the instruction to install grub from a LiveCD exactly, you wouldn't be in the state you are in now. 
I disagree. If you don't have the Grub boot files (stage1, stage2, stage1.5, etc) or if the Grub files are corrupt, you can't install Grub from the Live CD using the "sudo grub", "root (hdX,Y)", and "setup (hdX)" technique, just like Gerinych found out the hard way (since he had Grub2 installed). 

**Gerinych**, in order to troubleshoot your problem more accurately, I think it would help to get a clearer picture of your setup first; how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu Live CD desktop and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what it will take to get Grub working again.

---

### Post by Gerinych on 2009-01-22
I tried using grub-install on /dev/sdb (that's where my Ubuntu is), but it gives me this error: 
"Could not find device for /boot: Not found or not a block device."
I uninstalled GRUB2 because I didn't like it. I actually wanted to install grub-gfxboot, but I didn't know what it was called back then and it wasn't an official package, so it wasn't in Synaptic and I couldn't find it because of that. 
Here's my current menu.lst:
[http://pastebin.com/m542201fa](http://pastebin.com/m542201fa)
I think I ran update-grub on my installed Ubuntu when I could still boot it, so it kinda screwed up on the names and root commands. I don't have a menu.lst~ file for some reason, but I do have some other menu.lst backups that GRUB2 generated.
Here's menu.lst_backup_by_grub2_prerm: [http://pastebin.com/m10b90939](http://pastebin.com/m10b90939)
This is the only backup I remember having before GRUB2, all others have only 3 entries for Ubuntu for some reason.

---

### Post by KIAaze on 2009-01-22
I have no exact idea of how to reinstall Grub, but here are three crazy untested solutions to repair the grub files:
1)Boot from a live-CD, mount your HD, [chroot]("http://antionline.com/showthread.php?t=156511") into it to install/remove software
2)Get source tarballs and:
```
./configure --PREFIX=/rootdir && make && make install/uninstall
```
or
```
./configure && make && make install DESTDIR=/rootdir
```
3)Download the .deb packages and install to another directory using:
```
dpkg --root=<directory> PACKAGE
```
cf: [https://www.linuxquestions.org/questions/debian-26/install-with-apt-get-in-other-path-386763/](https://www.linuxquestions.org/questions/debian-26/install-with-apt-get-in-other-path-386763/)

---

### Post by pastalavista on 2009-01-22
Download, burn to disk and boot from a [SuperGrub Disk]("http://www.supergrubdisk.org/").

---

### Post by rwshoemaker on 2009-01-22
what crappy answers.  if you don't know, don't guess.

---

### Post by kansasnoob on 2009-01-22
If you want a guaranteed good outcome listen to caljohnsmith!

Really!

---

