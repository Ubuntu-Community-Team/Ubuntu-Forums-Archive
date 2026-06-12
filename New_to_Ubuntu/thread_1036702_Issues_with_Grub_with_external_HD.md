---
title: "Issues with Grub with external HD"
date: 2009-01-11
forum: New to Ubuntu
---

### Post by cloudfrog on 2009-01-11
Hey everyone!

I recently installed Ubuntu to an external hard drive so I can run it on my work laptop without disrupting the windows-based computer.  The installation went incredibly smoothly, except for one hangup...  When I want to boot the computer normally into Windows, and I do not have the external hard drive plugged in, I get an error similar to the following:

"Loading Grub 2.5...

Grub 2.5 could not load.
Error 42"

Thats not exact, but it's rather close.  I tried moving the USB/External drive down on the boot menu in BIOS, and this did not resolve the issue at all.  If the external is plugged in, it gives me a simple options list regarding which kernel or OS I'd like to boot into, but this doesn't help me in the event that I return this laptop.  

Does anyone know what could cause this?  Is there a simple resolution?

Thanks everyone!  You've all been a huge help in my transition to Linux!

---

### Post by marshall.robert on 2009-01-11
this is because you should have taken out your laptop hdd if installing onto an external media.

if its just windows you have then you will need to boot off the windows disc. for xp you will need to get a console open and run fixmbr, for vista i found a nice guide here [http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD](http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD)

---

### Post by caljohnsmith on 2009-01-11
> **marshall.robert said:**
> this is because you should have taken out your laptop hdd if installing onto an external media.

if its just windows you have then you will need to boot off the windows disc. for xp you will need to get a console open and run fixmbr, for vista i found a nice guide here [http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD](http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD)
It is not necessary to remove the internal drive in order to install Ubuntu to an external drive while leaving the internal drive untouched. You can choose the drive where Grub gets installed to by clicking the "advanced" button near the end of the installation, and have Grub installed to /dev/sdb or whichever is the drive you are installing Ubuntu to. That way the internal drive is not modified in any way.

Cloudfrog, in order to fix your current dilemna, how about opening a terminal in Ubuntu (Applications > Accessories > Terminal) and do:
```
sudo apt-get install lilo
sudo lilo -M  /dev/sda mbr
```
That will reinstall a Windows MBR to your internal Windows drive so that you can boot directly into Windows with your external drive disconnected. Then to install Grub to your external drive, how about trying:
```
sudo grub
grub> find /boot/grub/stage1
```
The command above should return your main Ubuntu partition in the form of (hdX,Y) where X and Y are numbers, for example (hd1,0), but use whatever it returns as follows:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
Please post the output of all the above commands prior to doing "quit". Next if you reboot, set your BIOS to boot the external Ubuntu drive, you should be able to boot into Ubuntu if all goes well. If you have any problems, it might be that your Grub's menu.lst will need a little tweaking or something like that; so if you run into any problems let me know and we can work from there if you want.

---

### Post by cloudfrog on 2009-01-11
```
       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> find /boot/grub/stage1
 (hd1,0)

grub> root (hd1,0)

grub> setup (hd1)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd1)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd1) (hd1)1+16 p (hd1,0)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.

```


Looks good from my end.  I'll try a reboot to see if the problem still occurs.  I appreciate everyone's help so far.  The transition to ubuntu would have been far more frustrating without everyone.

---

### Post by cloudfrog on 2009-01-11
Okay, everything is almost working the way I'd like for it to.  The only problem is that now it wants to boot directly into Windows every time unless I edit the boot sequence in some way.  The strange thing is that it doesn't really matter how I edit the boot sequence, Grub will come up afterwards, but will not in subsequent times...strange stuff.

I'd be perfectly fine with Grub loading up at the beginning of every startup (whether I had the external connected or not), provided that it loads properly.

Thanks again everyone.

---

### Post by caljohnsmith on 2009-01-11
I'm glad you can at least boot Ubuntu now, but it sounds like what might be happening is you are using the BIOSes quick boot menu on start up to temporarily choose which drive to boot from. If you can go into your BIOS, there should be a "boot order" where you can permanently set the Ubuntu drive boot before the Windows drive. Anyway, that's just an idea, but cheers and have fun with Windows and Ubuntu. :)

---

### Post by cloudfrog on 2009-01-11
haha, thanks!

thats the issue.  when i power the laptop on, whether the external is connected or not, it boots directly into Windows, no matter what the boot order is.  Now if I go into BIOS and change the boot order at all, no matter what I changed it to, it boots into GRUB.  Very strange...

---

### Post by caljohnsmith on 2009-01-11
> **cloudfrog said:**
> haha, thanks!

thats the issue.  when i power the laptop on, whether the external is connected or not, it boots directly into Windows, no matter what the boot order is.  Now if I go into BIOS and change the boot order at all, no matter what I changed it to, it boots into GRUB.  Very strange...
That doesn't sound so bad, because you could add an entry in your Grub menu to boot Windows on the internal drive. If you want to give that a try, how about opening your menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
And at the very bottom add:
```
title       Windows XP
rootnoverify     (hd1)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1
```
And that will hopefully be all it takes to boot Windows from Grub, but let me know if you run into problems.

---

### Post by cloudfrog on 2009-01-11
Thats the other strange thing, Windows XP is listed in the GRUB menu when GRUB boots up.  I'm completely fine with that.  I'd prefer for it to boot into Windows if no USB storage device is plugged in, and if one is plugged in, I'd like for it to boot into GRUB and give me options as to which operating system and Kernel it boots into.

I may be describing all of this poorly  =)

Thanks for everyone's help.  You guys really have taken the sting out of the transition.

---

### Post by windy81 on 2009-07-10
have a look at this thread for a workaround, or atleast a way to understand grub a little bit better. 

[http://ubuntuforums.org/showthread.php?p=7595374#post7595374](http://ubuntuforums.org/showthread.php?p=7595374#post7595374)

---

### Post by koleoptero on 2009-07-10
When installing ubuntu, perhaps you can make a small partition at the end of your internal hard drive, and assign it to be /boot (you'll have to manually edit the partitions, hope you know how), then grub will be installed in the local and not the external drive.

THe size for the partition should not be more than 128mbyte, and ext3 would be a recommended option.

Doing that you'll be seeing grub every time your computer boots, whether you have the external drive installed or not. You can then make windows your default operating system through grub, and select ubuntu when you want to and have the external drive connected.

---

