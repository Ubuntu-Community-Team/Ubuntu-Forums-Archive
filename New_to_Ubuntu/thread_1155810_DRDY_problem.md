---
title: "DRDY problem"
date: 2009-05-11
forum: New to Ubuntu
---

### Post by Mr.Kuchinawa on 2009-05-11
Don't know exactly where to put this, but here goes:

Hi. Every time I try to boot ubuntu, I get the DRDY error. I have tried "e2fsck -f -c -v /dev/sda5" up to several times with system rescue cd, and I get *FILE SYSTEM MODIFIED* each time. However, It doesn't seem to do squat.

I know the HDD is not physically damaged, both because Win XP boots perfectly and because the machine has not been damaged in any way. 

Any help will be very much appreciated.

EDIT: Oh, and I have have also tried reinstallation

---

### Post by pro003 on 2009-05-11
did you scanned your drive for bad sectors? 

I have yesterday tried to install kubuntu on one older dell's box and I could not make it because of bunch of errors I got during installation and after installation, although win xp installs perfectly..

---

### Post by Mr.Kuchinawa on 2009-05-11
Isn't that what e2fsck does? If not, how do I do it?

---

### Post by pro003 on 2009-05-11
yes, but for linux partitions, you can run it with command **e2fsck -c**

---

### Post by Mr.Kuchinawa on 2009-05-11
Which is exactly what I stated that I had tried in the first post?

---

### Post by OffAxis on 2009-05-11
what filesystem did you install?
ext2, 3, or 4?

If you're up for another re-install you could opt for a different version (ext4 is the default for jaunty) and see if the problem persists.

---

### Post by Mr.Kuchinawa on 2009-05-12
I thought I had ext3, but if ext4 is default for jaunty, then I guess that's what I have. I will try to install it with ext3.

---

### Post by Mr.Kuchinawa on 2009-05-13
I tried with ext3, but it didn't make any difference..

---

### Post by pro003 on 2009-05-13
check this, might help maybe:

[http://linux.chrissweeney.co.uk/topic.php?t=40](http://linux.chrissweeney.co.uk/topic.php?t=40)

---

### Post by Mr.Kuchinawa on 2009-05-13
Thanks for your effort, but I've already tried exactly that..

---

### Post by Didius Falco on 2009-05-13
> **Mr.Kuchinawa said:**
> Thanks for your effort, but I've already tried exactly that..

Have a look at the first message on this thread:

[http://wiki.ubuntuforums.org/showthread.php?t=1034762](http://wiki.ubuntuforums.org/showthread.php?t=1034762)

I hope this helps,

Regards,

Didius

---

### Post by Mr.Kuchinawa on 2009-05-14
Thanks, but there's no "options" in "/etc/modprobe.d/". All I can see is .conf files with other names than "optons". Sorry if this is something obvious, but I also have to point out that I have to use a live-cd (or usb..), because ubuntu from HDD doesn't work at all.

---

### Post by Didius Falco on 2009-05-14
> **Mr.Kuchinawa said:**
> Thanks, but there's no "options" in "/etc/modprobe.d/". All I can see is .conf files with other names than "optons". Sorry if this is something obvious, but I also have to point out that I have to use a live-cd (or usb..), because ubuntu from HDD doesn't work at all.

Yes, I just did a search on that, and found out that the "options" file was made obsolete... 

[https://bugs.launchpad.net/ubuntu/+source/ubuntu-docs/+bug/368021](https://bugs.launchpad.net/ubuntu/+source/ubuntu-docs/+bug/368021)

I'm searching now for information on where/how to use it otherwise. If I find any leads, I'll post them here.

Understand, I can't guarantee anything - this isn't a problem I've had, so I'm just searching for others that have had it and solved it.

Regards,

Didius

---

### Post by Mr.Kuchinawa on 2009-05-14
Thank you so much!

---

### Post by Didius Falco on 2009-05-14
Hi,

Per this LaunchPad bug report:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/289207](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/289207)

 you can add it as an option at the end of the kernel line in your menu.lst file as ```
libata.noacpi=1
```

Regards,

Didius

---

### Post by Mr.Kuchinawa on 2009-05-14
Where exactly is the menu.lst file?

EDIT: Do you mean in "boot/grub". In that case, what line is the "kernel line" ?
EDIT2: I assume you mean the one with "/bootvmlinz..", but I dont have the privilege to edit it..

---

### Post by Didius Falco on 2009-05-14
> **Mr.Kuchinawa said:**
> Where exactly is the menu.lst file?

EDIT: Do you mean in "boot/grub". In that case, what line is the "kernel line" ?

Yes, it's the menu.lst file in ```
/boot/grub/menu.lst
```You'll need to have root privileges to edit it, so you can do ```
gksudo gedit
```, navigate to the file and open it.

You'll see a bunch of lines at the top of the file, most of which will have a hash (#) in front of them. Scroll down until you see something similar to this:

```
## ## End Default Options ##

title        Ubuntu karmic (development branch), kernel 2.6.30-5-generic
uuid        e47525af-4710-4faa-bc80-fbad1ec6d109
kernel        /boot/vmlinuz-2.6.30-5-generic root=UUID=e47525af-4710-4faa-bc80-fbad1ec6d109 ro quiet splash 
initrd        /boot/initrd.img-2.6.30-5-generic
quiet
```The line you want to edit is the one marked "kernel" at the front:

```
kernel        /boot/vmlinuz-2.6.30-5-generic root=UUID=e47525af-4710-4faa-bc80-fbad1ec6d109 ro quiet splash 
```You'd just add that option to the back end of the kernel line, so it would look like this:

```
kernel        /boot/vmlinuz-2.6.30-5-generic root=UUID=e47525af-4710-4faa-bc80-fbad1ec6d109 ro quiet splash libata.noacpi=1
```Then save and try booting up. Again, I make no promises - it may or may not work. If it should work, you can then go in and add it to all the kernel lines.

If you get a kernel update, it will add a new kernel line at the top of the menu.lst file. Hopefully, it won't cause that problem, but if it does, and this works, you can just go back and add that kernel option to the end of the new kernel lines - there will be two, because of the separate Recovery Mode listing.

Regards,

Didius

I'd strongly urge you to make a bug report as well, so they can work on a permanent solution instead of a workaround.

---

### Post by Mr.Kuchinawa on 2009-05-14
What the..I did just that..and now I can't even boot an external ubuntu (same error message). Not only that, but when booting from HDD it tells that it's an "invalid boot option, ignoring" and then everything proceeds as I have mentioned.. 

This is all messed up..I can't see the light on the usb stick flash as I boot from it.. I'll try with a cd tomorrow (external drive).. Thanks for all the help

---

### Post by Didius Falco on 2009-05-14
If you have problems with it tomorrow, have a look at this community doc about boot options from CD:

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Take note of the F6 options.

Sorry it didn't help...

Regards,

Didius

---

### Post by Mr.Kuchinawa on 2009-05-14
I will. I really appreciate the effort

EDIT: I won't be able to try it for a couple of days.. I will try it, though!

---

### Post by Mr.Kuchinawa on 2009-05-18
No dice. What a load of shite

---

### Post by girimam on 2009-05-21
Hi,
I had a similar problem I used one the solutions given earlier with a difference.

e2fsck supports only ext3 and ext2 file systems. I have used ext4 filesystem. So I directly used the command

*fsck.ext4 [device name]*

and said yes to all and then got fixed. Has to be a filesystem problem. I do not know whether it is a permanent fix or a temporary one. 

Hope it helps..

---

