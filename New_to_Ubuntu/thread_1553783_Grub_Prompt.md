---
title: "Grub Prompt"
date: 2010-08-15
forum: New to Ubuntu
---

### Post by koitaki on 2010-08-15
Anyone have any idea on how to boot up from the grub prompt please?

I bought Rickford Grant's "Ubuntu for Non-Geeks", installed Ubuntu 10.04 Lucid Lynx from the accompanying CD, and have spent the past day just trying to get a ubuntu os working.  I installed in tandem with windows, then went to the reboot and tried to run it from the prompt which allows me the choice of windows or ubuntu.  I then get the grub> prompt.

I've tried everything I've found from previous posts by well-meaning advisers and no luck for my system.

I don't know enough about grub, and I'm getting the feeling I've been sold a pup - i thought i was buying into a simple operating system but the range of solutions I've seen make it seem absolutely not for 'non-geeks' :)

For example, I've downloaded the wubildr file and put that in my C drive - no luck. I also tried overwriting the same file in c:\ubuntu\winboot.   All I get is a change in the grub prompt to 'sh:grub>'.

I think I've tried every possible variation of the various instructions people have written (eg. set root=(loop0), linux /boot/vmlinuz-2.6.31-14-generic, etc.)

I uninstalled that version and downloaded the ubuntu 10.04 straight from the ubuntu web site.  Same thing again.

So am at the stage now where I've not found any other ideas.  I'd love to get away from Windows, so if anyone has any constructive suggestions could you pleeaase provide them.

Many thanks in advance,
Chris

---

### Post by oldfred on 2010-08-15
Welcome to the forum.

Just to see where you are at, you can run this from liveCD you downloaded.:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

### Post by koitaki on 2010-08-21
Hi oldfred,

Thanks for looking at my issue and the reply.

Afraid to say, I couldn't get that to work.  I downloaded the boot_info_script055.sh but thereafter it all went a bit circular.

For example, I tried to boot Ubuntu again and it went to the sh:grub> prompt as per normal, and then no matter what I did I couldn't get any further with the boot stage. Eg. I tried following the instructions and typing in:

sh:grub> sudo bash ~/Desktop/boot_info_script*.sh

But it came up with error: unknown command 'sudo'
It did the same when I tried the alternative command which used 'su' instead of 'sudo'.

And according to the instructions on the boot_info_script page, I need to be able to boot up a Gnome desktop terminal so that I can copy the results file and post them back showing the problems with bootup.   Hence, because I'm stuck at the grub prompt, I just can't get to a desktop environment to run that script.

Incidentally, I leave the disk in my CD drive, but I *think* it seems to want to boot from my hard drive.

Maybe I'm doing something wrong with the bootup but that's what happened...

Cheers,
Chris

---

### Post by oldfred on 2010-08-22
IF you are at sh:grub> you are booting your hard drive not the liveCD. You have to boot liveCD and download the boot_info_script per the instructions. It may download in download or desktop directory and you then can run it from there.

AT sh:grub can you manually boot?

Display the drives/partitions known to GRUB 2.
ls #lists partitions

ls (hdX,Y)/    
Display the contents of the / folder of the designated drive/partition.

ls (hdX,Y)/boot    
Display the contents of the /boot folder. Example: ls (hd0,5)/boot



Manual boot:
Adjust drive, partition to your install:
ls (hd1,3)/
sh:grub> linux (hd1,3)/vmlinuz root=/dev/sdb3
sh:grub> initrd (hd1,3)/initrd.img
sh:grub> boot


            grub    grub2
sda1    hd0,0    hd0,1
sda2    hd0,1    hd0,2

sdb1    hd1,0    hd1,1

---

### Post by lkjoel on 2010-08-22
> **koitaki said:**
> Anyone have any idea on how to boot up from the grub prompt please?

I bought Rickford Grant's "Ubuntu for Non-Geeks", installed Ubuntu 10.04 Lucid Lynx from the accompanying CD, and have spent the past day just trying to get a ubuntu os working.  I installed in tandem with windows, then went to the reboot and tried to run it from the prompt which allows me the choice of windows or ubuntu.  I then get the grub> prompt.

I've tried everything I've found from previous posts by well-meaning advisers and no luck for my system.

I don't know enough about grub, and I'm getting the feeling I've been sold a pup - i thought i was buying into a simple operating system but the range of solutions I've seen make it seem absolutely not for 'non-geeks' :)

For example, I've downloaded the wubildr file and put that in my C drive - no luck. I also tried overwriting the same file in c:\ubuntu\winboot.   All I get is a change in the grub prompt to 'sh:grub>'.

I think I've tried every possible variation of the various instructions people have written (eg. set root=(loop0), linux /boot/vmlinuz-2.6.31-14-generic, etc.)

I uninstalled that version and downloaded the ubuntu 10.04 straight from the ubuntu web site.  Same thing again.

So am at the stage now where I've not found any other ideas.  I'd love to get away from Windows, so if anyone has any constructive suggestions could you pleeaase provide them.

Many thanks in advance,
Chris
On the prompt, just simply type:
```
help
echo "gonna boot"
exit

```
I do not get why you have to type "help" and "echo", but it doesn't work otherwise.

