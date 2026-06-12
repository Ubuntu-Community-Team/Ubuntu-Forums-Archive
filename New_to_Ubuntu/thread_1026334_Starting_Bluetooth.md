---
title: "Starting Bluetooth"
date: 2008-12-31
forum: New to Ubuntu
---

### Post by HolySpagetty on 2008-12-31
Hello,

Upon start-up, I get the usual Ubuntu start-up screen. Then at about -92% it freezes and shows the command that it got stuck at, and it happens to be of this format:

```
* Starting bluetooth     tion layer hald
```

I have no idea what is going on and I am not on Ubuntu ATM, as it won't start-up.

Also, upon shut-down, I just press my shut-down button, it can't stop it. It says:

```
* Stopping bluetooth
```

And again freezes.

Please help me, thanks in advance.

---

### Post by HolySpagetty on 2008-12-31
Okay, this might help a little, it started happening after I dual-booted WinXP x64. And after I boot WinXP, this is when the problem comes about.

And I temporarily fixed it by going into recovery mode and doing a file check. That fixed it until I again booted to WinXP and tried booting back to Ubuntu.

If someone could please give me a lasting solution that would be greatly appreciated.

Thanks in advance to anyone that reply's. :)

---

### Post by HolySpagetty on 2008-12-31
Can no one help me?

