---
title: "fails to mount file system after upgrade to 9.10"
date: 2009-11-17
forum: New to Ubuntu
---

### Post by sharpdrop on 2009-11-17
Hi, I used 9.04 update manager to upgrade to 9.10 on my dual boot Vista Dell Inspiron 1501 and I get a terribly long message about a failure to mount file system and loading some maintenance shell.  It has no Xserver (?) ability so no graphic based apps and no path setting. can use nano to edit but that's about it.

---

### Post by Sealbhach on 2009-11-17
What happens if you try 

```
sudo service gdm start
```.

---

### Post by CoryThompson on 2009-11-17
I have a friend who had this issue, He accidently shut down half way through the upgrade and was running a mix of 9.04 - 9.10.

It can be fixed by typing the following in the CLI:
```
sudo apt-get upgrade

sudo apt-get -f install

```

Although try "startx" before this.

Hope this helps

---

### Post by sharpdrop on 2009-11-20
I hope this helps:
original error message is as follows-
init: spreadahead main process (2859) terminated with status 1
mountall: /proc: unable to mount: Device or resource busy
mountall: /proc/self/mountinfo: No such file or directory
mountall: root filesystem isn't mounted
init:  mountall main process (2860) terminated eith status 1
General error mounting filesystems.
A maintenance shell will now be started.
CONTROL-D will terminate this shell and retry
[my prompt]:~#

When I try Sealbhach's suggestion:

init: gdm main process ended, respawning
init: gdm main process (2899) terminated with status 1
(repeat several times with process number increasing in increments of 3 and then: )
init: gdm respawning too fast, stopped
_

I hope this tells someone something!
thanks

---

### Post by Kjeldgaard on 2009-11-20
I have the same problem as sharpdrop.

When I type
```
service gdm start
```
it returns
```
gdm start/running, process 1582
```

And the "startx" command returns a long error text including Fatal server error: no screens found, and xinit: No such file or directory (errno 2): unable to connect ro X server...

I found another post where anthonywith writes a solution: [http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1308350](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1308350)

But I don't understand how he does it, can someone explain it to me?

Thanks in advance.

---

### Post by john newbuntu on 2009-11-22
Read through this. Good luck.

[https://answers.launchpad.net/ubuntu/+question/87712](https://answers.launchpad.net/ubuntu/+question/87712)

---

### Post by sharpdrop on 2009-11-23
Okay, here's what is happening now.
1st-I read through the launchpad material mentioned above.
2nd- tried to enter through recovery mode oi veih! Got a screen full of gibberish going to fast to comprehend. when it did settle down it just kept repeating the same 4 lines non-stop:
[##.######(these numbers were increasing)] atkbd.c: use 'setkeycodes e00d <keycode>' to make it known.

[##.###### (increasing as well)] atkbd.c: unknown Key pressed (translate set 2, code 0x8d on isa 0060/serio0)

[##.######(these numbers were increasing)] atkbd.c: use 'setkeycodes e00d <keycode>' to make it known.

[##.###### (increasing as well)] atkbd.c: unknown Key released (translate set 2, code 0x8d on isa 0060/serio0)

As near as I could tell, the only way to stop the cascading nightmare is to do a hard reboot (holding the power button down for 5 sec.

then tried the sudo mount -o rw, remount /
sudo update-grub

It didn't change the outcome

I can access the menu.lst file in nano (only non x editor I can find) but filesystem is read only.

How can I get in and edit, and once I do, what should the entry look like for Ubuntu 9.10?

---

### Post by philinux on 2009-11-23
Boot to the mainteance shell. Identify the partition that is failing to mount. e.g /dev/sdax it might be sdb etc.

Then use this command.

```
fsck -v /dev/sd??
```

If it offers to fix things hit the Y key.

Then s the command reboot.

---

### Post by Kjeldgaard on 2009-11-24
> **philinux said:**
> Boot to the mainteance shell. Identify the partition that is failing to mount. e.g /dev/sdax it might be sdb etc.

Then use this command.

```
fsck -v /dev/sd??
```If it offers to fix things hit the Y key.

Then s the command reboot.

First of all I get the same error as sharpdrop in post #4. And when I type
```
sudo fdisk -l
```I get
```
Disk /dev/sda: 320 GB,
255 heads, 64 sectors/track,38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0e8a14fc
    Device Boot   Start      End         Blocks    Id   System
/dev/sda1   *         1    38913      312568641     5   Extended
/dev/sda5             1      486        3903732    82   Linux swap / solaris
/dev/sda6          1703    38913      298897326    83   Linux
/dev/sda7           487     1702        9767488+   83   linux
```If I write fsck -v /dev/sda1 I get an error and "Could this be a zero-length partition?"

If I write fsck -v /dev/sda5 i get
```
fxck: fsck.swap: not found
fsck_ Error 2 while executing fsck.swap for dev/sda5

```When running fsck -v /dev/sda6 I get
```

/dev/sda6 is mounted
WARNING!!! Running e2fsck on a mounted filesystem may cause SEVERE filesystem damage.

Do you really want to continue (y/n)?

```I don't know what happens if I press Y. The same warning appears when I type fsck -v /dev/sda7.

From these informations do you know what the boot problem can be?

---

### Post by philinux on 2009-11-24
Never run fsck on a mounted file system, use the livecd.

Which is the root partition? Thats the one to run fsck on from the livecd or maintenance shell if its unmounted.

---

### Post by philinux on 2009-11-24
[https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/447747](https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/447747)

Se last post for the fix.

---

### Post by sharpdrop on 2009-11-29
Thanks for all your help guys, but, I have decided to go with a fresh reload from a CD.  Granted, this opens up other issues, but I have fought those fights before.

---