---

### Post by koitaki on 2010-08-22
Er...well spotted oldfred...apologies for not adding this information before.  I'll see if I can add all the information that may be relevant in this post.

1. I guess I'm not able to boot from the liveCD because it seems to keep ignoring that and going straight to the sh:grub> prompt.

I've tried a little bit of messing around with the BIOS (AMBIOS SETUP, copywrite 1999 American Megatrends Inc), changing the following settings:

Quick Boot: Enabled
1st Boot Device: CDROM
2nd Boot Device: CDROM
3rd Boot Device: CDROM
Try Other Boot Devices: Yes
Boot to OS/2> 64MB: Yes

But no matter what I've changed so far, it went straight to that grub prompt.
 
And thereafter, no matter what I type it just doesn't seem to boot.  Eg. boot, nil response.  Any of the other stuff you mention, it either does nothing or comes up with unknown command.

JFYI, I've got a new problem now, whereby my Windows ME seems to have gone awry too (it seems to go into a loop opening up a million instances of explorer when I get to the desktop) so I'll probably be absent this week sorting that out...*sheesh*

(Might even be worth my while trying to use my 2nd hard drive as my main bootup disk, so I'll have a crack at working that out)

Many thanks again for looking at the issue, much appreciated.
Chris



> **oldfred said:**
> IF you are at sh:grub> you are booting your hard drive not the liveCD. You have to boot liveCD and download the boot_info_script per the instructions. It may download in download or desktop directory and you then can run it from there.

AT sh:grub can you manually boot?

Display the drives/partitions known to GRUB 2.
ls #lists partitions

ls (hdX,Y)/    
Display the contents of the / folder of the designated drive/partition.

ls (hdX,Y)/boot    
Display the contents of the /boot folder. Example: ls (hd0,5)/boot



Manual boot:
Adjust drive, partition to your install:
ls (hd1,3)/
sh:grub> linux (hd1,3)/vmlinuz root=/dev/sdb3
sh:grub> initrd (hd1,3)/initrd.img
sh:grub> boot


            grub    grub2
sda1    hd0,0    hd0,1
sda2    hd0,1    hd0,2

sdb1    hd1,0    hd1,1

---

### Post by koitaki on 2010-08-22
Cheers lkjoel, thanks for looking at the problem.

I typed those instructions and it took me back to the reboot screen, and then ended up back at the grub> prompt :)

As I've said to oldfred, i think i got some new issues here that I'll now have to sort them out, so I'll be off for a little while, hopefully not too long, and then I'll come back.

Many thanks again,
Chris

---

### Post by lkjoel on 2010-08-22
> **koitaki said:**
> Cheers lkjoel, thanks for looking at the problem.

I typed those instructions and it took me back to the reboot screen, and then ended up back at the grub> prompt :)

As I've said to oldfred, i think i got some new issues here that I'll now have to sort them out, so I'll be off for a little while, hopefully not too long, and then I'll come back.

Many thanks again,
Chris
Can you boot into recovery mode? (Enter the Menu)

---

### Post by koitaki on 2010-08-29
Hi oldfred and lkjoel,

Update: I pulled apart my computer and after quite a few hours of messing around, learning about jumpers, masters and slaves, I managed to switch my hard drives around (I had an old one from 2000 and a 'new' one from 2005).

I then booted up again and voila, the purple screen of ubuntu appeared!

I'm afraid I don't have an answer to what was going on, but I think oldfred's comment about my pc evidently not booting off the cdrom tipped me off as to some problem there.  No idea what, but perhaps something going awry with the old master disk.

So, despite not really knowing what was wrong, the problem can be considered sorted.  

Many thanks again for your help oldfred and lkjoel, very much appreciated!! :)

Cheers,
Chris

---

### Post by oldfred on 2010-08-29
Glad you got it working. 

Older computers with IDE/PATA drives boot primary master. Newer SATA based BIOS let you choose boot drive in BIOS. My PC uses BIOS to choose but still calls it primary master even though it can be anyone of many SATA ports.

---

### Post by lkjoel on 2010-09-01
> **koitaki said:**
> Hi oldfred and lkjoel,

Update: I pulled apart my computer and after quite a few hours of messing around, learning about jumpers, masters and slaves, I managed to switch my hard drives around (I had an old one from 2000 and a 'new' one from 2005).

I then booted up again and voila, the purple screen of ubuntu appeared!

I'm afraid I don't have an answer to what was going on, but I think oldfred's comment about my pc evidently not booting off the cdrom tipped me off as to some problem there.  No idea what, but perhaps something going awry with the old master disk.

So, despite not really knowing what was wrong, the problem can be considered sorted.  

Many thanks again for your help oldfred and lkjoel, very much appreciated!! :)

Cheers,
Chris
Could you mark it as solved then?
Oldfred's signature tells you how.

---

### Post by koitaki on 2010-09-09
sorry for tardiness, didn't see your comments till just now lkjoel  - was over on page 2 :)

Ok, marked as solved now, thanks again for the assistance, really is appreciated having you folks voluntarily providing your time and help!

---

