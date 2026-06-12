---
title: "Unable to access system without daily reboot from putty/smb/ping"
date: 2016-09-08
forum: Networking &amp; Wireless
---

### Post by saad_khan2 on 2016-09-08
Guys,

I have been using by system as a plex/file server for quite a while with RAID 1. As of late, i have been having to hard reboot it daily to access it via putty, smb or for the most part anything. It has both a wired and wireless connection. I am wondering if there is some sort of 'sleep feature' that is putting it on standby or something where i can access it. When i go to it, the system is powered on and i see tx/rx lights on my wired connection. i havent upgraded yet..still am on Ubuntu 14.04 LTS

Thanks !

---

### Post by oldfred on 2016-09-09
Never hard reboot. If system is doing anything, you end up with a corrupted filesystem and then need fsck on that partition, or maybe all ext4 partitions.

       Never force shutdown your system. Use Alt+SysRq R-E-I-S-U-B instead. (For newer laptops they don't bother adding the SysRq print to the key, but it's the same as the PrtScr key) 
   Holding down Ctrl+Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[https://en.wikipedia.org/wiki/Magic_SysRq_key](https://en.wikipedia.org/wiki/Magic_SysRq_key)
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)
[http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274](http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274)

---

### Post by saad_khan2 on 2016-09-09
LOL
Thanks for the info ! However this system is headless and just sits in a room alone. i do have a keyboard attached to it when needed....but any idea as to why it just goes MIA ? even when powered on

---

### Post by oldfred on 2016-09-09
There are two modes for not active, suspend & hibernation.

Normally hibernation is not used and it has had issues, so not often recommended. If you turned on hibernation that could be an issue. That writes RAM to hard drive & on reboot recovers image of RAM from hard drive.

Suspend is a lower power default and you can set timing on how long with no activity before it suspends. But that keeps everything in RAM for immediate use. Monitor may turn off, hard drive stop spinning but system is still running.

I do not know how to set either from command line.

---

### Post by saad_khan2 on 2016-09-09
> **oldfred said:**
> There are two modes for not active, suspend & hibernation.

Normally hibernation is not used and it has had issues, so not often recommended. If you turned on hibernation that could be an issue. That writes RAM to hard drive & on reboot recovers image of RAM from hard drive.

Suspend is a lower power default and you can set timing on how long with no activity before it suspends. But that keeps everything in RAM for immediate use. Monitor may turn off, hard drive stop spinning but system is still running.

I do not know how to set either from command line.

I have remote desktop access. If you could shoot me a way to get to it that would be great !

---

### Post by saad_khan2 on 2016-09-09
> **saad_khan2 said:**
> I have remote desktop access. If you could shoot me a way to get to it that would be great !

i checked and suspend is not checked. meaning it shouldnt suspend. i cant find a hibernation option anywhere though

---

### Post by oldfred on 2016-09-09
Then it is not the sleep issue, but something else.
Perhaps conflicts with wired & wireless?

---

### Post by saad_khan2 on 2016-09-10
I dont know. So yesterday i decided to rebuild the system using Ubuntu 16. Everything is all good....and now its doing the same thing again. I have to do a manual reboot to make it come alive again....i am lost.

---

### Post by saad_khan2 on 2016-09-11
Update...i acutally installed gnome tweak utility and got some info out of it...disabled all suspend and dim screen/locks. that may have worked. However i was connected to it via remote and putty, and it out of the blue just cut off. I ordered a new NIC which i will try...cause i feel like the onboard may be burned ?

---

### Post by saad_khan2 on 2016-09-11
So its having issues still...i ordered a NIC so well see if that works...

im trying to upload or paste my log here...not working...

---

### Post by oldfred on 2016-09-11
If log is very long better to use one of the pastebin sites and post link.

If just somewhat long be sure to use code tags.
       How to use Code tags, # in advanced editor
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

---

### Post by saad_khan2 on 2016-09-11
Just to add...the IP keeps on resetting which is most likely the reason why this is happening. I was able to re-connect via putty with the actual IP and not the host name. only other issue is how remote access will drop and how i cant restart services due to systemd

---

### Post by saad_khan2 on 2016-09-13
Just a fyi i dont think its hardware failure...syslog i cant paste because its too big...

---

