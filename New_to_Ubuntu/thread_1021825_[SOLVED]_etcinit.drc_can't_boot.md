---
title: "[SOLVED] /etc/init.d/rc can't boot"
date: 2008-12-26
forum: New to Ubuntu
---

### Post by breakbread on 2008-12-26
Ok, I've screwed up the /etc/init.d/rc by not reading ahead.  I've searched the forums and found similar issues, but the ones that were most similar to mine were resolved by people simply reinstalling.  As fun as reinstalling a fresh OS is, I'd rather not, honestly.

From some of the other threads, people requested outputs of my fstab:

#/etc/fstab: static file system information.
#
# <file system>  <mount point>  <type>  <options>     <dump> 
proc             /proc          proc     defualts      0
#/def/sda5
UUID=13b494c-8559-441f-92ff-36c0c2a4063e /       ext3  relatime,error
# /devsda6
UUED=e98b969a-3cd9-4d59-9e31-09e62d6c6951 none      swap      sw
0     0                  
udf , iso966- user, noauto,exec,utf8 0         0


That's a rough, manually typed output.

But basically, I've tried to manually edit the /etc/init.d/rc but the recovery mode is read-only and I'm on an Eee with no cd-rom.

---

