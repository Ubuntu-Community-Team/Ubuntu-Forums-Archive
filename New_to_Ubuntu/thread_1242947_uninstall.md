---
title: "uninstall"
date: 2009-08-17
forum: New to Ubuntu
---

### Post by sockettman on 2009-08-17
Hey there, very newbi i have XP on one drive and have just installed ubuntu on a second, it means i have to open my pc to plug and un plug drives, it seems that with abuntu i cant play COD4 , watch tv or dvd's, send emails, so how do i uninstall ubuntu with the drive active, thanks

---

### Post by coldReactive on 2009-08-17
> **sockettman said:**
> Hey there, very newbi i have XP on one drive and have just installed ubuntu on a second, it means i have to open my pc to plug and un plug drives, it seems that with abuntu i cant play COD4 , watch tv or dvd's, send emails, so how do i uninstall ubuntu with the drive active, thanks

You can't, you have to reformat the drive using a format utility THAT WILL NOT INSTALL GRUB (Such as DBAN.) Then reinstall Windows.

Remember, Windows XP only has about 15-20 activation times over the internet available. After that, you must activate over the phone.

By the way, if you want to stay in ubuntu, [read this thread](http://ubuntuforums.org/showthread.php?t=766683) to get DVD playback.

To run windows programs: [go here and follow instructions](http://www.winehq.org/download/deb) then [read wine documentation](http://www.winehq.org/documentation)

---

### Post by Merk42 on 2009-08-17
You also should be able to do half, if not all of the four things you had listed.
Nonetheless, I'm not sure if you need to reinstall Windows.

Am I to understand you have Windows on one physically drive and Ubuntu on the other?
Do you have GRUB currently installed? Didn't Ubuntu detect windows when you installed Ubuntu?
or
Did you unplug your Windows drive when installing Ubuntu?
Meaning, if you swap your drives, are you still currently able to boot into Windows XP?

---

### Post by northern lights on 2009-08-17
DO NOT REINSTALL WINDOWS - it is most likely not necessary.

Merk's inquiry is sensible: Are the two OSs on two separate physical drives? If so, formatting the Ubuntu one to ntfs will suffice. Your Windows can do that without the use of second party software.

As for your bad Ubuntu experience:
- DVD support is easily added, see Merk's post
- COD4 is a Windows game and will not run under Ubuntu, just as you wouldn't expect it to run on Mac OS either
- Ubuntu comes with *evolution* (email client) installed, *thunderbird* can be added
- webmail: browser, OS unspecific
- post your tv-tuner's make and model, if you are still interested in getting it to work with Linux

As a general note: Please only give advice that you are certain of to be correct or make it clear that you're unsure.

---

### Post by sockettman on 2009-08-17
Hi yes, i did unplug windows drive, the prob now is if i have both drives connected nothing will boot, so i cant uninstall from windows or from ubuntu, i like look of ubuntu but everything is so complicated, even to install a graphics or tv card driver is a pain,as with emails i can recieve but not send it just hangs, maybe i will try it in a year or so.
cheers,

---

### Post by coldReactive on 2009-08-17
> **sockettman said:**
> Hi yes, i did unplug windows drive, the prob now is if i have both drives connected nothing will boot, so i cant uninstall from windows or from ubuntu, i like look of ubuntu but everything is so complicated, even to install a graphics or tv card driver is a pain,as with emails i can recieve but not send it just hangs, maybe i will try it in a year or so.
cheers,

It won't get any uncomplicateder

---

### Post by northern lights on 2009-08-17
> **sockettman said:**
> Hi yes, i did unplug windows drive, the prob now is if i have both drives connected nothing will boot, so i cant uninstall from windows or from ubuntu, i like look of ubuntu but everything is so complicated, even to install a graphics or tv card driver is a pain,as with emails i can recieve but not send it just hangs, maybe i will try it in a year or so.
cheers,

Understandable. I'd like to say that Linux only appears unintuitive because users are used to the way Windows works. Still the (attempt of a) switch can be strenuous and frustrating. Give it a shot some other time when you have more to spare, maybe.

As for the actual problem:

If you're windows drive was not connected while installing Ubuntu on the other, it is not listed in your bootloader's ('GRUB') menu.

Either boot Windows and connect the other drive thereafter (external casing present?) or boot from any LiveCD. The Ubuntu one can do it, Knoppix for instance would be predestined. Wipe the drive with a partitioning tool such as *gParted*. You could even boot into Windows setup, format the drives and cancel the setup before starting the actual installation process. Up to you.


[EDIT]
> **coldReactive said:**
> It won't get any uncomplicateder
A. If you had used Breezy or Dapper you'd know that it constantly does.
B. The comparative of 'uncomplicated' is 'more uncomplicated'...
C. The above 'general note' (pretty much directed at you in the first place) still holds.
[/EDIT]

---

### Post by Merk42 on 2009-08-17
Well at this point you have 3 options.

1. Erase Ubuntu
2. Keep Ubuntu and let us help you figure out the differences
3. Erase and Keep Ubuntu.  Meaning reinstall it (or just GRUB), but with both drives present in your system so that you can easily boot either Windows XP or Ubuntu without going inside your computer.

To erase Ubuntu use the LiveCD.  The LiveCD is the default CD to burn from Ubuntu's site, most likely what you may have used to install in the first place.
Put that in the computer, with the Ubuntu drive connected to make things easier, and turn it on.
Try Ubuntu without any change to your computer.
Once it starts go to System > Administration > Partition Editor
Any partition that say EXT3, or EXT4 or SWAP, right click and delete (you may have to 'swapoff' the swap ones).
One all one big unallocated space, right click and make a new partition, this time as NTFS.  Let it do it's thing and you're done.

---

### Post by egalvan on 2009-08-17
It's no more complicated than XP was,
the difference is that you have experience with XP.

Some more modern computers will let you choose which drive to boot from..
it's called a 'boot menu', and different makes have different methods to access it...

but if you want to wipe ubuntu....

then connect the ubuntu drive.

get out the cd you used to install it with..

boot to the "Try Ubuntu without Installing" option.

run gparted

and make sure all partitions are unmounted...

right click on each and choose 'unmount'

then again right click on each and choose 'delete'

choose 'apply actions'

re-format with ntfs if you want.



Alternately

use Darik's Boot And Nuke
dban.org
to wipe the drive
BE SURE TO HAVE YOUR XP DRIVE DISCONNECTED...
YOU CAN WIPE THE WRONG DRIVE EASILY.


Alternately...

can you hook up both drives at once?

if so...

make the XP drive the boot one

boot and go to My Computer

try to access the ubuntu drive.

xp will complain that it
"cannot read the drive, do you want to format?"
choose yes

drive is formatted.


It's fairly easy to remove Ubuntu...

and it's probably as easy to fix most problems you may be having :)

---

### Post by coldReactive on 2009-08-17
> **northern lights said:**
> [EDIT]

A. If you had used Breezy or Dapper you'd know that it constantly does.
B. The comparative of 'uncomplicated' is 'more uncomplicated'...
C. The above 'general note' (pretty much directed at you in the first place) still holds.
[/EDIT]

I've been around since 7.10 or so, and yes, it's gotten less complicated, but I still find it very complicated.

---

### Post by sockettman on 2009-08-19
Sorry to be a pain, i now have a dual boot system so i can use xp and abuntu. on abuntu i have poor sound (xp using realtek HD) ubuntu (like a chrystal set) am still trying to install google earth and other things, no luck yet, also is it possible to watch u tube vids on this.
thanks.

---

### Post by oldos2er on 2009-08-19
> **sockettman said:**
> Sorry to be a pain, i now have a dual boot system so i can use xp and abuntu. on abuntu i have poor sound (xp using realtek HD) ubuntu (like a chrystal set) am still trying to install google earth and other things, no luck yet, also is it possible to watch u tube vids on this.
thanks.

 You'll need to install Flash to watch Youtube. Open up a terminal (Applications, Accessories, Terminal), and run
```
sudo apt-get update && sudo apt-get install ubuntu-restricted-extras
```
That will give you Java, Flash, mp3 codec, and some other goodies.

---

