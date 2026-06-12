---
title: "Installation problem"
date: 2010-05-11
forum: New to Ubuntu
---

### Post by benclark on 2010-05-11
Hi there, I have a laptop running Windows 7 and yesterday I thought I would give Ubuntu a go installing it on one of my external hard drives (connected via USB) as I didn't want anything to affect my Windows 7 setup. Everything seemed to go smoothly but now my computer won't boot into Windows if I have the external drive unplugged and get some kind of "Grub" error?
 
My initial idea was to have a Windows computer running as normal and be able to run Ubuntu simply by plugging in the USB drive and rebooting, while the latter works fine I have essentially ruined the first option and am seriously considering using the restoration CD's to get my computer back the way it was originally.
 
Is there anyone that can help as I really don't want to do this but it seems I have no option as the Ubuntu installer it seems has messed things up with this "Grub" error. A laptop is hardly practical after all if you have to carry a USB external drive with you all the time.
 
Many thanks, Ben

---

### Post by adam22 on 2010-05-11
I don't know much about using multiple drives, I just dual boot on one drive.

However, the Grub error means the bootloader is not in place, which is why you're unable to select an operating system. I think that this may have been the result of having both drives mounted at the same time when installing (as a rule of thumb, it's best to remove external devices like SD cards and flash drives, as they will show up on the partition table). I have a feeling that this would not have happened if you disconnected the laptop hard drive when you installed.

As for getting this fixed, I think you're going to have to take a look at either restoring the Windows Bootloader and/or formatting and reinstalling that external drive. Not 100% on this answer, hoping someone can build on it.

---

### Post by benclark on 2010-05-11
Oh no I can select which operating system I want but I have to have the external drive plugged in otherwise it reports a "Grub" error and won't boot into anything. With the external drive plugged in it comes up with loads of options for how I want to boot.
 
All I want to be able to do is boot into Windows without that external drive plugged in or boot into Ubuntu with it plugged in, and if that can't be made to work then I'll be restoring my computer (not fun) and throwing Ubuntu in the bin.

---

### Post by sundays211 on 2010-05-11
first off, grub is the 'bootloader' for linux. that is, it is the program that tells your laptop what os to boot from. it seams as though you have installed the bootloader into your external hard drive insted of your internal hard drive. 
Try entering this command into the termanal(note that you will need to use ubuntu to execute this command):
```
grub-install /dev/hda       
```

---

### Post by benclark on 2010-05-11
If its installed in the external drive then why is it reporting an error only when the external drive isn't connected, what has Ubuntu changed on my internal drive?
 
How do I bring the terminal up in 10.04? Sorry totally new to this and therefore a bit worried that I've totally screwed things up.

---

### Post by 3rdalbum on 2010-05-11
> **sundays211 said:**
> 
```
sudo grub-install /dev/hda       
```

Fixed it for you.

Ubuntu installs the first part of GRUB on the default boot disk (your internal hard disk) and the second part inside its own partition (in your case, the external). The command above puts it all into the internal hard disk.

If the first part can't find the second part, then you get such a problem as that you describe.

You can get to the terminal by booting the desktop CD and going to Applications > Accessories > Terminal.

---

### Post by sundays211 on 2010-05-11
to bring up the terminal in ubuntu you click the top-left button (applications) then the first option (cant remeber whic one that is) then click terminal. then simply type the comand that I said in the last post. if that doesn't work try adding 'sudo' before typing the rest.

---

### Post by benclark on 2010-05-11
Excellent thanks guys 3rdalbum thanks for the explanation too. Once I make this change will the default boot option be Windows? At the moment if I don't select anything within a short timeframe it boots into Ubuntu by default. Obviously with that on the external drive I want it to boot into Windows by default.
 
Just have to wait for my wife to wake up now so I can get into our room to try this out. I'll report back later to confirm it has worked!

---

### Post by sundays211 on 2010-05-11
changing the defalt-boot is something completely different, you probably don't want to try it quite yet as it is quite difficult to do (at least the way i do it is).

---

### Post by benclark on 2010-05-11
Ok guys that didn't work, after typing in "sudo grub-install /dev/hda" (without the quotes) and then entering in my password it came back with the error
 
/usr/sbin/grub-probe: error: cannot stat '/dev/hda'.
Invalid device '/dev/hda'.
Try '/usr/sbin/grub-setup -- help' for more information.
 
any ideas?

---

### Post by benclark on 2010-05-11
My laptop uses an internal SATA hard drive if that makes any difference, should I be typing "sudo grub-install /dev/sda"??
 
edit - I tried using "sda" instead, it says installation succeeded but made no difference, unplug the external drive, reboot and it still doesn't work!

---

### Post by sundays211 on 2010-05-11
can you still boot windows with the external drive plugged in?

basicly this is beyond me, i'm quite a newbie to linux myself. prehaps somebody els can help.

---

### Post by GregA on 2010-05-12
Installing any alternate Operating System on an external drive is somewhat more complex than simply accepting the Ubuntu default recommendations for setting up a dual boot system on one internal drive (in your case "sda").

