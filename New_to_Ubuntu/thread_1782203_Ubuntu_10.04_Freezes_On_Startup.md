---
title: "Ubuntu 10.04 Freezes On Startup"
date: 2011-06-14
forum: New to Ubuntu
---

### Post by tomsubt on 2011-06-14
Hello,, I cannot start ubuntu today, I was installing updates last night and it was taking a long time so I thought I could resume them today and I shut down the PC but it just freezes at startup, (cannot move mouse or anthing!  Any ideas? Thanks

---

### Post by candtalan on 2011-06-14
1) When you restart, does it work then?
2) can you try it with a live CD, does that work ok?
3) With installed version or live cd, does the disc utility show the hard drive is all clear?

---

### Post by tomsubt on 2011-06-14
When I restart all the icons come up but the mouse stays frozen in the middle of the screen. how can I get to the disc utility if is frozen?
I will have to find the cd its around here somewhere

---

### Post by wildmanne39 on 2011-06-14
> **tomsubt said:**
> When I restart all the icons come up but the mouse stays frozen in the middle of the screen. how can I get to the disc utility if is frozen?
I will have to find the cd its around here somewhere
Hi, boot into recovery and finish the upgrades.
```
sudo apt-get update && sudo apt-get upgrade
``` Here is a guide to boot into recovery mode.
[https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode)

---

### Post by tomsubt on 2011-06-14
I boot into recovery but at the bottom there is a blinking cursor so I tried to type the code in but nothing would type in??????????

---

### Post by wildmanne39 on 2011-06-14
> **tomsubt said:**
> I boot into recovery but at the bottom there is a blinking cursor so I tried to type the code in but nothing would type in??????????
Hi, did you enter your username and password?

---

### Post by tomsubt on 2011-06-14
There is nowhere to enter username or password the desktop comes up with the icons but the mouse wont move and I can do nothing with it?????

---

### Post by wildmanne39 on 2011-06-14
> **tomsubt said:**
> There is nowhere to enter username or password the desktop comes up with the icons but the mouse wont move and I can do nothing with it?????Hi, ok I see, see if you can get a terminal by hitting ctrl+alt+t if so enter those commands, if not hit ctrl+atl+f2 after it finishes installing restart by hitting ctrl+atl+del. If that does not fix it we will move on to the next step.

---

### Post by tomsubt on 2011-06-14
I hit ctrl+alt+t  and it did nothing, I tried hitting ctrl+atl+f2 and it did nothing, then I tried ctrl+atl+del and Nothing again.

When I bring up the Recovery screen it fills up with alot of stuff and as i mentioned a blinking cursor at the bottom but it wont let me type anything into it????

---

### Post by wildmanne39 on 2011-06-14
> **tomsubt said:**
> I hit ctrl+alt+t  and it did nothing, I tried hitting ctrl+atl+f2 and it did nothing, then I tried ctrl+atl+del and Nothing again.

When I bring up the Recovery screen it fills up with alot of stuff and as i mentioned a blinking cursor at the bottom but it wont let me type anything into it????
Hi, did you follow the link in my post #4 about which keys to hit to get into recovery mode?
If so and you still can not get recovery mode to work run this script and post the information from this script so we can see where everything is located:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans

Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.

---

### Post by tomsubt on 2011-06-15
I have the recovery on my boot options, thats the only way I can get into it, and has I mentioned at the bottom of the recovery screen it seems to be waiting for me to type in a command, but it will not except any letters from my keyboard??????????

---

### Post by wildmanne39 on 2011-06-15
> **tomsubt said:**
> I have the recovery on my boot options, thats the only way I can get into it, and has I mentioned at the bottom of the recovery screen it seems to be waiting for me to type in a command, but it will not except any letters from my keyboard??????????Hi, post the information from the boot script in my post #10 and follow the instructions. Boot the livecd click try then follow the instructions in #10

---

### Post by tomsubt on 2011-06-15
How can I post the Recovery screen info, everything is frozen, Also I cannot find the 10.04 disk, I did however find the 9.4, can I just install it then upgrade to 10.04?

---

### Post by wildmanne39 on 2011-06-15
> **tomsubt said:**
> How can I post the Recovery screen info, everything is frozen, Also I cannot find the 10.04 disk, I did however find the 9.4, can I just install it then upgrade to 10.04?
Hi, it is not as easy to upgrade 9.4 because it is out of date. I would make a disk of 10.04 ubuntu so you can use it to repair your system, or use it to reinstall which ever you want to do, but you will need to have another computer to make a copy, maybe a friends?

---

