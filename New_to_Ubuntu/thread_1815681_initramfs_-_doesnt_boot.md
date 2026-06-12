---
title: "initramfs? - doesnt boot?"
date: 2011-07-31
forum: New to Ubuntu
---

### Post by 007casper on 2011-07-31
my friend's computer defualts to initramfs? ???

You cant cd to anything nor update.  I wonder if something went wrong during update.  Please advise. What she wrote to me is down below.

> 
Dear Unbuntu:

I don't know what happened. My computer just up and died on me this morning.

I restarted my computer after the text editor failed to launch properly. The window would open but no text anything. So I tried to restart the computer normally, via the "restart" pull down option. But that wouldn't launch either.

So I went straight to the heart; I pushed the physical start button. It quit like it was supposed to. Then I paused for a moment of silence and again pressed down on the physical start button.

But nothing normal happened after that. :( The just went black (no tribal unbuntu greeting) and started spitting out white text gobbledgook. 

What now?

P.S. I DID download the latest ubuntu update.


---

### Post by 007casper on 2011-07-31
When you tried to boot the computer, it prompts to initramfs.

initramfs ls -al
```

drwxr-xr-x 14 0   0 3280 dev
drwxr-----  2 0   0    0 root
drwxr-xr-x  5 0   0    0 lib
-rwxr-xr-x  1 0   0 5145 init 
drwxr-xr-x  3 0   0    0 conf
drwxr-xr-x  2 0   0    0 sbin
drwxr-xr-x  8 0   0    0 scripts
drwxr-xr-x  2 0   0    0 bin
drwxr-xr-x  6 0   0    0 etc
drwxr-xr-x 12 0   0    0 sys
drwxr-xr-x 85 0   0    0 proc
drwxr-xr-x  2 0   0    0 tmp
drwxr-xr-x  3 0   0    0 var
drwxr-xr-x 14 0   0    0 ..
drwxr-xr-x 14 0   0    0 .

```

it seems as some of the folders are missing

so I tried apt-get upgrade
apt-get update; got
```

/bin/sh: apt-get: not found

```

???

---

### Post by Gone fishing on 2011-07-31
I think this usually happens when the system cannot mount the root partition. I assume this is a normal non Wubi install? and you haven't changed any partitions? If it is a Wubi install it might be as easy to fix as running Windows chkdsk.

If this is normal install I wonder as this was after an update whether it will boot from an old kernel?

---

### Post by 007casper on 2011-07-31
havent changed partitions.  No wubi install.  Straight ubuntu.

I get a section of the message.
> 
[  1.794994] [<c02243b3>] ? do_mount+0x1c3/0x200
[  1.795041] [<c022445b>] ? sys_mount+0x6b/0xa0
[  1.795088] [<c01033ec>] ? syscall_call+0x7/0xb
[  1.795135] [<c0590000>] ? register_kretprobe=0x1a0/0x1b0
[  1.795181] Code: 00 55 89 e5 57 89 c7 56 53 e8 f3 ee 22 00 8b 5f 04 b8 ff ff ff ff 8b 77 08 eb 1c 8d b6 00 00 00 00 8b 0c 85 00 1e 7a c0 8b 57 14 <8b> 14 0a 89 d1 c1 f9 1f 01 d3 11 ce 8d 48 01 a1 2c a0 59 c0 ba
[  1.796477] CR2: 00000000023bd000
[  1.797293] ---[end trace 00db598d581b1865 ]---
Killed
mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesnt have /sbin/init.
No init found. Try passing init= bootarg.

BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) [ 2.3006665] ieee1394: Host added: ID:BUS[0-00:1023] GUID[384fc000111bf9c1]


---

### Post by 007casper on 2011-07-31
how do I boot from the old kernel?

---

### Post by Gone fishing on 2011-08-01
When you start up click esc and will see the grub menu and in previous versions of Ubuntu the kernels are listed from newest to oldest. In 11.04 there is an option previous versions of linux click that and the kernels will be listed.

If that doesn't work I'd boot from a live CD check the the root partition can be mounted and if everything is there and then if there is a problem run fsck.

---

### Post by 007casper on 2011-08-01
it is 10.4.  I tried 'esc' it just beeps, when I let go, it goes to initramfs on the command line.

???

---

### Post by 007casper on 2011-08-01
bump

---

### Post by Gone fishing on 2011-08-02
Sorry - have to work - shame :( 

Esc should get you into grub if it is pressed just as at the very beginning of the Ubuntu boot process.

However, I think it is unlikely that this will work, worth a try but.... 

Boot from a live disk and see it the file system can be mounted - I think there will be a problem - lets take it from there probably you will need to fsck.

The quickest solution maybe to backup home (is it's  own partition?) and reinstall this will take maybe half an hour? Fixing will be more interesting and offer the opportunity to learn more but may take some time.

---

### Post by 007casper on 2011-08-03
just reloaded ubuntu with live usb stick, and then updated.  All is good now.

I dont know what happened.  I figure the previous update ruined the old set up.

---

### Post by Gone fishing on 2011-08-03
Very pleased for you - I thought if you were lucky it would be a problem with kernel update - I don't know why you couldn't get the grub screen and boot from an old kernel have a look this should be easy.

Pleased it wasn't a corrupt file system, I had this horrible feeling you were going to find your whole file system in lost and found.

Once again very pleased for you.

---

