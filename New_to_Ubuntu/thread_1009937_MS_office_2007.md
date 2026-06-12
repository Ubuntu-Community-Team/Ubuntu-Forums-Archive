---
title: "MS office 2007"
date: 2008-12-13
forum: New to Ubuntu
---

### Post by LinnetLegs on 2008-12-13
I am trying to follow this guide to install MS office 2007 [http://ubuntuforums.org/showthread.php?t=922963](http://ubuntuforums.org/showthread.php?t=922963)

I can follow it until it says:

change rpcrt4.dll ng Wine with rpcrt4

Can anyone tell me what that means?

---

### Post by scratman on 2008-12-13
You need to download the file that was attached ad the bottom of that post.  You may need to extract it.  Go to your /home/user/.wine/drive_c/windows/system32 folder.  There should be a file called rpcrt4.dll.  Rename that to Originalrpcrt4.dll.  Then copy the file you just doenloaded and paste it into your system32 folder.  Then go to Applications > Wine > Configure Wine > Libraries and select the rpcrt4.dll, then add.  Should do what you need.

hth

---

### Post by LinnetLegs on 2008-12-13
I am currently trying that - thanks

---

### Post by LinnetLegs on 2008-12-13
can't find /home/user/.wine/drive_c/windows/system32 folder :confused::confused:

---

### Post by WRDN on 2008-12-13
> **LinnetLegs said:**
> can't find /home/user/.wine/drive_c/windows/system32 folder :confused::confused:

If you have WINE installed, you can quickly get to drive_c by clicking Applications > Wine > Browse C:\ Drive, then just go to windows/system32

---

