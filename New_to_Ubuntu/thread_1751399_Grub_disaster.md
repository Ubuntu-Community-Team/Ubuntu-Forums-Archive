---
title: "Grub disaster"
date: 2011-05-06
forum: New to Ubuntu
---

### Post by 645dood on 2011-05-06
Hi, I have Win7 & Ubuntu 10.04.2 LTS on my PC (Win7 first). I went through the install process installing them side by side all was well when I was prompted to restart I did so to my amazement there is no GRUB/dual boot screen. I installed the live cd again and went back in to Ubuntu, I can see GRUB in a folder...what can I do to fix this, many thanks, Alex

---

### Post by wilee-nilee on 2011-05-06
So from a booted live Ubuntu cd, thumbdrive, or Ubnutu installation lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the **(#)** in the reply panel this makes code tags paste all the text in between.

This will give us a look at what's going on without a lot of questions.;)

---

### Post by 645dood on 2011-05-06
Hi, I can't seem to get the program to work.

---

### Post by Quackers on 2011-05-06
Did you download the boot script to your desktop? Or to Downloads?

---

### Post by 645dood on 2011-05-06
Thanks, downloaded to Firefox Download.

---

### Post by wilee-nilee on 2011-05-06
> **645dood said:**
> Thanks, downloaded to Firefox Download.

Drag it to the desktop open a terminal and run this command and please look at my first post and follow the instructions on using [COLOR="Red"]code tags[/COLOR].
```
sudo bash ~/Desktop/boot_info_script*.sh 
```

---

### Post by jtarin on 2011-05-06
Are you still able to boot into Win 7? Refer to EasyBCD in my signature and let me know if your interested.It is a way of booting Ubuntu and leaving your MBR alone without a Grub install to it. You will still need to know where your Ubuntu is installed (partition).

---

### Post by 645dood on 2011-05-07
Hi Jtarin, yes I am able to boot into win 7 without a problem. Yes very much interested thought I have Ubuntu installed alongside on Win 7 is this a problem. let me know more please. thank you.

---

### Post by jtarin on 2011-05-07
> **645dood said:**
> Hi Jtarin, yes I am able to boot into win 7 without a problem. Yes very much interested thought I have Ubuntu installed alongside on Win 7 is this a problem. let me know more please. thank you.No its not a problem....only problem you have at this point is knowing where your Ubuntu partition is. Find that and download EasyBCD in Windows then PM with your email address when you have that done and I will send you documentation and links for setting this up.

---

### Post by 645dood on 2011-05-07
Hi jtarin, I believe the Ubuntu partion is: /dev/sdb1 which I allocated 100GB to. There is an entry for 847.04GB /dev/sdb2 NTFS which I know is for Win 7. There is also /dev/sdb3 with a key along side extended 84.38GB. Does this sound right. If I pick the wrong partion what are the consequences. my email: [email]anpp2005@gmail.com[/email]. I have been looking at wubi do you think this is a better option or not. Thanks.

---

### Post by jtarin on 2011-05-07
> **645dood said:**
>  If I pick the wrong partion what are the consequences. my email: [email]anpp2005@gmail.com[/email]. I have been looking at wubi do you think this is a better option or not. Thanks.I don't recommend WUBI. If you choose the wrong partition it won't boot until you choose the correct one, but first things first. 
[Reinstall Grub to the partition you have ubuntu installed on.]("https://help.ubuntu.com/community/Grub2#METHOD%203%20-%20CHROOT")
Using the CHROOT method.At step 9 it says "Do not specify a partition number"....**_in your case do specify the Ubuntu partition number._**    
**_[COLOR="Red"]Do not execute step #10[/COLOR]_**. 
Step #15 reboot into Win7 and install EasyBCD choosing the partition for Linux as the one where you installed Grub. 
The Windows Boot manager will chainload Grub after the EasyBCD install. PM me for any additional help.

---

### Post by 645dood on 2011-05-09
Hi jtarin, This may be a stupid question but where do i find my Ubuntu partion in 11.04. I can see NTFS which I believe is my Win 7 partion. Thanks again.

---

### Post by manicol on 2011-05-09
I had the same problem when I installed windows after Ubuntu.

What I did was to boot ubuntu from  CD Live.
You may need to tell the bios to boot from disk first.
Then when CD Live of Ubuntu has booted tipe in a terminal:

*sudo fdisk -l*

This will list all the partitions.
The partition you need to remember is the one with Linux as System. In my case it was /dev/sda6.

now mount this partition tiping:

*sudo mount /dev/sda6 /mnt*

then:

[I]sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys /mnt/sys[/I]

Do a chroot on your sistem, tipe:

*sudo chroot /mnt*

Now to install the Grub2 tipe:

[I]grub-install /dev/sda
update-grub2[/I]
To exit the chroot use Ctrl+D or tipe:

*exit*

Now you can unmount all devices:

[I]cd ~
sudo umount /mnt/dev
sudo umount /mnt/proc
sudo umount /mnt/sys
sudo umount /mnt/

[/I]Now restart your system and remove the Ubuntu disk.
The grub should be back at start-up.


I followed this tut when it appened to me, but it's in Italian:

[http://wiki.ubuntu-it.org/AmministrazioneSistema/Grub/Ripristino?highlight=%28grub](http://wiki.ubuntu-it.org/AmministrazioneSistema/Grub/Ripristino?highlight=%28grub)

---

### Post by jtarin on 2011-05-09
> **645dood said:**
> Hi jtarin, This may be a stupid question but where do i find my Ubuntu partion in 11.04. I can see NTFS which I believe is my Win 7 partion. Thanks again.Step #3 of the link I gave you.

---

### Post by 645dood on 2011-05-09
Dear All, I really appreciate all you work trying to help me resolve Grub but nothing seems to be going my way....I have dual dooted Win 7 and Ubuntu many times previously with no problems what so ever but for some reason this time around it is a disaster. I can't seem to get it going so I will leave Win 7 on my PC and I do have Ubuntu 11.04 on my 4 yera old Dell Netbook which I have installed without a problem what so ever. Grub seems be be a big pig this time around maybe Ubuntu / Canonical should have put more effort into Grub. I realy don't want to be stuck with Win 7 but at the moment I have not choice...Thank you again...645dood

---

### Post by bennachie on 2011-05-09
Any of the methods outlined by previous contributors should work (I use a somewhat simplified variation of the one recommended by manicol). However, the brute force alternative, which would be better than resorting to Wubi, is simply to reinstall Ubuntu, this time selecting the option offered in the installer dialogue to have Ubuntu replace the existing Linux partition(s). 

Then you'll be back to a reliable dual-boot situation.

---

### Post by 645dood on 2011-05-09
Hi Bennachie, Thanks for replyiong, It has got up to the point where if I reinstall 11.04 it fails. I know the problem is Grub and since I am no expert at Ubuntu I am finding it very hard to fix. If I do fix it the wrong way I may screw-up my Win 7 system. Thanks again, 645dood.

---

