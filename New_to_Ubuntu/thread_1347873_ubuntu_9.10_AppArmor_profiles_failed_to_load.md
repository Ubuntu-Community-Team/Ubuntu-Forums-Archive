---
title: "ubuntu 9.10 AppArmor profiles failed to load"
date: 2009-12-06
forum: New to Ubuntu
---

### Post by FwdVision on 2009-12-06
I have 9.10 installed in a partition on my laptop, Vista is on the other side.  Intermittently, Ubuntu booted up fine, but after I let my laptop battery power get low, it started to become intermittently problematic and now will not complete the boot process - During Ubuntu startup, this is the error i get: " AppArmor profiles failed to load " ...any ideas on how to address this?  Thanks!  I'm new to this OS, so I will need a detailed instruction of exactly what to do - thank you!

---

### Post by spiderbatdad on 2009-12-06
might help to see dmesg. Open terminal Applications>>Accessories>>Terminal.
Enter ```
dmesg > ~/Desktop/dmesg.txt
```Copy/Paste the contents here in code tags by clicking the # symbol in the editor. If the file is too big, you can right click it and choose create an archive. You can upload the archive with the manage attachment tool, below.

---

### Post by FwdVision on 2009-12-09
Thank you Spiderbatdad, I appreciate this help.  A question for you:  Do you want me to open the terminal (as described below) on the windows partition, or do you want me to open the terminal on the ubuntu partition side.  If on ubuntu, how do I open the terminal?
 
Thanks!!
 
 
 
 
> **spiderbatdad said:**
> might help to see dmesg. Open terminal Applications>>Accessories>>Terminal.
Enter ```
dmesg > ~/Desktop/dmesg.txt
```Copy/Paste the contents here in code tags by clicking the # symbol in the editor. If the file is too big, you can right click it and choose create an archive. You can upload the archive with the manage attachment tool, below.

---

### Post by spiderbatdad on 2009-12-11
We are trying to discover what is happening during the boot process of your Ubuntu operating system that might prevent AppArmor profiles from loading...I was thinking you might be running a kernel with SELinux. So you want to boot Ubuntu. This has nothing to do with Windows.
Anyway, to open a terminal, you click on Applications (in your top panel, of a default desktop installation) then you you click on Accessories. Then you click on Terminal. So: Applications>>Accessories>>Terminal.

After you run the dmesg command and write it to a file with the command dmesg > ~/Desktop/dmesg.txt   (and you must use proper case sensitive letters.) then you will right click the file that gets written on your desktop, and you will select "compress." The default might be .tar.gz. That is fine. Upload that compressed file in to a post using the "manage attachment" tool found by scrolling down below the reply window. If you are editing a post and don't see a manage attachment option, you will need to click on "Go Advanced," located in the lower right corner of the reply window.

---

### Post by FwdVision on 2009-12-16
Hi Spiderbatdad,
 
Thank you for this great help; I will attempt this tonight.  I work full time (praise God) and am working on projects on the windows side of the partition, so it took me a few days to address this Ubuntu issue.  I would like to participate with Ubuntu, and the open source movement, so I hope to get this confingured properly and I apreciate your magnanimity in assisting me.
 
Kind regards

---

### Post by cesium62 on 2009-12-25
I'm confused.  If the system won't boot, exactly how are we supposed to click on the non-existant gnome menu?  And why would we look in some random user's home account for debugging information?

---

### Post by cesium62 on 2009-12-25
For me, the app armor message appeared somewhere in passing, and my problem may or may not be related.  My boots were hanging as well.  I was able to boot to recovery mode.

I resolved my problem by booting the recovery kernel, and selecting the "repair" option. After 15 to 30 minutes and answering a couple of prompts, the repair finished. The system them rebooted normally.

---

### Post by FwdVision on 2009-12-25
Hello,

Thanks for that idea; can you please tell me how to boot the recovery kernel, and I'll try the same process.

Thanks and Merry Christmas and Happy Holidays to you.

---

### Post by RodGer GR on 2009-12-31
> **FwdVision said:**
> Hello,

Thanks for that idea; can you please tell me how to boot the recovery kernel, and I'll try the same process.

Thanks and Merry Christmas and Happy Holidays to you.
When you boot your computer, if you have more than one O.S. installed, there should be a GRUB (grand unified boot-loader) menu that lets you choose between between the OSs. If this menu doesn't come up by default, you can just press esc (or maybe shift) when you boot your pc to make it show up. In this menu you can find your currently installed kernel(s). If there is more than one, look for the latest release (according to the numbers accompanying the kernel line). Under this there must be a recovery option for that certain kernel. That's it. Press enter having highlighted this recovery kernel.

If you still have problems, please provide some feedback.

---

### Post by FwdVision on 2010-01-01
Hi Rodger,

Thank you for this excellent guidance; I see exactly what you're describing (GRUB), so I'll run the recovery kernel as you indicate.
A question for you: when I run the recovery, should my expectation be that it could take 30 min to 1 hour, or even many hours for the recovery process to happen, or should I be expecting just moments or minutes for the process to complete?
I had tried the recovery kernel in the past, but after about 30-45 minutes I shut it down because it seemed nothing was happening, but maybe I didn't allow it enough time, so I just want to get my expectations in order.
I will try the kernel recovery process tonight or tomorrow, so I appreciate your help with this!
Happy New Year and let's have a great 2010.

---

### Post by RodGer GR on 2010-01-02
Assuming that your computer has the proper memory, processor and disk resources (since you can run vista) the recovery process shouldn't last more than some minutes. When the recovery kernel loads you should choose the dpkg option to repair any broken software packages. When dpkg finishes, return to the recovery menu and choose the netroot option (being connected to the internet) give the command ```
sudo apt-get update
```to update your packages. After this, give ```
sudo apt-get --reinstall apparmor
```to reinstall the apparmor and finally give```
sudo reboot
``` to reboot your computer and test if the problem is fixed.

Inform us how did it go and if the problem is not solved we'll try something else.

Have a happy and creative new year everybody.

---

