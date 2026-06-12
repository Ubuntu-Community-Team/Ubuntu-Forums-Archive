---
title: "input/output error from usb HD"
date: 2008-12-09
forum: New to Ubuntu
---

### Post by Alden born on 2008-12-09
ok i have a usb HD I'm running ubuntu 8.10 on a dell inspiron 1501. when i connect the usb HD every thing mounts fine but when i go to copy files over i get a input/output error. and the drive sometimes remounts.  Yes the files i copy are large.  But also my other computers that i have work with the drive just fine no problems.

thanks for your help i have also attached a pic of what the error is i really need this fixed thanks again.

 [IMG]http://i36.tinypic.com/evdquh.jpg[/IMG]

---

### Post by lykwydchykyn on 2008-12-09
Directly after getting the error, check /var/log/syslog and see if there are any disk-related errors.

Also, I would scan both your USB drive and your laptop's hard drive with "badblocks -v".

---

### Post by Alden born on 2008-12-09
> **lykwydchykyn said:**
> Directly after getting the error, check /var/log/syslog and see if there are any disk-related errors.

Also, I would scan both your USB drive and your laptop's hard drive with "badblocks -v".


OK I’m at college right now I’ll have to do it when I get home.  Also will “badblocks -v" automatically fix errors if there are any?

---

### Post by superprash2003 on 2008-12-09
are you able to acces/browse/open those files from your usb hdd?

---

### Post by Alden born on 2008-12-09
> **superprash2003 said:**
> are you able to acces/browse/open those files from your usb hdd?

Yes i'm able to acces/browse/open.  I just get the error when i try to copy files.  BUt like it said its only that computer.  Not my other ones.

---

### Post by newbee70 on 2008-12-09
> **Alden born said:**
> ok i have a usb HD I'm running ubuntu 8.10 on a dell inspiron 1501. when i connect the usb HD every thing mounts fine but when i go to copy files over i get a input/output error. and the drive sometimes remounts.  Yes the files i copy are large.  But also my other computers that i have work with the drive just fine no problems.

thanks for your help i have also attached a pic of what the error is i really need this fixed thanks again.


Questions

1. ** How big are the files? **

2. ** What is the removable drive formated as? **

---

### Post by lykwydchykyn on 2008-12-09
> **Alden born said:**
> OK I’m at college right now I’ll have to do it when I get home.  Also will “badblocks -v" automatically fix errors if there are any?

badblocks checks for physical problems on the disk; naturally, those aren't fixable by software.

fsck will check for filesystem problems, and with the right switches (I think -c is the one) it will locate bad blocks and work around them.  You can't run fsck on a mounted filesystem (i.e. you system's root partition) so you'd need to run that from the liveCD or similar.

---

### Post by mahiyar on 2008-12-09
If you have doubt about your usb's integrity, simply reformat. Either from windows or linux. Of course after copying all your imp files.

---

### Post by Alden born on 2008-12-09
> **newbee70 said:**
> Questions

1. ** How big are the files? **

2. ** What is the removable drive formated as? **

the files are small but i have tried to copy one at time and all the folders at once it just does it when it feels like it.

the drive is formated as NTFS

---

### Post by Alden born on 2008-12-09
well I check the syslog and I keep getting this error in the log 

> Dec  9 14:42:15 paul-laptop kernel: [  325.532829] atkbd.c: Use 'setkeycodes e00d <keycode>' to make it known.
Dec  9 14:42:15 paul-laptop kernel: [  325.542866] atkbd.c: Unknown key released (translated set 2, code 0x8d on isa0060/serio0).
Dec  9 14:42:15 paul-laptop kernel: [  325.542879] atkbd.c: Use 'setkeycodes e00d <keycode>' to make it known.

it just keeps adding its self in the log.  could that have something to do with it? cause it just keeps filling up the log.  Also after I get the error the file still try to copy and it can happen again during that. Also if more information is needed let me know. 

thanks.

---

### Post by Alden born on 2008-12-09
ok i have some more info when I go to restart or shut-down the computer.  it freezes on this 

> stopping Avahi mDNS/DNS-SD Daemon avahi-daemon

and it only does that after it has a problem with the usb drive.

---

### Post by Alden born on 2008-12-09
ok guys after i had installed ntfs configuration tool from the repos i now am getting these new messages.  But it still lets me access view and open files. just cant copy them.  So her they are.

[IMG]http://i33.tinypic.com/2lw4nqw.jpg[/IMG]

&

[IMG]http://i33.tinypic.com/2psj3b5.jpg[/IMG]

---

### Post by lykwydchykyn on 2008-12-09
Plug the drive into a windows machine and do a disk check on it.  It may just be that the drive got unplugged from a machine without being "safely removed" and the volume is marked dirty.

Linux hasn't got a good "checkdisk" solution for ntfs, as far as I'm aware.

---

### Post by Alden born on 2008-12-09
> **lykwydchykyn said:**
> Plug the drive into a windows machine and do a disk check on it.  It may just be that the drive got unplugged from a machine without being "safely removed" and the volume is marked dirty.

Linux hasn't got a good "checkdisk" solution for ntfs, as far as I'm aware.

ok that will be no problem,  But i copied every thing over to another machine and took it to a windows computer and reformating it as i type this.  I did not do a quick format so it might take a little while and the FS is still going to be NTFS.  After that ill run a Checkdisk on it. 

agian thanks for you help.

---

### Post by Alden born on 2008-12-09
Ok i just reformated the drive and its still NTFS and i ran a checkdisk afterwards and no errors where found.  Ill put some data back on it and see if it works. ill post back in a few.

---

### Post by Alden born on 2008-12-09
OK so that did not work. any ideas?

---

### Post by Alden born on 2008-12-10
i was thinking could it have something to do with RAID?

---

### Post by lykwydchykyn on 2008-12-10
I have no idea how RAID would have anything to do with it.  I would be suspect of your laptop hard drive at this point, or the USB ports on your laptop.  If it's not a hardware issue, I'm not sure what else to suggest at this point, as I've never seen this sort of thing caused by a software issue.

---

### Post by lionstone on 2009-06-30
wow, like everyone else, i've had my fair share of frustrations with linux over the years.

but this one might take the cake.

after the same problem as everyone else here while copying a 20gb file via usb, i tried copying the same file from another hard drive - only to get the same errors.

somehow i didnt believe that BOTH hard drives had bad sectors around the same file.

so instead of "cp" i tried "mv"....

...and worked like a charm.

so do we really have a bug in the core "cp" command????

---

