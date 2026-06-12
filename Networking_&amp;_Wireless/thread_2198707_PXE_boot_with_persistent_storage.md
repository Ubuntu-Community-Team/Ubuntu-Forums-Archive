---
title: "PXE boot with persistent storage"
date: 2014-01-10
forum: Networking &amp; Wireless
---

### Post by jcdenton21 on 2014-01-10
Hello everybody
I am booting Ubuntu 12.04.3 x64 via PXE and it boots just fine
instead of modifying squashfs I would like to have a small (~1GB) persistent partition of overlayfs just like liveCD on USB with persistent partition (casper-rw)
I spent a few days searching the internet but did not find any clear enough tutorial
this thread ([http://ubuntuforums.org/showthread.php?t=1421981](http://ubuntuforums.org/showthread.php?t=1421981)) is about what I am asking but I could not replicate the success

I created a file in the /casper directory of extracted LiveCD and gave it write permissions
```
sudo dd if=/dev/zero of=casper-rw bs=1024 count=1572864
sudo mkfs -t ext2 casper-rw
sudo chmod 666 casper-rw
pi@raspberrypi:~/www/tftp/pxelinux.cfg/ubuntu/12.04.3/casper$ ls -la
total 746300
dr-xr-xr-x  2 root root       4096 Jan 10 10:44 .
drwxr-xr-x 12 pi   pi         4096 Jan 10 10:32 ..
-rw-rw-rw-  1 root root 1610612736 Jan 10 10:44 casper-rw
-r--r--r--  1 root root      43202 Aug 20 20:04 filesystem.manifest
-r--r--r--  1 root root        872 Aug 20 20:04 filesystem.manifest-remove
-r--r--r--  1 root root         11 Aug 20 20:04 filesystem.size
-r--r--r--  1 root root  698949632 Aug 20 20:04 filesystem.squashfs
-r--r--r--  1 root root   17088807 Jan  8 11:28 initrd.lz
-r--r--r--  1 root root   16873273 Aug 20 20:04 initrd_old.lz
-r--r--r--  1 root root    5428352 Aug 20 20:04 vmlinuz.efi
pi@raspberrypi:~/www/tftp/pxelinux.cfg/ubuntu/12.04.3/casper$
```

and added "**persistent **" keyword into my APPEND line for PXE entry

but it does not seem to work
once I reboot from PXE I am back with the default live environment and no changes are there that I made

could anybody please help me?
or just point me to a tutorial that I missed 

I would love to have the same capabilities with PXE boot as live CD on USB with persistence gives me

Thank you very much in advance


//edit:
once I boot the Ubuntu through PXE the filesystem mounts look like this ( click to enlarge the attachment [IMG]http://ubuntuforums.org/attachment.php?attachmentid=249349&d=1389347897&thumb=1&stc=1[/IMG] )

//edit:
same question was asked here ([http://discuss.howtogeek.com/t/how-to-pxe-boot-an-ubuntu-image-from-windows-server-2008/2727](http://discuss.howtogeek.com/t/how-to-pxe-boot-an-ubuntu-image-from-windows-server-2008/2727)) but I did not find any conclusive answer there either

---

### Post by jcdenton21 on 2014-01-15
I would like to know if this is even possible or not so I am not chasing ghosts trying to solve it.

thank you very much in advance for any answer.

---