So, as your windows OS and files are still intact, you may want to do a "typical" (dual-boot) install on your internal drive,  . . it's easier than what you tried, and Ubuntu will automatically re-write and fix grub2 for you (then you select the OS to boot up).   Then lastly, reformat your external drive to FAT32 so you can use either windows or linux to write data to it.

One final suggestion, . . . if the Ubuntu install seems a bit too complex for you, there's another Linux distribution called "Suse, version 11.3", which will do a dual-boot setup in a manner by which even a cave-man could do it.

---

### Post by benclark on 2010-05-12
Thanks for the replies guys, I had a feeling this would be more complex than it painted itself to be. I've taken the plunge though and spent last night backing up all my pictures and other documents and today will be using my system recovery discs. They supposedly restore your computer back to the way it was right from the factory and right now that's probably the best and safest option. I know my way inside-out around Windows but Linux is something beyond me right now, it paints itself as easy but requires everything to be fed to it in code via the terminal, I'm sure I'm among the few here but sadly I haven't been impressed.

---

### Post by sundays211 on 2010-05-12
I will make just one last post for those who may have found this page with a simular problem:

try to re-install ubuntu, but create a very small partion in the internal hard drive(1gb) and mount it as /boot when you choose which hard drive to install on.

---

### Post by benclark on 2010-05-12
Thanks for the help guys, I've restored my system, everything went smoothly (thankfully) and I am problem free again. It is a shame as I did want to give Ubuntu a go but this has firmly put me off for now. I think if I try again it will be on an old machine that I don't care about if I screw it up.

On the bright side doing the reset has given me another 2 months free Norton and 2 months free Office lol

---

### Post by kansasnoob on 2010-05-12
> **benclark said:**
> Thanks for the help guys, I've restored my system, everything went smoothly (thankfully) and I am problem free again. It is a shame as I did want to give Ubuntu a go but this has firmly put me off for now. I think if I try again it will be on an old machine that I don't care about if I screw it up.

On the bright side doing the reset has given me another 2 months free Norton and 2 months free Office lol

Well what happened is you installed grub to the mbr of the Windows drive which is almost undoubtedly /dev/sda (drive #1), and everyone here keeps telling you to reinstall grub to sda :(

I hope you didn't totally reinstall Windows! All you needed to do was restore the Windows mbr which can be done either with a Windows CD or an Ubuntu Live CD!

If you left Ubuntu on that external drive you could still get it booting by booting an Ubuntu Live CD, plugging in the external drive, then running "sudo fdisk -l" to determine the proper drive designation and the partition info for the Ubuntu partition.

Then you can simply follow the instructions here to install grub2 to the mbr of the external drive:

**How to restore the Ubuntu grub bootloader (9.10 and beyond)**

[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

But you must know where to install grub!

This happened in the first place because you didn't study enough before installing. When you get to the final installation screen where you get to review the installation info there's an Advanced button in the lower right hand corner.

If you have more than one drive you must tell the installer where to install grub. It always installs to sda by default:

[http://members.iinet.net.au/%7Eherman546/p22/036.png](http://members.iinet.net.au/%7Eherman546/p22/036.png)

It's almost never a good idea to install grub to a partition! Partitions end with a number, drives end with a letter!

You can chalk this up to two things, operator error, and absolutely horrid advice here on the forums!

I wish people wouldn't even try if they don't know what they're talking about :mad:

Also, if you're ever having a boot issue in the future, please post the output of the Boot Info Script:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by benclark on 2010-05-12
Hey thanks for the reply. I did try their advice to reinstall grub to sda (although they did all say hda), I believe the partition issue may of been the problem stopping it working. I have an HP laptop and they partition the main drive into 3 sections. The main partition, the smaller Recovery partition (essentially a hdd copy of the 3 recovery dvd's you can make) and a tiny HP Tools partition. I think I discovered afterwards that my windows partition was being referred to by grub as sda1.

If this is potentially a common problem which can be solved by going into an advanced tab I wish it was something more obvious to fix it. Advanced tabs are usually left alone unless you know what you are doing, a fairly common attitude amongst computer users world over. If this is something that is so important it can potentially really screw up things (as in my case) perhaps this should be removed from the advanced tab and put on the main install screen or have some kind of help file you can refer to as you go through the install. Kind of hard to check online after all while your still only installing your OS.

As for the advice given, I wouldn't say it was horrible, they were just saying what they felt in their opinion was the solution. Thanks for your help though, I think I may hold for the moment on wiping the external drive....

---

### Post by kansasnoob on 2010-05-13
> Hey thanks for the reply. I did try their advice to reinstall grub to sda (although they did all say hda)

And that was the problem! If you have only one internal drive it would almost certainly be sda, and the Ubuntu installer puts grub there by default anyway.

You only needed to restore the Windows mbr on sda and then identify what the designation is for the external by running "sudo fdisk -l". Then install grub2 to the mbr of the external drive.

Also, it is almost never a good idea to install grub to a partition rather than a drives mbr.

> If this is potentially a common problem which can be solved by going into an advanced tab I wish it was something more obvious to fix it. Advanced tabs are usually left alone unless you know what you are doing

Some assumption must be made that those working with multiple drives and/or multi-boots do know what they are doing. How can any installer just "know" where you want the bootloader installed?

---

