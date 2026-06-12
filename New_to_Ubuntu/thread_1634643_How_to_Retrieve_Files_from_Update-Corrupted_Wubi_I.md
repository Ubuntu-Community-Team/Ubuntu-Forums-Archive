---
title: "How to Retrieve Files from Update-Corrupted Wubi Install?"
date: 2010-11-30
forum: New to Ubuntu
---

### Post by RDLP715 on 2010-11-30
Ahoy-hoy!

My Dell laptop's harddisk kind of gave in about 3 months ago due to old age. I decided to experiment in its last days and somehow got a wubi install of 10.04 running. I juggled between that and a pen-drive install. Eventually my pendrive got physically bent out of shape from constant/careless lifting and moving of laptop.

Up until last week I was in the strange scenario of my windows OS being on too corrupt a section of the harddisk to run while somehow my wubi install worked perfectly fine. However I absent-mindedly allowed updates even though I had read that they potentially kill wubi installs. It looks like that has now happened. In the boot-up it gives me a brief 2 line impasse of "error: no command loadfont" or to that effect.

I don't entirely mind if it is irredeemable as I am back on the pendrive, where I wanted to be initially. However there are folders inside it I really want to reclaim if at all possible. I have been on windows all my life and so this coding/terminal approach is completely alien to me. I searched the forum for a solution before considering this new thread but I only found one thread remotely related that it was unfortunately way above my head if it was related..! :oops:

If it is possible could anyone kindly direct me in the simplest of baby language how I could
a) restore my wubi install to its previous working setting
or
b) find and rescue the files on my wubi install desktop

I've learned so much from this forum over the last few months and due to this I am a definite life-long convert to ubuntu, so if anyone could help me further I would be eternally in their debt!

---

### Post by cariboo on 2010-11-30
You shouldn't need to do anything in a terminal, just run nautilus as root. Press alt-F2 and type:

```
gksu nautilus
```

the above command will open the file manager as root, allowing you to do pretty much what you want.

---

### Post by oldfred on 2010-12-01
Welcome to the forums.

I do not know wubi, but bcbc has posted several fixes.

Fix for 10.04 upgrade fail bcbc copy wubildr or edit grub.cfg
[http://ubuntuforums.org/showpost.php?p=9932369&postcount=5](http://ubuntuforums.org/showpost.php?p=9932369&postcount=5)
Fix for grub2 problem with wubi with 9.10
[http://sourceforge.net/apps//bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps//bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)
[https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/477169/comments/210](https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/477169/comments/210)

From another install or your USB drive you can mount the root.disk and read it.

How-to: Recover files from Wubi install with LiveCD
[http://neosmart.net/forums/showthread.php?t=5004](http://neosmart.net/forums/showthread.php?t=5004)

sudo mkdir /win
sudo mount /dev/sdxy /win
sudo mkdir /vdisk
sudo mount -o loop /win/ubuntu/disks/root.disk /vdisk

[Script] Mount Wubi Disk from Linux mount old wubi in new install
mount ntfs partition first:
[http://ubuntuforums.org/showthread.php?t=1037874](http://ubuntuforums.org/showthread.php?t=1037874)

---

### Post by RDLP715 on 2010-12-27
Ah apologies, I forgot to enable notifications after replies!

This looks like exactly what I'm looking for. Thanks a lot for your assistance fellows, I'll give it a try and get back to you. I'm finding learning by doing is the best way to learn about ubuntu.

---

### Post by bcbc on 2010-12-27
Now there is a wubi megathread for help on this: [http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198) Problem #2, Solution #1, Permanent fix

---

