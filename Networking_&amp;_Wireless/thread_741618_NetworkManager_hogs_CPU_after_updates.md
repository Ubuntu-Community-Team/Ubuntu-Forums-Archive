---
title: "NetworkManager hogs CPU after updates"
date: 2008-03-31
forum: Networking &amp; Wireless
---

### Post by Leopoguin on 2008-03-31
Hi, I'm running Gutsy dual-boot on an iMac G5.  I just installed a bunch of updates through the update manager, and my fans spun up and didn't stop.  I've heard Linux has had problems controlling the fans on Apple machines, but that's apparently not the problem: it's NetworkManager using like 97% of my CPU, according to top.  I killed NetworkManager and the fans kindly spun down.

So what is this NetworkManager and how do I calm it down?  I'm connected to the net via DSL modem -- I don't need wifi, if that's what NetworkManager does.  As you can see, killing it did not break my internet connection.  

Yes, I read the man page, but there is no command line option for "--stop_blowing_my_friggin_fans"!   And I never turned on any wifi config so I'm not sure why it's even running.

 If no one here knows I'll repost in the PowerPC forum.  Thanks for any ideas!

---

### Post by stream303 on 2008-04-01
> **Leopoguin said:**
> Hi, I'm running Gutsy dual-boot on an iMac G5.

Welcome to the club! 

> I don't need wifi, if that's what NetworkManager does.  As you can see, killing it did not break my internet connection.

On G5 iMacs, the fans should only blow full blast during install.  After a reboot, they should calm down.  (Unlike in Debian PPC where they are controlled during install)

I don't run Network Manager either.  No need for it, so I just disable it - but I don't remove it.  Seems to be a cleaner solution since a lot of stuff seems to depend on NM being around - or so I'm told..  Check out how to disable it here:  (just create two files with "exit" as the text)

[https://help.ubuntu.com/community/WifiDocs/NetworkManager#head-1de145d05f957ff659f5fdb58974ec3e5864def5](https://help.ubuntu.com/community/WifiDocs/NetworkManager#head-1de145d05f957ff659f5fdb58974ec3e5864def5)

> And I never turned on any wifi config so I'm not sure why it's even running.

NM seems to be installed by default no matter what - it is supposed to be transparent, but in your case, and with my G4 iBook, NM was hogging the cpu big time.  Didn't seem to hurt my G5.

Happy to see you here or over in ppc forum either way!

---

