---
title: "Slow download fast upload local wired network"
date: 2014-06-13
forum: Networking &amp; Wireless
---

### Post by justin52 on 2014-06-13
Hello,

 I have a newer computer setup with dual boot. It's windows 7 and Ubuntu 14.04. 

 I also have a Synology 1512+ NAS. File transfers in windows 7 seem to work fine.

 Using Ubuntu file uploads to the NAS are around 80-100MB/s, but file downloads are steady at 1.6MB/s

I downloaded and installed the driver from the broadcom website for my Broadcom BCM57781 onboard ethernet. It didn't seem to change anything though.

Any ideas on how to troubleshoot this further?

---

### Post by justin52 on 2014-06-18
I added a new trendet ethernet pci card that is gigabit. Hooked up my ethernet cable, and tried downloading a large file from my diskstation. It downloaded at 1.6 MB.

---

### Post by justin52 on 2014-06-19
OK,

 The disktation had two file services running, one was smb, and the other was Mac file service. On the computer that was working slow I was apparently connecting to the Mac service. I disabled the Mac service in my Diskstation and now it seems to work fine.

---

