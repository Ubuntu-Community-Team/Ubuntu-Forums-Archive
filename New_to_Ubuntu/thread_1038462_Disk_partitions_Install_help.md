---
title: "Disk partitions Install help"
date: 2009-01-12
forum: New to Ubuntu
---

### Post by hok30 on 2009-01-12
Hey,
I tried Ubuntu yesterday on my old laptop using VirtualBox, and I am loving it. I tried to install it on my broken desktop (which used to run windows, but now just gives me an error when I try to boot up). I'm not familiar with different operating system, (although am familiar with windows) so I was proud of myself when I got it to even boot off of the LiveCD I burned. I got it finally to install (it made me wait like 3 minutes between each time I pressed Forward in the installer), I finally got it to the installing stage, and it loaded the first bar to 100 percent, but on the second bar, it stopped at 5 percent and gave me an error about disk partitions and writing the Ex3 system. It then redirected me to the disk partitioning section of the install, and it made me do a manual disk partition, but when I tried that, it told me that no Root System was selected. Help? :confused:

Thanks for reading that.

---

### Post by taurus on 2009-01-12
Do you want the installer to use the whole harddrive on that computer?  Open a terminal from the LiveCD and have a look at your disk layout.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by drs305 on 2009-01-12
If you selected manual partitioning, you will have to designate the / (root) and swap partitions. To do this during the partitioning setup, you select the type, size, location, use as, *and most importantly in this post*, the mountpoint. This is probably what you forgot to do.

Look at the link for a snapshot with the input box outlined in red:

I will also include the ubuntu documentation on installing, although it doesn't include pix of the partitioning process:
[https://help.ubuntu.com/community/GraphicalInstall]("https://help.ubuntu.com/community/GraphicalInstall")

For partitioning considerations, this is a good resource:
[http://www.psychocats.net/ubuntu/partitioning]("http://www.psychocats.net/ubuntu/partitioning")

---

### Post by hok30 on 2009-01-12
Thanks for your replies, but for some reason when I try to even use the LiveCD, I try pressing 'Use Ubuntu without any change to your computer', but it tries to load for a while, then I get a loop of black text that keeps coming down my screen.

---

### Post by hok30 on 2009-01-12
Do you think I could fix this by reburning a Ubuntu LiveCD?

Also, I'm running Windows right now, but don't have any install disks that I can find... I was wondering if anyone knew where I could get a windows ISO file that I could theoretically make a Windows LiveCD with, just to install it on the computer, then use Wubi to install it on Windows? Or, would even using windows for a day or two without buying that copy be illegal?

---

### Post by handydan918 on 2009-01-13
> **hok30 said:**
> Do you think I could fix this by reburning a Ubuntu LiveCD?

Also, I'm running Windows right now, but don't have any install disks that I can find... I was wondering if anyone knew where I could get a windows ISO file that I could theoretically make a Windows LiveCD with, just to install it on the computer, then use Wubi to install it on Windows? Or, would even using windows for a day or two without buying that copy be illegal?
Actually, if your box came from the manufacturer with windows, you likely have a license on a tag on the box somewhere. If you have a license, it is not illegal to install windows.

---

### Post by mkvnmtr on 2009-01-13
If you are not having any luck with the live Ubuntu disk you might need to tell us how much ram you have and the other specs of the unit.

---

### Post by hok30 on 2009-01-13
Well I'm not exactly sure now, because my Windows OS is broken, I haven't used the computer in ages... 

That shouldn't matter though. I just got the computer to work with the LiveCD. It seems for some reason it occasionally works, but most of the time doesn't. I'll try the terminal command.

---

