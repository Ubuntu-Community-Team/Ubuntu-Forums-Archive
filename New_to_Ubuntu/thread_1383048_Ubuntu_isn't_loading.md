---
title: "Ubuntu isn't loading"
date: 2010-01-16
forum: New to Ubuntu
---

### Post by S Man on 2010-01-16
I installed Ubuntu a couple days ago and while it was somewhat awkward at first, I was satisfied with how smoothly it ran. Then I get a popup of applications that need installed/updated. It was about 117 MB and I click to download all. Everything ran smoothly and at the end I get the notice that my web browser had been updated and I need to restart. So I clicked restart but every time I try to get Ubuntu loaded I get black background with gray text and it never progresses further.

Anyway I'm running Windows in the meantime. I've tried Ubuntu safe mode as well but it didn't work. I never get to the log in screen. Any ideas on what to do?

---

### Post by MarkC502 on 2010-01-16
Try pressing escape when the PC is first starting to see if you can see your Grub boot menu. If so you should see a list of options including several Kernels to boot to. Just choose an older kernel version number as it would be the one the was working and see if that will get you booted into linux.

Is there any chance that the disk partition you have installed Ubuntu on ran out of disk space during the 117MB update ? ( I have seen this happen once and it had similar results ) , otherwise it most likely means that something failed during the update and it is trying to boot to the broken kernel from the update ( in which case my advice above should work )

You might add what version of Ubuntu you are running as well.

---

### Post by Pikestaff on 2010-01-16
Maybe X (your gui) isn't starting up... is it asking you to log in (name and password), just with text instead of a graphical interface?

---

