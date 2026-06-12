---
title: "problem in booting"
date: 2010-01-21
forum: New to Ubuntu
---

### Post by zdubun on 2010-01-21
Hi there,

I have 2 questions:-

Sometimes when I boot ubuntu, on my dell, which is double booted with windows xp as well, the system fails to boot from the hard drive and the screen goes blank after displaying the ubuntu logo. I know this because the hard drive light is off continously.

And I listen to audio files on torrent which have been uploaded as flash. How can I save them ?

Thanks in advance

---

### Post by candtalan on 2010-01-21
> **zdubun said:**
> Sometimes when I boot ubuntu, on my dell, which is double booted with windows xp as well, the system fails to boot from the hard drive and the screen goes blank after displaying the ubuntu logo. I know this because the hard drive light is off continously.
It would be useful to know the exact model of your dell also which version of ubuntu you are using? I trust that you are able to use the updates ok?

> 
And I listen to audio files on torrent which have been uploaded as flash. How can I save them ?

Depending on the facilities in your audio card, then 
applications>sound and video>sound recorder 
works for me, although the volume control (mixer) needs to be configured

hth

---

### Post by zdubun on 2010-01-21
Thaks for the reply. My dell is Latitude D530 core 2 duo. The ubuntu is 9.10 and being a beginner I obediently update the updates. And I shall try the sound recorder. thanks

---

### Post by zdubun on 2010-01-26
Thanks. The sound recorder is working fine. That helped.

Appreciate it.

---

### Post by oldfred on 2010-01-26
Some Dell (and HP) software can write hidden bits into the MBR and corrupt grub2. Also some windows virus software checks the MBR for a windows signature and if not windows assumes it is a virus.

HP ProtectTools and Dell Recovery Tool write into MBR
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941)
[https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/441941?comments=all](https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/441941?comments=all)
Dell Media direct issues with MBR
[http://ubuntuforums.org/showthread.php?t=923576](http://ubuntuforums.org/showthread.php?t=923576)
[http://ubuntuforums.org/showthread.php?t=1344828](http://ubuntuforums.org/showthread.php?t=1344828)
[http://ubuntuforums.org/showthread.php?p=8433673](http://ubuntuforums.org/showthread.php?p=8433673)

---