### Post by tomsubt on 2011-06-15
Yes, I have another second pc, where can I download the 10.04 from and after I make it and do I need a DVD or a regular cd will do? how do I get it to repair the pc I now have it on?  Thanks

---

### Post by wildmanne39 on 2011-06-15
> **tomsubt said:**
> Yes, I have another second pc, where can I download the 10.04 from and after I make it and do I need a DVD or a regular cd will do? how do I get it to repair the pc I now have it on?  Thanks
Hi, a regular cd will be ok. Dowwnload from here.
[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)
You should choose the 10.04 version.

---

### Post by tomsubt on 2011-06-16
I did not see the 10.04 version at the site you supplied so I decided to make a disk of the 11.4 and its almost completed

Can I install it right over the 10.04? If not how do I uninstall the 10.04? Thanks

---

### Post by wildmanne39 on 2011-06-16
> **tomsubt said:**
> I did not see the 10.04 version at the site you supplied so I decided to make a disk of the 11.4 and its almost completed

Can I install it right over the 10.04? If not how do I uninstall the 10.04? ThanksHi back up any files you want to keep onto an external drive,then manually reformat your partitions, if you choose to install a long side of it will keep 10.04 also and take up a lot more disk space. I am going to give you a link to help with partitioning, please be careful while partitioning.
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

---

### Post by tomsubt on 2011-06-17
Ok, I think I made a boo boo, I deleted the two partitions that ubuntu was using but when I restarted the pc I get this everytime>>>>  GRUB loading.
error: no such partition
grub rescue>

and there is a blinking cursor there at bottom there too, but I dont know what to type in it to restart windows, I dont have a recovery cd my recovery of windows is built into my HP oem machine and help would be apprecitated, Thanks

---

### Post by wildmanne39 on 2011-06-17
> **tomsubt said:**
> Ok, I think I made a boo boo, I deleted the two partitions that ubuntu was using but when I restarted the pc I get this everytime>>>>  GRUB loading.
error: no such partition
grub rescue>

and there is a blinking cursor there at bottom there too, but I dont know what to type in it to restart windows, I dont have a recovery cd my recovery of windows is built into my HP oem machine and help would be apprecitated, Thanks
Hi, if you deleted the partition while installing from the livecd, then you installed ubuntu it should be working. Did you install ubuntu from the livecd?

---

### Post by candtalan on 2011-06-18
> **tomsubt said:**
> Ok, I think I made a boo boo, I deleted the two partitions that ubuntu was using but when I restarted the pc I get this everytime>>>>  GRUB loading.
error: no such partition
grub rescue>


It sounds as if you deleted Ubuntu - gone. However, the boot entries in the startup area on the hard drive (the MBR master boot record) are still there and are pointing all the startup activities towards the non existent Ubuntu stuff.  All you have to do is 'repair' the MBR for normal Windows use, and then it will all just work (only) with Windows again.

There are various ways to repair the MBR. The conventional Windows way is to use a Windows CD or another utility. The Windows command for this is 
fixmbr, from a windows command line which is possible to get from booting from a Windows CD. There are a other utilities also which can do this.

---

### Post by tomsubt on 2011-06-18
Yes, but it was almost a year ago and it worked until now, I believe it was the 9.4 version, 
 i upgraded to 10.04
I deleted the two partition that were not windows but when I went back to start up windows all I get now is "Error no such partitions Grub Rescue>

I did make a new 10.04 cd but it will not install. 

Isn't there anyway to start windows from the Grub rescue screen?

---

### Post by wildmanne39 on 2011-06-18
> **tomsubt said:**
> Yes, but it was almost a year ago and it worked until now, I believe it was the 9.4 version, 
 i upgraded to 10.04
I deleted the two partition that were not windows but when I went back to start up windows all I get now is "Error no such partitions Grub Rescue>

I did make a new 10.04 cd but it will not install. 

Isn't there anyway to start windows from the Grub rescue screen?Hi, there is no way we can tell for sure what you have done with out having a look at your boot script information.

---

### Post by conbot on 2011-06-18
Try to get into console to try to configure the kernel to support whatever hardware you may need to be enabled to get your mouse running.

---

### Post by wildmanne39 on 2011-06-18
> **tomsubt said:**
> Yes, but it was almost a year ago and it worked until now, I believe it was the 9.4 version, 
 i upgraded to 10.04
I deleted the two partition that were not windows but when I went back to start up windows all I get now is "Error no such partitions Grub Rescue>

I did make a new 10.04 cd but it will not install. 

Isn't there anyway to start windows from the Grub rescue screen?Hi, what happened when you tried to install? did the live cd boot at all?

---

