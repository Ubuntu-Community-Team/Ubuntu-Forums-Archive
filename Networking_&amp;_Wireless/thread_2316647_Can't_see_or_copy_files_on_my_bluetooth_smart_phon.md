---
title: "Can't see or copy files on my bluetooth smart phone"
date: 2016-03-09
forum: Networking &amp; Wireless
---

### Post by richlion2 on 2016-03-09
Hello, 

I am trying to get my Samsung Galaxy GT-S5830 connected. I do get to connect it using the default 0000 pin. I can navigate to my phone folders in Dolphin, but I cannot create any files and cannot see my phone files. I found this older thread, but nothing helps.
[http://ubuntuforums.org/showthread.php?t=1867829](http://ubuntuforums.org/showthread.php?t=1867829)
It looks like a permissions problem, is there any one who can guide me?

Thanks, 
Richard

---

### Post by SeijiSensei on 2016-03-09
Have you tried connecting via USB?  I've not had much luck with Bluetooth.

---

### Post by richlion2 on 2016-03-10
Hi,
no, via USB cable the same thing. No devices appear. I can read the SD card in the SD card, nor a problem here. Does anyone know what this means?
> 
Add in the file */etc/rc.local* between the comments and *exit 0* just the code:  	Code:
 	hciconfig hci0 sspmode 0


---

### Post by jeremy31 on 2016-03-10
If it is an Android phone, it may not have obex enabled

---

### Post by SeijiSensei on 2016-03-10
What version of Ubuntu are you running?  Anything earlier than about 13.10 had problems with USB connections to phones.  

I had a Samsung Galaxy S3 that connected to my 14.04 machine with USB using the MTP protocol.  I now have an LG Stylo and that connects fine as well.

As for 
> Add in the file /etc/rc.local between the comments and exit 0 just the code: Code:
hciconfig hci0 sspmode 0 

that suggests adding a command to the file /etc/rc.local which runs at the end of the boot sequence.  You can edit the file with "sudo nano /etc/rc.local" then adding the line
```
hciconfig hci0 sspmode 0
```
above the "exit 0" line which ends that file.  Before you do that, though, try running the same command from a terminal prompt preceding it with sudo since it needs to be run with root privileges.  (Everything in rc.local is run with root privileges so sudo is not appropriate there.):
```
sudo hciconfig hci0 sspmode 0
```
If that doesn't fix the problem, adding the command to rc.local won't help.

---

### Post by richlion2 on 2016-03-10
Thanks to all of you. I am on Kubuntu 15 will all latest updates. The line in rc.local did not help. 
I'll check this "obex" enable thing, that's one hint.

Regards, 
Richard

---

### Post by richlion2 on 2016-03-10
> **jeremy31 said:**
> If it is an Android phone, it may not have obex enabled

I can't find any instructions on how to enable obex, anyone know a site? I checked the samsung web site, nothing there.

Thanks
Richard

---

### Post by jeremy31 on 2016-03-11
I got ES File Explorer File Manager from the google play app and it finally allowed me to browse files on my Samsung Note 2.  It didn't even work in windows and I haven't tested since I installed that program

---

