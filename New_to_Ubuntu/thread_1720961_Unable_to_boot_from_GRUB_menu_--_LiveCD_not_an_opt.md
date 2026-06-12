---
title: "Unable to boot from GRUB menu -- LiveCD not an option"
date: 2011-04-03
forum: New to Ubuntu
---

### Post by ajwiddershins on 2011-04-03
Hey everyone -- I'm grateful for those insightful tips about posting. 

For  the record, I am extremely new to Ubuntu. To this, I will add that  oftentimes, heavy jargon is potently discouraging, so please refrain  from ibibing in that where possible, or just elaborate where terminology  is necessary. This will help me out a lot.

Here's what I can offer so far about what's going on:

[INDENT][FONT=Lucida Console]GNU GRUB version 1.98+20100804-5ubuntu3

Ubuntu, with Linux 2.6.35-28-generic
Ubuntu, with Linux 2.6.35-28-generic (recovery mode)
Ubuntu, with Linux 2.6.35-27-generic
Ubuntu, with Linux 2.6.35-27-generic (recovery mode)
Ubuntu, with Linux 2.6.35-25-generic
Ubuntu, with Linux 2.6.35-25-generic (recovery mode)
Ubuntu, with Linux 2.6.35-24-generic
Ubuntu, with Linux 2.6.35-23-generic (recovery mode)
Ubuntu, with Linux 2.6.35-22-generic
Ubuntu, with Linux 2.6.35-22-generic (recovery mode)
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)
[/FONT][/INDENT][INDENT][FONT=Lucida Console]
Use the .... keys ... *[FONT=Arial]blah blah[/FONT]* ... 'c' for a command-line.[/FONT]
[/INDENT]Booting in any of those (obviously not the memory tests) does not get me very far whatsoever. 

Booting into the first option, I get this:
[INDENT][*lots of stuff i don't understand... numbers, etc...*]
[FONT=Lucida Console]No init found. Try passing init= bootarg.

BusyBox v1.15.3 (Ubuntu 1:5.15.3-1ubuntu5) built-in shell (ash)
Enter 'help' for a list of built-in commands.[/FONT]
[/INDENT]
Then more happens a few seconds later (This part seems dependent on which boot i pick):

[INDENT][FONT=Lucida Console](initramfs) [   35.268040] atkbd serio0: Uknown key pressed (translated set 2, code 0xd9 on isa0060/serio0). 
[   35.268106] atkdbd serio0: Use 'setkeycodes e059 <keycode>' to make it known.
[   35.268717] atkbd serio0: Unknown key released (translated set 2, code 0xd9 on isa0060/serio0).
[   35.268681] atkdbd serio0: Use 'setkeycodes 3059 <keybode>' to make it known.[/FONT]
[/INDENT]After which a little cursor blinks innocently at me as though i should come pet it or something. Cute.

FYI:  The CD drive on the computer in question (hp pavilion dv2000) no longer  works. I've done the live CD thing on my external harddrive, but have  no idea how to access that from where I currently am. The treads I've  read up to this point all seem contingent on have that CD. 


That's all I can speak to for now. I'm happy to try just about anything.  If you need any more info. I'll do my best to provide that, as getting  this solved is a very high priority for me.

Thoughts??

---

### Post by drs305 on 2011-04-03
*ajwiddershins*,

Welcome to the Ubuntu forums and thanks for researching before posting.  :-)

What were you doing when the system failed?  Installing, reinstalling, adding a new kernel, etc?

Do you know the partition your Ubuntu system was on? If not, at the Grub menu press "c" to get to the grub prompt.

Type: ls
This should show you your drives and partitions. Your Ubuntu installation is most likely (hd0,1) if it's the only system, or (hd0,5) if you also have Windows. 

Figure out which one it is by experimenting with the values from above and try to find your system files. Substitute the values you found from the "ls" command above for the X and Y:
```
ls (hdX,Y)/
ls (hdX,Y)/boot  # Do you find a "vmlinuz" and "initrd" file?
ls (hdX,Y)/boot/grub # Do you see a lot of *.mod files?
```

---

### Post by dcsoldschool53 on 2011-04-03
Can you tell me word for word and number too, what the error message said?

---

