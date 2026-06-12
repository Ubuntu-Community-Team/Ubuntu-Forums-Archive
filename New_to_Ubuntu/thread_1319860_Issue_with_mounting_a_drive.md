---
title: "Issue with mounting a drive"
date: 2009-11-08
forum: New to Ubuntu
---

### Post by AkuX on 2009-11-08
Hello everyone 
My laptop couldn't boot last night, and the tech support people said that I would have to do some OS Recovery thing, thus losing all my files. I wanted to try and recover some of them before trying this method, so I found this guide.

[http://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer/]("http://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer/")

I have been following the steps, but I came across a few issues.
The first being when I tried opening my hard drive, it gave me a different error than the one shown on the guide. Mine said

Unable to mount VistaOS

Error mounting: mount exited with exit code 18: Failed to
open ntfs attribute: No such file or directory
Failed to load $MFT: No such file or directory
Failed to mount '/dev/sda2': No such file or directory.

Then, when I tried using the mount command provided on the guide I got

Failed toopen ntfs attribute: No such file or directory
Failed to load $MFT: No such file or directory
Failed to mount '/dev/sda2': No such file or directory.

I noticed the guide was over a year old, so I was wondering if anything has been updated in the latest release of Ubuntu.

Any help would be appreciated. I just want to get my computer working again :(

Eric

Also, if anyone would like to offer help on why my computer screwed up in the first place, it would be appreciated as well. Feel free to contact me via PM.

---

### Post by varun.nagpaal on 2009-12-23
Hi all,
i am facing exactly the same problem. guys can any xperienced users suggest on this issue?

thanks
varun

---

### Post by lavinog on 2009-12-23
There are many issues that can happen if vista fails that can make mounting a ntfs drive difficult.
Some users might know how to repair a ntfs drive using ubuntu...I am not that experienced in it though.

I do know that you could use the testdisk package to install photorec to recover your files.
Make sure you use an external drive to recover them to.

---

### Post by bodhi.zazen on 2009-12-23
Some suggestions here :

[http://ubuntuforums.org/showthread.php?t=1339017](http://ubuntuforums.org/showthread.php?t=1339017)

I am not overly familiar with ntfs, and IMO the tools in Ubuntu are not great.

It seems your error message is not good =( , most people advise going straight to testdisk / photorec, which can take a long time , depending on the size of your HD.

[DataRecovery - Community Ubuntu Documentation]("https://help.ubuntu.com/community/DataRecovery")

---

