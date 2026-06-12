---
title: "Can I set root to a UUID in Grub2?"
date: 2010-01-05
forum: New to Ubuntu
---

### Post by bwallum on 2010-01-05
Hi

I would like to set root to a UUID instead of the (hdX,Y) format. This is because I am running Ubuntu on an external usb hard drive and connect it to a number of different machines with different hard drive configurations.

What I would like is a UUID version of the command ```
set root=(hdX,Y)
```

---

### Post by kansasnoob on 2010-01-05
Have you looked here:

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

I haven't tried what you're trying, when I run into problems I can't work around I revert:

[http://ubuntuforums.org/showthread.php?t=1298932](http://ubuntuforums.org/showthread.php?t=1298932)

I'm actually growing quite fond of grub2 but sometimes it's just easier to go back to something familiar.

---

### Post by kansasnoob on 2010-01-05
You may also find something helpful here:

[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

---

### Post by meierfra. on 2010-01-06
> This is because I am running Ubuntu on an external usb hard drive and connect it to a number of different machines with different hard drive configurations.

The default setup should already allow you to do that.  "root (hdx,y)"  will only be used if  the next line, namely "search --no-floppy --fs-uuid --set some_uuid", fails. Indeed, the only purpose of the search line is to determine the correct numbers for root. 

Also, if  Grub installed on the same hard drive as  Ubuntu, the numbers for root  will always be the same (unless you repartition the Ubuntu drive)

---

### Post by bwallum on 2010-01-06
> **meierfra. said:**
> The default setup should already allow you to do that.  "root (hdx,y)"  will only be used if  the next line, namely "search --no-floppy --fs-uuid --set some_uuid", fails. Indeed, the only purpose of the search line is to determine the correct numbers for root. 

Also, if  Grub installed on the same hard drive as  Ubuntu, the numbers for root  will always be the same (unless you repartition the Ubuntu drive)

The following is my menu entry in /boot/grub/grub.cfg generated from /etc/grub.d/10_linux (I think - not sure) to boot up my external usb hard drive. 

```
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	[COLOR="Red"]set root=(hd3,1)[/COLOR]
	search --no-floppy --fs-uuid --set fd0c6442-dc3d-49ba-8e46-91657460fe52
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=fd0c6442-dc3d-49ba-8e46-91657460fe52 ro   
	initrd	/boot/initrd.img-2.6.31-17-generic
}
```

I set the hard drive up on a computer that has 3 internal hard drives, hence it auto assumed the line [COLOR="Red"]set root=(hd3,1)[/COLOR]. The subsequent UUID lines contain the correct UUID for the first partition of the external hard drive, where 

The external hard drive works well on the machine that I configured it on. It does not work on other machines, it just hangs after the grub menu is displayed. I suspect it has something to do with the fact that other machines may have different hard drive configurations (say two internal drives, so the external drive root then becomes (hd2,1)).

Can I modify the [COLOR="Red"]set root=(hd3,1)[/COLOR] line to [COLOR="SeaGreen"]set root=UUID=fd0c6442-dc3d-49ba-8e46-91657460fe52[/COLOR]?

The filesystem is also ext4, is that significant? What does the insmod ext2 line mean?

---

### Post by meierfra. on 2010-01-07
I'm not sure that your problem is caused by Grub.

To get a better picture of the situation attach  the external drive  to one of the  machine where booting  fails and  follow these [instruction]("http://ubuntuforums.org/showthread.php?t=1291280")  for that machine.

---

### Post by bwallum on 2010-01-07
I couldn't attach the drive to the machine it fails on because it is a Windows XP machine and i don't know how to run bash scripts in Windows (if indeed that is possible)

I have attached the external hard drive to a Ubuntu machine, booted up on the external drive and then run the report as suggested.

The external drive is LABEL'ed UbuntuUSB. Grub files and os are located on the first partition. There is the usual swap file and also a vfat partition which I use for transfering files to/from Windows machines.

You will see that I have been playing around with grub menu entries in file 07_USBboot. They all fail on the Windows machine.

Does that help identify the problem?

---

### Post by meierfra. on 2010-01-07
> set root=UUID=fd0c6442-dc3d-49ba-8e46-91657460fe52?
The correct way to do this in Grub 2 is:

search --no-floppy --fs-uuid --set fd0c6442-dc3d-49ba-8e46-91657460fe52

But you are already using that. Maybe the search command fails for some reason.   Grub always considers the boot drive as "(hd0)". So the correct entry for root will always be:

```
set root=(hd0,1)
```


Lets  see what happens if  you remove the search lines and  make your menuentry as simple as possible:

menuentry "Ubuntu, Linux 2.6.31-17-generic" {
	insmod ext2
	set root=(hd0,1)
	linux	/vmlinuz root=UUID=fd0c6442-dc3d-49ba-8e46-91657460fe52 ro   
	initrd	/initrd.img
}

("insmod ext2" works for ext2, ext3, and ext4, so your ext4 partition should not cause any problems.)

---

### Post by bwallum on 2010-01-10
Hi again

I have now made the adjustments you suggested and attach a new report. The  external hard drive boots but seems to hang for around a minute 'loading grub'. The message on the screen says "[Linux-bxImage, setup=0x3400, size=0x362780]. There is a an underscore cursor just below the message but it does not blink. It stays that way for about a minute then continues to the Desktop.

One thing I find difficult to understand is that I specify (hd0,1) for my external drive boot partition and then find in device.map that my external drive is designated (hd3). I have deleted device.map and allowed it to regenerate but the change still occurs. Somewhere between grub loading and Ubuntu coming up the change is made and I don't understand why.

Thanks for the insmod and UUID advice. Having removed the search line is there somewhere I can see the various options for the search command so that I can understand it better.?

Greatly appreciate your help.

---

### Post by meierfra. on 2010-01-10
> the external hard drive boots but seems to hang for around a minute 'loading grub'. The message on the screen says "[Linux-bxImage, setup=0x3400, size=0x362780]. There is a an underscore cursor just below the message but it does not blink. It stays that way for about a minute then continues to the Desktop.

Does this happen on your Ubuntu machine or on your Windows maschine? Does booting from the Windows maschine still hang?

Since you removed the "set quiet=1" line, Grub2 now displays the messages you are seeing.  
Does booting take longer than it used too?

You might  replace

```
linux /vmlinuz root=UUID=fd0c6442-dc3d-49ba-8e46-91657460fe52 ro
initrd /initrd.img

```
by 

```
linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=fd0c6442-dc3d-49ba-8e46-91657460fe52 ro   
initrd	/boot/initrd.img-2.6.31-17-generic
```

/vmlinuz is a link to /boot/vmlinuz-2.6.31-17-generic.  So the second version should be slightly faster. But I doubt it makes any real difference.


> for my external drive boot partition and then find in device.map that my external drive is designated (hd3). I have deleted device.map and allowed it to regenerate but the change still occurs. Somewhere between grub loading and Ubuntu coming up the change is made and I don't understand why.

The device.map is only used  by "update-grub" to generated "grub.cfg"  (and also a little bit by grub-install)

But the device.map is not used in the booting process.

During booting, Grub sees the partitions in the same order as the bios.  So the drive you are booting from is always (hd0).  The second drive in the boot order of the bios is always (hd1), and so on. It does not matter what the device.map says.  That's why you have to use "(hd0,1)" in 07_USB_Custom

> the various options for the search command so that I can understand it better.?

search looks at the various partitions for something and then displays all the partitions where it found the something. There are three kinds of searches Grub2 can do


search -f  /some/file  (or search --file /some/file)

   This will display all partitions containing the file /some/file

search -u Some_UUID  (or search --fs-uuid Some_UUID )

     This displays all partition whose UUID is Some_UUID

search -l Some_Label (or search --label Some_Label)
        
      This displays all partitions whose label is Some_Label

You can add  a couple of options to "search"

-n  (or --no-floppy)  :
       tells grub  not look at the floppy drive when searching.

-s Some_Variable (or --set=Some_Variable)
    instead of displaying all partitions found, it sets the variable Some_Variable to the first partition found.

--set
    same as  --set=root

   
If you like to try out the "search" command:  Boot your Ubuntu maschine from the internal drive. Press "c" at the grub menu. That will give  you the grub shell. Type

```
insmod search
help search
```

That will tell you all about the  "search" command.

Type

```
search --file /boot/grub/grub/cfg
```

From your "RESULTS.txt" we know that /boot/grub/grub.cfg is on /dev/sda1 and on  /dev/sdd1.  Since you are booting from /dev/sda, /dev/sda will be (hd0).  I'm not sure what your external drive /dev/sdd is, but I would guess it will be (hd3).  So the output of "search --file /boot/grub/grub/cfg" should be

hd0,1
hd3,1

Next type

```
search --label Ubuntu_USB
```
Since /dev/sdd1 is your only partition with Label "Ubuntu_USB" the output  should be 

hd3,1

Type 

```
search --label --set=Hello Ubuntu_USB
```

This command will not have any output. Instead it set the variable "Hello" equal to "(hd3,1)". You can test this via

```
echo $Hello
```
The output should be 

(hd3,1).

Now reboot, but  boot from your external drive. Press "c" again and

```
search --label Ubuntu_USB
```
Since you booted from your external drive, /dec/sdd is now (hd0). So the output will by

hd0,1


Type

```
set root=(hd3,1)
```
This will have no output.
Type
```
echo $root
```
The output will be 
hd3,1

Type

```
search  --no-floppy --fs-uuid  fd0c6442-dc3d-49ba-8e46-91657460fe52
```
The output will be 

hd0,1

```
search --no-floppy --fs-uuid  --set fd0c6442-dc3d-49ba-8e46-91657460fe52
```

Since you used "--set" without  the name for the variable, it used "root" as the variable. So it sets  "root" equal hd0,1.  To confirm this

```
echo $root
```
The output will be 
hd0,1

So the "search" command did overwrite  your earlier "set root=(hd3,1)"


I suggest to also try the "search --no-floppy --fs-uuid  --set fd0c6442-dc3d-49ba-8e46-91657460fe52" at the grub shell when booting from the Windows machine.

You also might try

```
set root=(hd0,1)
linux /vmlinuz root=UUID=fd0c6442-dc3d-49ba-8e46-91657460fe52 ro
initrd /initrd.img
boot

```
in the Grub shell of the Windows machine  and see how far you can get.

---

### Post by bwallum on 2010-01-13
> Does booting from the Windows maschine still hang?
Unfortunately I no longer have access to the Windows machine.

> Does booting take longer than it used too?

When running Grub 0.97 booting from my USB drive, it was marginally quicker than booting from my harddrive. Caveat-I have subsequently changed the USB case (so the change in hardware may be significant).

These are my boot timings after selection from Grub2 menu:

From 320 GB SATA USB external Hard Drive:
Black screen with flashing cursor at top left - 40 seconds
Display of script - 25 seconds
Ubuntu splash - 15 seconds
TOTAL boot time 80 seconds

From internal 80GB SATA Hard Drive:
TOTAL boot time 25 seconds.

COMMAND LINE GRUB COMMANDS

These were great steers. I tried them all and gained a lot of understanding in how the search module worked. Using insmod I also tried a couple of other modules too.

One command I would add to your list is ```
ls -l
```It lists all the drives, partitions, names, UUID's and (hdx,y) style id. Great for cross checking the way drives are designated and mapped as Grub sees it.

Thanks for the advice re Grub does not use the device.map file when booting. I now know that when installing Grub I should configure the /boot/grub/device.map file first to ensure that when grub.cfg in auto generated including the 10_linux file then the correct (hdx,y) id is inserted.

I have been selecting the boot up drive from the bios boot menu (in my case by pressing the F11 key to evoke the menu prior to loading the os) and not by changing the order of the drives in cmos setup. Consequently when the os is loaded it takes the device map from the bios. Prior to the os loading Grub takes the priority from the boot menu. So Ubuntu sees (hd0,1) as the first partition on the first drive as listed in cmos. Grub2 at boot time sees (hd0,1) as the first partition on the first drive selected in the boot menu. Same notation but two different drives.

This has been a great learning point for me and I understand Grub2 much better now. I will give the new found knowledge a run on a Windows machine as soon as I get a chance.

Thank you very much indeed for the time and considerable effort you have afforded me.

---

### Post by bwallum on 2010-01-13
The dual boot scenario where Grub2 fails appears to be an ongoing problem, see[https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/441941?comments=all](https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/441941?comments=all)As mentioned above I don't have the Windows machine with me at the moment so can't check the current situation.

It does appear that there is a major issue with dual booting Windows using Grub2.

---

### Post by meierfra. on 2010-01-13
> It does appear that there is a major issue with dual booting Windows using Grub2. 

if you are dealing with two different operation system and  millions of possible  combination of bios and hardware, you will always  run  into some problems. But I have not seen any major issue. 

> [https://bugs.edge.launchpad.net/ubun...1?comments=allA](https://bugs.edge.launchpad.net/ubun...1?comments=allA)
 Some programs in Windows write data into the first 63 sector of the hard drive. (That area is reserved for booting purposes, so this  is not supposed to happen).  This destroys the  grub 2  boot code.    But that is not what is happening to you, otherwise you wouldn't  be able boot from your external drive at all.


> I will give the new found knowledge a run on a Windows machine as soon as I get a chance.
If you need some help in the future:  Attached your external drive to the Windows machine. Then boot from the Ubuntu Live CD, run the boot info script and post the RESULTS.txt

---