### Post by ajwiddershins on 2011-04-03
Hey there, thanks for getting back to me!

> What were you doing when the system failed?  Installing, reinstalling, adding a new kernel, etc?It had shut down randomly, which it sometimes will do if it overheats. When I turned it back on, this is what happened.

As a side note, I'd attempted to update a few days prior and it hadn't worked fully: something about untrusted sources, I believe. I understand this may or may not have anything to do with the issue.

> Do you know the partition your Ubuntu system was on? If not, at the Grub menu press "c" to get to the grub prompt.

Type: ls
This should show you your drives and partitions. Your Ubuntu  installation is most likely (hd0,1) if it's the only system, or (hd0,5)  if you also have Windows. [FONT=Lucida Console]
[/FONT][INDENT][FONT=Lucida Console]grub> ls[/FONT]
[FONT=Lucida Console](hd0)  (hd0,msdos5)  (hd0, msdos1)[/FONT]

[/INDENT]> Figure out which one it is by experimenting with the values from above  and try to find your system files. Substitute the values you found from  the "ls" command above for the X and Y:
     Code:
     ls (hdX,Y)/
ls (hdX,Y)/boot  # Do you find a "vmlinuz" and "initrd" file?
ls (hdX,Y)/boot/grub # Do you see a lot of *.mod files? 

```
grub> ls (hd0)/
error: unknown filesystem.
grub> ls (hd0,msdos5)/
error: unknown filesystem.
grub> ls (hd0,msdos1)/
lost+found/ var/ etc/ media/ bin/ boot/ dev/ home/ lib/ mnt/ opt/ proc/ root/ sbin/ selinux/ srv/ sys/ tmp/ usr/ initrd.img vmlinuz cdrom/ initrd.img.old vmlinuz.old
grub> ls (hd0,msdos1)/boot
grub/ System.map-2.6.35-22-generic abi-2.6.35-22-generic
config-2.6.35-22-generic memtest86+.bin memtest+86.bin memtest86+_multiboot.bin
vmcoreinfo-2.6.35-22-generic vmlinuz-2.6.35-22-generic
System.map-2.6.35-24-generic initrd.img-2.6.35-22-generic
config-2.6.35-24-generic abi-2.6.35-24-generic vmcoreinfo-2.6.35-24-generic
System.map-2.6.35-25-generic config-2.6.35-25-generic abi-2.6.35-25-generic
vmcoreinfo-2.6.35-25-generic System.map-2.6.35-27-generic
initrd.img-2.6.35-25-generic vmlinuz-2.6.35-25-generic
config-2.6.35-27-generic abi-2.6.35-27-generic vmcoreinfo-2.6.35-27-generic
initrd.img-2.6.35-27-generic vmlinuz-2.6.35-27-generic
System.map-2.6.35-28-generic vmlinuz-2.6.35-28-generic
vmcoreinfo-2.6.35-28-generic abi-2.6.35-28-generic
initrd.img-2.6.35-28-generic config-2.6.35-28-generic
grub> ls (hd0,msdos1)/boot/grub


```.... yes -- there's a butt-tonne of *.mod files. [/FONT]

> Can you tell me word for word and number too, what the error message said?Sadly, no, as there was no error message that I saw.

---

### Post by drs305 on 2011-04-03
Since you are using Grub 2, there wouldn't be an error number if it is a boot issue. Only Grub legacy reports boot error numbers, Grub 2 leaves you at a grub or grub rescue prompt.

Let's see if we can get your system to boot by entering commands at the grub prompt. It may work if your files are intact and not corrupted.

Get back to the grub prompt and type these commands:
**Correction: Entries should be (hd0,1) in all commands below:**

First attempt:
```
set prefix=(hd0,5)/boot/grub
set root=(hd0,5)
insmod normal
normal
# If the grub menu doesn't appear:
configfile /boot/grub/grub.cfg
```
If you get your grub menu try to boot. (It may look the same as what you had, but try it anyway).

If that fails:
```
set prefix=(hd0,5)/boot/grub
set root=(hd0,5)
insmod (hd0,5)/boot/grub/linux.mod
linux /vmlinuz root=/dev/sda5 ro
initrd /initrd.img
boot
```

