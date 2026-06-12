---
title: "Mount of filesystem failed - fsck cannot fix"
date: 2010-04-28
forum: New to Ubuntu
---

### Post by Raggylad on 2010-04-28
[FONT=Arial][SIZE=3]I am running 9.10 desktop version in a dual boot setup with Windows XP (home edition) on an Asus EeePC 1000 (40GB SSD).[/SIZE][/FONT]
 
[FONT=Arial][SIZE=3]I am a semi-newbie, having only run Ubuntu for about 9 months – my first venture into Linux. I have not used the command line much and then only on a ‘monkey see .. monkey does’ basis.[/SIZE][/FONT]
 
[FONT=Arial][SIZE=3]I am having a problem when trying to get Ubuntu to boot (XP is working fine), which gives me the following error message, whichever of the Ubuntu kernel versions I select from the boot menu:[/SIZE][/FONT]
 
[FONT=Arial][SIZE=3]Mount of filesystem failed.[/SIZE][/FONT]
[FONT=Arial][SIZE=3]A maintenance shell will now be started.[/SIZE][/FONT]
[FONT=Arial][SIZE=3]CONTROL-D will terminate this shell and re-try.[/SIZE][/FONT]
[FONT=Arial][SIZE=3]root@ubuntu:~#[/SIZE][/FONT]
 
[FONT=Arial][SIZE=3]After CONTROL-D I get the following series of messages:[/SIZE][/FONT]
 
[FONT=Arial][SIZE=3]root@ubuntu:~# exit[/SIZE][/FONT]
[FONT=Arial][SIZE=3]mountall start/starting.[/SIZE][/FONT]
[FONT=Arial][SIZE=3]Swapon:/host/ubuntu/disks/swap.disk:swapon failed: Device or resource busy.[/SIZE][/FONT]
[FONT=Arial][SIZE=3]Mountall: problem activating swap:host/ubuntu/disks/swap.disk fsck from util-linux-ng 2.16[/SIZE][/FONT]
[FONT=Arial][SIZE=3]/dev/loop0: Superblock last write time is in the future. (by less than a day, probably due to bad system clock last boot) FIXED[/SIZE][/FONT]
[FONT=Arial][SIZE=3]/dev/loop0 contains a file system with errors, check forced.[/SIZE][/FONT]
[FONT=Arial][SIZE=3]Filesystem checks are in progress (ESC to cancel):[/SIZE][/FONT]
[FONT=Arial][SIZE=3]/dev/loop0: Inodes that were part of a corrupted orphan linked list were found.[/SIZE][/FONT]
[FONT=Arial][SIZE=3]/dev/loop0:UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY. (ie, without –a or –p options)[/SIZE][/FONT]
[FONT=Arial][SIZE=3]Mountall: fsck/[844] terminated with status 4.[/SIZE][/FONT]
[FONT=Arial][SIZE=3]Mountall: Filesystem has errors:/[/SIZE][/FONT]
[FONT=Arial][SIZE=3]Init: mountall main process (839) terminated with status 3.[/SIZE][/FONT]
 
[FONT=Arial][SIZE=3]I then get the original error message again.[/SIZE][/FONT]
 
[FONT=Arial][SIZE=3]I have caused this by my own impatience & incompetence. In trying (without success) to remove an unwanted read-only file icon from the desktop, I eventually tried to unmount it – by right clicking then UNMOUNT. The screen went blank except for the taskbar and the computer would not shut down. Force quit by turning off the power didn’t work either, so I removed the battery – which did.[/SIZE][/FONT]
 
[FONT=Arial][SIZE=3]So I suspect that not only have I managed to unmount the desktop (or something else critical), but I have also fouled up the boot process. The trouble is that I can’t work out how to fix it – short of a complete re-install, which I am reluctant to do as it was 4 days since my last backup and there is a fair amount of work to be lost. Search of the forum hasn’t really helped either.[/SIZE][/FONT]
 
[FONT=Arial][SIZE=3]All help or suggestions very gratefully received.[/SIZE][/FONT]
 
[FONT=Arial][SIZE=3]Many thanks.[/SIZE][/FONT]
 
[FONT=Arial][SIZE=3](I will also be posting this in the ubuntu forum of the EeeUser.com forum)[/SIZE][/FONT]

---

### Post by philinux on 2010-04-28
Reboot.
```
Mount of filesystem failed.
A maintenance shell will now be started.
CONTROL-D will terminate this shell and re-try.
root@ubuntu:~#
```

It should also show which filesystem needs checking like e.g./dev/sda1

At the root prompt to check the correct filesystem use this.

```
fsck -y /dev/sdXX
```

Replace XX to suit. If the file check offers to correct something hit the y key.

---

### Post by Raggylad on 2010-04-28
Phil,
 
Many thanks.  I'll give it a go.
 
A bit puzzled though.  While I couldn't do a screencap of the sequence (I am having to work on another machine), it is a verbatim copy of all that I saw.  There was no filesystem (eg: /dev/sda1) specified anywhere.
 
Is there any way of getting the OS to reveal where the problem filesystem is?
 
Thanks again.
 
Nick

---

### Post by philinux on 2010-04-28
Ok.

Reboot it and when you get to grub choose the recovery mode.

Then try resume normal boot.

---

### Post by Raggylad on 2010-05-02
Phil,

Thanks for the help.  Afraid it didn't work - nor did a couple of ideas from this forum and the EeeUse forum ... ah well !

So I have removed what was left of 9.10 from the machine and reloaded from fresh.  All is working well now.

---

### Post by emmshub on 2010-10-15
fsck -y /dev/sdXX  

worked for me 

Thanks philinux

---

