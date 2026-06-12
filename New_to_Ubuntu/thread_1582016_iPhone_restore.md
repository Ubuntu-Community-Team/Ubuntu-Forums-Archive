---
title: "iPhone restore"
date: 2010-09-25
forum: New to Ubuntu
---

### Post by jepy10 on 2010-09-25
I don't know if people in this forum might be able to help and any help will be greatly appreciated. 
I have compile libimobiledevice in ubuntu and now i was getting ready to use it once i run the command 
idevicerestore -e i get this error message i even went to the libimobiledevice forums but no one there has really answer my question and someone else had post the same error so i was hoping maybe someone here might help. This is the error i get 


root@jonathan-laptop:~# idevicerestore -e '/home/jonathan/Desktop/iPhone1,2_3.1.3_7E18_Restore.ipsw' 
Found device in Recovery mode
Identified device as iPhone1,2
Extracting BuildManifest from IPSW
Product Version: 3.1.3
Product Build: 7E18
Variant: Customer Erase Install (IPSW)
This restore will erase your device data.
Extracting filesystem from IPSW
[==================================================] 100.0%
Resetting recovery mode connection...
Extracting iBEC.n82ap.RELEASE.dfu
Sending iBEC (105844 bytes)...
ERROR: Unable to send iBEC component: Unable to upload data to device
ERROR: Unable to send iBEC to device.
ERROR: Unable to send iBEC
ERROR: Unable to place device into restore mode


I have run this command as a root and as normal, i have also tried putting it in recovery mode before i run the command and still the same issue, I have compile libirecovery correctly although it took a while but i was able to figure it out. 
Like i said any help i will certainly appreciated!

---

### Post by jtarin on 2010-09-25
Why did you compile? It is available in the regular repository.

---

### Post by jepy10 on 2010-09-26
I didn't know but you think I'm doing something wrong it just won't send the ibec!

---

### Post by jtarin on 2010-09-26
> **jepy10 said:**
> I didn't know but you think I'm doing something wrong it just won't send the ibec!
No I'm not saying you did something wrong but to eliminate the possibility of a compiled version causing any difficulty why not uninstall it and use the one from the repository that's compiled already. That's my take on it, but the one you have might be perfectly fine. Not having run this particular application this is the best advice I can give you in a logical chain of events.

---

### Post by jepy10 on 2010-09-26
Maybe this is a very stupid question but which repository the libimobiledevice cause i already have that one? Im sorry man but i really appreciate your help!!

---

### Post by jtarin on 2010-09-26
So what you are saying is that you have 2 installed versions. One you compiled and the other from repo? If you will go to Menu>System>Administration>Synaptic Package Manager then enter "libimobiledevice" in the search box.It will show you all software installed under that name and version. In the left-hand pane you should have "All" higlighted. (usually by default)then you can see all  software installed and not installed under that name and version. It will probably not show your compiled version if you did not compile as a .deb package.

---

### Post by iPhoneNewbie on 2011-01-08
You can see the answer at link: [http://ubuntuforums.org/showthread.php?t=1606378&highlight=restore+iPhone+data](http://ubuntuforums.org/showthread.php?t=1606378&highlight=restore+iPhone+data)
Have funs! :D

---

