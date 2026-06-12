---
title: "grub moving help in 10.10"
date: 2011-04-20
forum: New to Ubuntu
---

### Post by Bones2010 on 2011-04-20
How do I install the grub loader into the root of the drive so a third party boot loader will see the Ubuntu drive. I'm running Ubuntu 10.10 64 bit on a 1.5 tb hd and Windows 7 64 bit on a 1.5 hd and Mac os x on a 1 tb hd. The third party loader will pick up the Mac and Windows not Ubuntu. the drive poisoning is as follows:
sata 0 Mac os x
sata 3 Ubuntu 
sata 4 windows
sata 5 dvd burner

sata 1 and 2 empty

I tried booting from the cd and doing : sudo grub
grub> find /boot/grub/stage1
but can't do anything sudo from the live disk.

---

### Post by oldfred on 2011-04-20
Grub stage 1 is from old grub legacy not grub2. If you have UEFI, it is different. With gpt you need a bios_grub partition.

General info:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://www.gnu.org/software/grub/manual/](http://www.gnu.org/software/grub/manual/)
The Grub 2 Guide (formerly Grub 2 Basics)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD, Ubuntu install on sda5 and want grub2 in drive sda's MBR:
#Find linux partition, change sda5 if not correct:
sudo fdisk -l
#confirm that linux is sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda
# If no errors on previous commands reboot into working system and run this:
sudo update-grub

---

### Post by Bones2010 on 2011-04-20
I'm not sure what grub comes with Ubuntu 10.10 but I installed it on its own hd while the others were unplugged, as I did with all the other os's. What i"m trying to do is make a third party boot loader that is on the mac os hd see the Ubuntu hd so I can boot to mac, windows, Ubuntu. But the boot loader only sees windows and mac the Ubuntu is missing and the mac form I was on told me to move the grub to the root and the boot loader will see it. So what ever boot loader is standard with Ubuntu is the one I used when I installed it.

---

### Post by oldfred on 2011-04-20
If you installed Ubuntu to just that drive, then you have grub2 in the MBR. But Macs work with gpt. Did you format drive to gpt?

(I do not know details of Macs, there is a Apple sub-forum here).

If you want to see what is where, run this from Ubuntu liveCD.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.

edit - May be better to run this version which sees gpt partition better:
Get last development version of Boot Info Script:
wget -O boot_info_script.sh 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=boot_info_script.sh;hb=HEAD'

---

### Post by Bones2010 on 2011-04-20
no I just did the same mbr as always because i didn't know i could do a gpt format in Linux. I will try that but is windows 7 gpt to then because it's on its own drive and it is seen by the third party boot loader. just like the mac os. This is all installed on a gigybite h55m-s2v motherboard, it's not mac It's a pc Running a mac os, windows and ubuntu.

---

### Post by oldfred on 2011-04-20
Win7 will only boot MBR unless you have 64 bit and boot with UEFI.

I am not sure we can help if not a Mac.

Ubuntu Forums Code of Conduct
[http://ubuntuforums.org/index.php?page=policy](http://ubuntuforums.org/index.php?page=policy)

---

### Post by Bones2010 on 2011-04-20
Thanks for all your time I really appreciate it you have given me the info that helped open my eyes a bit and I thing I know what has to be done now so we can call this solved. Thanks again and I hope I can talk to you more about ubuntu, because i'm always learning and trying something new. I add you as a friend, and hope to talk to you again soon

---

