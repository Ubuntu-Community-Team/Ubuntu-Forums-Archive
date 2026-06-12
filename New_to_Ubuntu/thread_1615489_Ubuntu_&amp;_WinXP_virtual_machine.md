---
title: "Ubuntu &amp; WinXP virtual machine"
date: 2010-11-07
forum: New to Ubuntu
---

### Post by MyD0j0 on 2010-11-07
Hello and thanks for the forums!

I'm trying to convert to Ubuntu while realizing that there are some things I will still need my WinXP to do for me.  I'd like to convert the winxp part to a virutal machine rather than side by side install (wireless lexmark printer and iDevices for example).  First, what is the best virtual machine to do these things in and second, how do i get my winxp disk imaged so that I can create a VM image?

---

### Post by tajiknomi on 2010-11-07
[I][SIZE=2]Welcome to forum...:P

you can use **Virtual-Box**  for that purpose...(how to use? follow the link [/SIZE][/I][http://www.youtube.com/watch?v=9-DiPRrE3Bg](http://www.youtube.com/watch?v=9-DiPRrE3Bg)[I][SIZE=2])

2)[/SIZE][/I][http://www.optimizingpc.com/howtouse/imagebootdisk.html](http://www.optimizingpc.com/howtouse/imagebootdisk.html)

---

### Post by P4man on 2010-11-07
+1 for virtualbox. but if you need to access USB devices from your VM, then you need the closed source PEUL version from oracle's website, not the opensource version in the repositories.

To migrate your existing XP to a VM, check this out:
[http://blog.paragon-software.com/?p=439](http://blog.paragon-software.com/?p=439)

---

### Post by MyD0j0 on 2010-11-08
> **P4man said:**
> +1 for virtualbox. but if you need to access USB  devices from your VM, then you need the closed source PEUL version from  oracle's website, not the opensource version in the repositories.

To migrate your existing XP to a VM, check this out:
[http://blog.paragon-software.com/?p=439](http://blog.paragon-software.com/?p=439)


Thanks for input from both [tajiknomi]("http://ubuntuforums.org/member.php?u=1146324") and [P4man]("http://ubuntuforums.org/member.php?u=412374").   I tried out the paragon software but after about 10 minutes into  creating the virtual disk, it errors.  I gave that a couple attempts,  un-installed/re-installed and still no success.  The virtual box web  site though has a HOWTO for migrating a windows disk to virtual box and  it discusses using dd as the program to create the image.  The howto  says not to capture just the partition though and I'm not certain what  is meant by that, so I'm not sure how to set my options using dd (and  I'd like not to trash my data).

Thanks, folks!

---

### Post by P4man on 2010-11-08
You didnt run out of diskspace running that paragon tool? Ive tried it a few times and it worked perfectly for me.

Anyway, dd is another way, but the problem with the dd approach is that windows doesnt boot from a different hdd controller than the one it was installed on. Once you move the image to a VM, the virtual hdd controller will be different from the one of your actual machine, and windows will bluescreen, 100% guaranteed, even safe mode. I think virtualbox website also explains somewhere how you can work around that, but you do need to do that.

As for capturing just the partition or the entire drive: 

dd if=/dev/sda4 of=whatever somemore options

will image partition 4 on drive sda. Problem with that is likely just that you dont get the MBR which has the windows bootloader.

if you do

dd if=/dev/sda of=whatever somemore options

That will image the entire drive sda (including MBR and all partitions on it). Which apparently is what you should do.

---

### Post by MyD0j0 on 2010-11-10
no, i'm only imaging an 80Gb drive and the target drive for the image file has 450Gb unused.  I'll try out the dd commands you helped with and see where that gets me.  Could be that this is a dell box (though I haven't looked very deep into yet).  Ubuntu 10.10 wouldn't install or run as livecd, so who knows until i get more time to look it all up.

---

