---
title: "Error 22"
date: 2009-06-06
forum: New to Ubuntu
---

### Post by devnull123 on 2009-06-06
I recently manipulated my partitions to allow space for windows (surprise surprise) =)

seriously though I am going to reinstall Ubuntu..

my partitions are down to:
```

Partition      File System       Label            Size        Used         
               
/dev/sda1      NTFS              Windows XP       76.01 GIB      66.82 MIB

unalloted      unallotted                          ----          ----         
``` 


after rebooting and putting the Windows XP CD in it gave me error 22


what can i do to resolve it?

---

### Post by 73ckn797 on 2009-06-06
It seems that you are saying that you can boot into Windows but upon inserting the CD you get the error?

Error code explanation :

```
Code 22        The text displayed for this error code differs depending on the circumstances.
   

[LIST]
[*]If this device is disabled because you disabled it using Device Manager,      the following text is displayed:      [INDENT]                            This device is disabled. (Code 22)
         
         Click Enable Device to enable this device.        
      [/INDENT]            Solution button: Enable Device
[*]If the device is not started, the following text is displayed:      [INDENT]                            This device is not started. (Code 22)
         
         Click Start Device to start this device.        
      [/INDENT]            
     Solution button: Start Device
[*]If the device is disabled by a driver or program, the following text is      displayed:      [INDENT]                            This device is disabled. (Code 22)
         
         You can't enable this device because it has been disabled by a Windows          driver.        
      [/INDENT]            Solution button: None
[/LIST]
    This code means that the device is either disabled or has not started.
 
 To resolve this error code, follow the recommended solution. For the third case,  try removing the device in Device Manager, then redetecting it using the Add New  Hardware wizard. If the problem persists, try a clean boot to rule out software  interference. If the error persists, contact the hardware manufacturer.
```[FONT=Arial][SIZE=2]

[http://www.usbman.com/Guides/Error%20Codes%20Explained.htm](http://www.usbman.com/Guides/Error%20Codes%20Explained.htm)
[/SIZE][/FONT]

---

### Post by rickycodie on 2009-06-06
check to see if the device is set wrong in device manager, and the bios.

---

### Post by devnull123 on 2009-06-07
thats the thing i cant boot into XP

---

### Post by rickycodie on 2009-06-07
do you boot into grub or into windows bootloader?

---

