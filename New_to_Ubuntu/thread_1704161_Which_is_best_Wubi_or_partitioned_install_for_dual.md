---
title: "Which is best: Wubi or partitioned install for dual boot"
date: 2011-03-10
forum: New to Ubuntu
---

### Post by Nickjpost on 2011-03-10
Good morning, all! I have been fortunate enough to get a new laptop and want badly to have Ubuntu installed along with Windows. I have a Dell Inspiron, i5, 8GB RAM, 750HD, Intel HD graphics. I am worried about partitioning windows, shrinking the available hard drive space to make room for Ubuntu, so I'm leaning towards Wubi install. I have never had a dual booted system, it's either been an Ubuntu system witha windows VM or vice versa. Is Wubi safe? Will it cause problems booting to Windows? I considered Ubuntu on a VM, but there are some things I cannot do on the VM that I can if Ubuntu is actually on the computer (ie, it will not see some devices and keyboard shorcuts are a pain to set up since certain combinations won't work) plus, a VM just isn't the same.  I need Windows for some programs and games that I like, but I just am in love with Ubuntu and desire to have it on my system. What is your advice, my Ubuntu brothers and sisters? Your advice is greatly respected and appreciated!

---

### Post by philinux on 2011-03-10
Dual boot.

Wubi is not meant for full time use. Only as another way of trialling ubuntu like the livecd.

Just make sure you defrag first and use windows to shrink it's partition.

Incidentally I use easybcd to boot ubuntu. I installed grub to the partition not the mbr.

Acer 1410.

---

### Post by el_koraco on 2011-03-10
wubi is fairly good, i tried it a few months ago when i bought a new laptop with win7 preinstalled, but it doesn't provide the full experience. 

there's the option of installing ubuntu alongside windows in the ubuntu installer, which does the job automatically. it creates an extended partition on which it puts root and swap, but no home partition. the upside is that it's automatic, so you don't need to partition manually in case you're scared of it. another downside is that it only uses the windows C drive, so you'll have to edit fstab if you want ubuntu to mount the windows D drive automatically at startup. 

another option is to use the windows disk management utilies, i'm not quite sure what they're called, leave room for ubuntu, and go on from there. that way you can create a root and home partition, which can be helpful in case you ever need to reinstall ubuntu and keep you current data. another upside is that you can specify how much of the hard drive you'll allocate to ubuntu. 

[link]("https://help.ubuntu.com/community/HowtoResizeWindowsPartitions#Resize%20the%20Windows%20partition") 

this is a nice overview of the process. 

of course, the best thing is to run a ubuntu only laptop, but that's another story :D

---

### Post by Nickjpost on 2011-03-10
Thank you both for your advise. I am weary of "playing" with a partition editor, so I think for now, I'll stick with a VM until I am thoroughly educated with it and run some experiments on my older laptops that I only use for experimentation and testing puposes. Thank you for the link also; that's exactly what I needed!! You both are appreciated!

---

### Post by george.wicked on 2011-03-10
wubi would be apt for your laptop considering at the max u can partition to only for primary drives and the first one will be taken by dell for its backup and rescue software and other functionalities installation and in no way you want to mess with that by playing with partition editor.. 

as always you can do the installing in logical drive but..

---

### Post by el_koraco on 2011-03-10
> **george.wicked said:**
> 
as always you can do the installing in logical drive but..

but what?

---

### Post by ssulaco on 2011-03-10
> **Nickjpost said:**
>  Is Wubi safe? Will it cause problems booting to Windows? 
Nick,I used Hardy as a Wubi install for about 8 months on my wifes computer and I honestly couldnt tell that much of a speed difference from a normal install,the reason I uninstalled it,I was running out of HDD space.
The reason I chose Wubi,like you,I didnt want to partition my wifes HDD
I say go for it.......
[http://www.psychocats.net/ubuntu/wubi](http://www.psychocats.net/ubuntu/wubi)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)
[http://www.ubuntu.com/desktop/get-ubuntu/windows-installer](http://www.ubuntu.com/desktop/get-ubuntu/windows-installer)
The method I used was the wubi installer already on the Live CD,pop in the live CD while your in windows,you should see autoplay window,click on run wubi.exe
and if you want to uninstall,just go to add/remove
good luck

---

### Post by Nickjpost on 2011-03-10
> **ssulaco said:**
> Nick,I used Hardy as a Wubi install for about 8 months on my wifes computer and I honestly couldnt tell that much of a speed difference from a normal install,the reason I uninstalled it,I was running out of HDD space.
The reason I chose Wubi,like you,I didnt want to partition my wifes HDD
I say go for it.......
[http://www.psychocats.net/ubuntu/wubi](http://www.psychocats.net/ubuntu/wubi)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)
[http://www.ubuntu.com/desktop/get-ubuntu/windows-installer](http://www.ubuntu.com/desktop/get-ubuntu/windows-installer)
The method I used was the wubi installer already on the Live CD,pop in the live CD while your in windows,you should see autoplay window,click on run wubi.exe
and if you want to uninstall,just go to add/remove
good luck
 
That's some great input, thanks! The draw back with Wubi is that I would be limited to 30GB, I just found. I think I will research paritioning and stick with the VM for now until I learn more.

---

### Post by ssulaco on 2011-03-10
Your welcome...yes there are drawbacks to using Wubi,but its a great alternative.
I just got done partitioning my new drive(XP)so I can install Lucid,waiting on new memory...used gparted live,simple as pancakes:)
I believe Vista and 7 have their own partitioning tools...

---

### Post by hank22077 on 2011-04-20
Deleting

---

### Post by hank22077 on 2011-04-20
> **philinux said:**
> Dual boot.

Wubi is not meant for full time use. Only as another way of trialling ubuntu like the livecd.

Just make sure you defrag first and use windows to shrink it's partition.

Incidentally I use easybcd to boot ubuntu. I installed grub to the partition not the mbr.

Acer 1410.


Happy to find this.
I'm new to understanding Ubuntu. I've used it before, but it was installed by someone else;
I was confused as to the exact difference between Wubi and DualBoot, but this helped clear it up for me!

Thanks!

---

### Post by SinkingRocket on 2012-08-12
wubi will install the OS same as installing it using a live cd.. just a different approach to different users.. i use to partition with my old laptop now ehn i got a new one i used wubi.. no issues ..the same experience

---

