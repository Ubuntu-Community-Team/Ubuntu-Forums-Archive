---
title: "Lockups"
date: 2009-05-11
forum: New to Ubuntu
---

### Post by choochoo22 on 2009-05-11
After much work and help, 9.04 is finally operable and I want to edit a recorded video and make it into a DVD.  I installed DVDstyler and discovered it makes the DVD but doesn't edit the video but I decided to try it anyway.

On two of two attempts the transcoding process began as I expected and continued in the background as I puttered with the system for a few minutes.  When I walked away to let the job finish, the system locked up.  The first time I'm not sure how long it worked before crashing but it didn't seem to have made much progress from before I left.  The second time I returned about 2 minutes later to find it locked already.  By locked I mean there was no apparent activity and the system was completely unresponsive, the only thing functioning was mouse pointer movement.  Actually, this happened once before DVDstyler was installed but I just wrote it off at the time.  As a Windows user this is not entirely uncommon behavior but I wasn't expecting it in Ubuntu.

Is this a known problem, if so is it fixable or just something to live with like Windows?

Also what is the best course of action in such a situation?  Is there an alternative to just shutting off the power?  Is any lasting harm done?  Should some cleanup be done after reboot?

---

### Post by choochoo22 on 2009-05-12
The problem seems to be worse than I thought.  The system doesn't seem to do anything beyond firefox and file browsing without locking up.  It has crashed 2 or three times now trying to add applications.

---

### Post by 3rdalbum on 2009-05-12
Are you using any proprietary drivers? If so, try disabling them.

You can look at the system logs in System > Administration > Log File Viewer. Look under "kern.log" and it may tell you what has caused the crash.

---

### Post by choochoo22 on 2009-05-12
The contents of those logs mean nothing to me but I noticed that each boot begins with entries like this:

```
May 11 00:56:46 Rix2-Linux kernel: Inspecting /boot/System.map-2.6.28-11-generic
May 11 00:56:46 Rix2-Linux kernel: Cannot find map file.
May 11 00:56:46 Rix2-Linux kernel: Loaded 51712 symbols from 42 modules.
```

And each boot ends with entries like this:

```
May 11 00:56:50 Rix2-Linux kernel: [   20.890941] [drm] writeback test succeeded in 1 usecs
May 11 00:56:56 Rix2-Linux kernel: [   26.724390] eth0: Setting full-duplex based on MII#8 link partner capability of 41e1.
May 11 00:57:02 Rix2-Linux kernel: [   34.688075] eth0: no IPv6 routers present
```

It appears that if the system was re-booted a line like this is present, if the system locked up this line is absent:

```
May 12 10:21:10 Rix2-Linux kernel: [  897.252873] mtrr: no MTRR for d0000000,2000000 found
```

---

### Post by choochoo22 on 2009-05-12
Sorry, I didn't answer your question about drivers.  The only drivers installed automatically, I didn't knowingly download or install any specific drivers.

---

### Post by choochoo22 on 2009-05-13
In trying to get 9.04 to boot, I accidently trashed the Windows XP installation so XP was re-installed at the same time 9.04 was installed on the same system.  Both have been used.  

XP has not crashed once since then.  Ubuntu crashes pretty much every session, it rarely survives to be shut down normally.  Based on reputation, this isn't what I expected when I decided to try Linux.

---