I thought this would be a pretty common problem.. :(

---

### Post by bumanie on 2008-12-31
I would try the ubuntu alternate installation cd. It is text-based and usually installs when the live cd is presenting with issues such as you describe. Other things you could do first is check your cd for errors and do an [md5 checksum]("https://help.ubuntu.com/community/HowToMD5SUM") on the file you downloaded to ensure it was a 'clean' download.

---

### Post by HolySpagetty on 2008-12-31
I used Linux for a while before this happened, this is not installation.

This just started after I dual-booted to WinXP.

Right after my first WinXP shut-down I came back to go on Ubuntu, and BAM, this crap showed up. :(

---

### Post by unutbu on 2008-12-31
Do you use bluetooth devices? If not, perhaps try removing bluetooth from the bootup and shutdown processes:
```

ls -l /etc/rc*.d/*bluetooth > ~/bluetooth_symlinks
sudo update-rc.d -f bluetooth remove
```
This will remove the symlinks in /etc/rc*.d which affect bluetooth.
(If this does not work and you want to restore the symlinks to their current state, post bluetooth_symlinks and we can supply the right command to recreate the symlinks.)

Also, when you boot Windows, and then Ubuntu and then get the boot problem, what happens if you power down and try booting Ubuntu a second time? 

When do you get the shutdown problem (hanging at Stopping bluetooth...)? Do you get this message every single time you try shutting down? 

By the way, if your machine hangs, it is best not to power off your machine abruptly. Although journaling filesystems like ext3 usually protects you from filesystem corruption, it is still safer to use the following key-combo sequence:


```
Alt-SysRq-R  turns off keyboard raw mode and sets it to XLATE
Alt-SysRq-E  send a SIGTERM to all processes, except for init.
Alt-SysRq-I  send a SIGKILL to all processes, except for init.
Alt-SysRq-S  attempt to sync all mounted filesystems.
Alt-SysRq-U  attempt to remount all mounted filesystems read-only.
```

and then one of the following:
```

Alt-SysRq-B  immediately reboot the system without syncing or unmounting
Alt-SysRq-O  poweroff

```
Wait a few seconds between each key-combination, to give the kernel time to complete each operation.

---

### Post by HolySpagetty on 2008-12-31
Thanks for your reply. :D

But, do you want me to boot from LiveCD to run those commands? Or do you want me to file check it so I can boot it until I boot WIndows again.

And for your questions, I don't use bluetooth, and if I boot Ubuntu a second time, it actually works, until I boot WinXP again.

And I only get the Shutdown hang when I get the boot-up hang.

And I will try to remember those commands, not remember, but write down, at another time, I just want to get Ubuntu working atm..

---

### Post by unutbu on 2008-12-31
> But, do you want me to boot from LiveCD to run those commands?

There is a way to do it from the LiveCD (by chroot'ing), but the update-rc.d command I posted would only work as-is when booted into Ubuntu from your hard drive. 
> 
Or do you want me to file check it so I can boot it until I boot WIndows again.

Yes. fsck if you have to.

But before you try the update-rc.d command, would you please confirm if this is correct?

```
IF                                                        THEN
---------------------------------------------------------------------------------------
Boot Windows, Boot Ubuntu                             --> hangs on boot
Boot Windows, Boot Ubuntu Recovery Mode, fsck, reboot --> successful boot, but hangs on shutdown
Boot Windows, Boot Ubuntu, Shutdown, Boot Ubuntu      --> successful boot, but hangs on shutdown
```

Is there any sequence of actions which allows you to shutdown properly at the moment?

---

### Post by HolySpagetty on 2009-01-01
Sorry I didn't report back, the removing bluetooth from the boot commands thingy worked.

Now there is one problem, my wireless doesn't work.

This was actually a problem BEFORE I removed bluetooth, so that is not the culprit.

But if you could help me there, that would be great. :D

---

### Post by adult swim on 2009-01-01
what is your wireless card?

---

### Post by HolySpagetty on 2009-01-01
It is a USB actually, not a card, if that helps any.

---

### Post by Archibald mathers on 2009-01-11
I am an absolute beginner to Ubuntu, as in i've never gotten it installed because of this exact problem.

running from the live cd this happened, after i went ahead and just tried installing it, the same problem happened. i don't use blutooth, and i'd try turning it off with that peice of code, but i don't know how i'd do that if i can't run ubuntu at all.
again, i'm an absolute beginner...

---

### Post by unutbu on 2009-01-11
Hello Archibald mathers, welcome to the forums.
Let's see if we can make your Ubuntu experience a little more fruitful.

When you boot up your hard drive into Ubuntu, can you get to a command line prompt?
What happens if you press Ctrl-Alt-F2 ? 
Since it sounds like the boot sequence is halting at the "Starting bluetooth" message, you probably can not get to a command line prompt this way, but it can't hurt to try.

[list]
[*]If you can get to a command line, type
```

sudo update-rc.d -f bluetooth remove
sudo reboot

```
You may be asked for a password. Type your regular user password. No text will show on the screen, just type it anyway and press enter.

[*]If you can't get to a command line by booting normally, try booting from the LiveCD.
Get to the desktop environment. (choose the "Try Ubuntu without installing" option).
Go to Applications>Accessories>Terminal to open a terminal.
Type
```

sudo fdisk -l
```

(Note "-l" is minus lowercase L, not minus one.)

This will give you a listing of your partitions. You should see 
some lines similar to these:
```

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63      112454       56196   de  Dell Utility
/dev/sda2          112455    10602899     5245222+   b  W95 FAT32
/dev/sda3   *    10602900    51568649    20482875   83  Linux

```
Each line is a partition. The first column is the "device name". The last column is the "System type". Find the device name whose System type is Linux.

Then type
```

sudo mount /dev/sda3 /mnt
```

(changing /dev/sda3 to the correct device name for your system.) This mounts your Linux filesystem at /mnt. 
```

sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo chroot /mnt
update-rc.d -f bluetooth remove
```

The four commands above will remove bluetooth from your boot sequence.
See if you can reboot successfully now
[/list]

---

### Post by Archibald mathers on 2009-01-14
thanks!
unfortunately the same problem happens with the live cd.
i did however find another solution somone had, which is to unplug all usb devices. that worked, but now all i get is a tan screen after the login window. if i get past that, then i'll go back and use that code to solve the bluetooth problem.
thanks.

---

### Post by unutbu on 2009-01-15
Great! At the login window, try pressing Ctrl-Alt-F2. This will send you to a text terminal.

You'll then be prompted to log in, and then given a command-line prompt. The following should then remove bluetooth from your boot sequence:

```
sudo update-rc.d -f bluetooth remove
sudo reboot
```

---