If it boots, run:
```
sudo update-grub
```

I'll be offline. If it doesn't boot, let us know specifically what happens if it doesn't produce the same errors you already posted. Good luck.

---

### Post by ajwiddershins on 2011-04-03
Hola:

Here's what I did. The code you offered is as follows:

set prefix=(hd0,5)/boot/grub
set root=(hd0,5)
insmod normal
normal
# If the grub menu doesn't appear:
configfile /boot/grub/grub.cfg
This I attempted. The grub menu did not appear. Upon entering the final line of the above code, I got "error: unknown filesystem"

So, I attempted to take a hint and entered this:
```
set prefix=(hd0,msdos1)/boot/grub
set root=(hd0,msdos1)
insmod normal
normal 
```

That got me to the grub menu, which is the same as what I had above, and is now duplicated.

From here, I attempted to boot from the first option ([FONT=Lucida Console]Ubuntu, with Linux 2.6.35-28-generic)[FONT=Verdana]. This brings me the same issues as before [/FONT](No itit ... bootarg... BusyBox... Enter 'help'... . etc[/FONT]).

I entered also the second suggestion you offered, for good measure 
set prefix=(hd0,5)/boot/grub
set root=(hd0,5)
insmod (hd0,5)/boot/grub/linux.mod
linux /vmlinuz root=/dev/sda5 ro
initrd /initrd.img
boot
... but ultimately got the same errors.

Thanks for your help so far. I am sleepy and incoherent and also retiring for the day. Will check back as soon as I can.

Peace.

---

### Post by oldfred on 2011-04-04
Was it not (hd0,1) that showed all the files. Try with ones.

set prefix=(hd0,1)/boot/grub
set root=(hd0,1)
insmod (hd0,1)/boot/grub/linux.mod
linux /vmlinuz root=/dev/sda1 ro
initrd /initrd.img
boot

---

### Post by drs305 on 2011-04-04
*oldfred*, You are exactly right! Guess I  saw what I expected to see. 

*ajwiddershins*
> I am sleepy and incoherent and also retiring for the day. Will check back as soon as I can.
Guess you weren't the only one. Use (hd0,1) in the commands.

---

### Post by ajwiddershins on 2011-04-04
Okay, let's see here...

[INDENT]set prefix=(hd0,1)/boot/grub
set root=(hd0,1)
insmod (hd0,1)/boot/grub/linux.mod
linux /vmlinuz root=/dev/sda1 ro
initrd /initrd.img
boot 	

[/INDENT]Same errors :(

---

### Post by drs305 on 2011-04-04
Assuming no system files are missing, my guess is that you need to run an fsck or e2fsck check on your Ubuntu partition to fix some errors, however, you are going to have to figure a way to be able to boot either a CD or thumb/USB drive to be able to do that.

When you say "I've done the live CD thing on my external harddrive," what do you mean. Do you have an ISO of Ubuntu on that drive? If so, and the external drive shows up when you type "ls" at the Grub prompt, we may be able to just boot the ISO directly from Grub without having to burn/use a CD. 

If you can provide the (hdX,Y) values and path perhaps we can get the LiveCD to run. For instance, (hd1,1)/iso/ubuntu-10.04-2-desktop-i386.iso

---

### Post by ajwiddershins on 2011-04-09
>  Do you have an ISO of Ubuntu on that drive? If so, and the external  drive shows up when you type "ls" at the Grub prompt, we may be able to  just boot the ISO directly from Grub without having to burn/use a CD. 

If you can provide the (hdX,Y) values and path perhaps we can get the  LiveCD to run. For instance, (hd1,1)/iso/ubuntu-10.04-2-desktop-i386.iso 	

Hey again everyone,

Internet and computer access for me has been pretty severely limited. Apologies for taking so much time to get back. 

An ISO of Ubuntu is on my harddrive. A good friend suggested I use a smaller thumb/flash drive because there is a chance it could be ruined. So, with this in mind, I've been waiting for their help as they have an ISO on a small flash drive that can be used instead of taking that greater risk. They'll be by to offer some advice on Monday.

As these things happen, I plan to post our successes or failures, when I can -- this way others with similar problems can access this information rather than it being a loose end. 

Thanks again for your help so far!

---

