---
title: "Printer Not Found On Server"
date: 2010-07-14
forum: New to Ubuntu
---

### Post by Singlebbl on 2010-07-14
I'm attempting to setup my Ubuntu 10.04 Dell 4600 as a print server for another local WinXP system. 
 
The printer is USB connected to the Dell and works just fine locally. 
 
After reading NetworkPrintingFromWinXP and SettingUpSamba documentation, I installed Samba and was then able to add the printer on the XP system. Print sent to it goes into the print queue but does not get sent to the printer. Status for the printer says "Printer not found on server, unable to connect". 
 
The URL for the printer appears to be correct. I used copy / paste to get it from IE per the instructions in NetworkPrintingFromWinXP. 
 
FWIW, it works AOK with the printer connected to XP. Ubuntu found it w/o a hitch and prints just fine on it so I'm 99% sure the network between them is good. 
 
Any assistance would be appreciated.

---

### Post by cariboo on 2010-07-15
You don't need samba to allow XP to print to a printer connected to your server. open a browser and enter:

[http://localhost:631](http://localhost:631)

in the url bar, or just click the link. Click the Administration link and enable Share printers connected to this system. See the screen shot

---

### Post by Singlebbl on 2010-07-15
[SIZE=3]> **cariboo907 said:**
> Click the Administration link and enable Share printers connected to this system. [/SIZE]
[SIZE=3]Share printers has already been enabled. In fact I have checked every option except "Use Kerberos ...". [/SIZE]
 
[SIZE=3]I saw a note in NetworkPrintingFromWinXP that says both systems need to be using IPv6. Can you tell me how to check / change that? [/SIZE]

---

### Post by Singlebbl on 2010-07-17
This problem is resolved.  

I had to update the workgroup in smb.conf to match the one used by the XP system:  

gksu gedit /etc/samba/smb.conf
Find and change the default "WORKGROUP".  

File sharing works OK from Ubuntu to XP but I have not figured out the "trick" to allow XP to see shared files on Ubuntu.  But that's a story for another day.

---

