---
title: "USB Pen drive permissions"
date: 2010-02-27
forum: New to Ubuntu
---

### Post by colintivy on 2010-02-27
Hi folks.

Just started to play with a new USB 16.1GB pen drive. OS found it OK as sdb1 but it tells me that its "permissions are not known". Tried to chmod but I am not sure that it found the drive. I gather that it will be viewed as a SCSI drive rather than USB and indeed it seems to come up as "disk" in /media instead of "usbdisk" which may be fooling the system. I am administrator but having put myself down as an owner able to write and read files, right-clicking on the drive icon it still says "permissions not known". Must be doing something wrong...books do not seem to help. Can someone elucidate?? My ultimate aim is to backup /home in preparation for 10.04.

colintivy :confused:

---

### Post by HermanAB on 2010-02-27
Most all USB disks are formatted with FAT32 which doesn't support any file permissions.  This can be handled in two ways: Reformat the thing with Ext3, or make a tar ball of whatever you want to backup and save that to the drive, since all the permissions will be preserved by tar.

---

### Post by colintivy on 2010-02-27
Hi HermanAB

Thanks for quick reply. I have already formatted pen to Ext3 in anticipation for BU /home. I have not been able to set the permission to me so far. Once that has been done I then will ba able to try an experimental BU. Any other ideas?

I have tried to look at your howto site but there is no option there to sign on as a new user!!!

colintivy :)

---

