---
title: "Mounting Network Attached USB Storage Device (WD &amp; Netgear)"
date: 2011-07-02
forum: New to Ubuntu
---

### Post by oconnor on 2011-07-02
I'm wondering how I can see the network attached storage hard drive I just connected.  I'd like to have a folder in Places -> Network called NAS if possible.

My equipment:
OS: Ubuntu 11.04
Router: Netgear N600 
Storage: Western Digital My Book Essential 2TB USB 2.0 + 3.0

So far I've looked for the device by logging into the router 
[http://www.routerlogin.net/start.htm](http://www.routerlogin.net/start.htm)
and looking at the Advanced Settings under USB device.  I can see it has an IP address of 192.168.1.1

I can see the files on the hard drive and I've opened the user manual which provides only Windows and Mac support.  There is no mention of Linux. 

I've looked in Places -> Network but there is nothing there other than an empty "Windows Network" folder.  

Thanks.

---

### Post by sandyd on 2011-07-02
> **oconnor said:**
> I'm wondering how I can see the network attached storage hard drive I just connected.  I'd like to have a folder in Places -> Network called NAS if possible.

My equipment:
OS: Ubuntu 11.04
Router: Netgear N600 
Storage: Western Digital My Book Essential 2TB USB 2.0 + 3.0

So far I've looked for the device by logging into the router 
[http://www.routerlogin.net/start.htm](http://www.routerlogin.net/start.htm)
and looking at the Advanced Settings under USB device.  I can see it has an IP address of 192.168.1.1

I can see the files on the hard drive and I've opened the user manual which provides only Windows and Mac support.  There is no mention of Linux. 

I've looked in Places -> Network but there is nothing there other than an empty "Windows Network" folder.  

Thanks.


Nautilus=smb://192.168.1.1
or Places>Network>Windows Network>Workgroup>Readyshare
Firefox= [ftp://192.168.1.1](ftp://192.168.1.1)
[ftp://192.168.1.1/shares](ftp://192.168.1.1/shares)
[http://192.168.1.1/shares](http://192.168.1.1/shares)

---

### Post by oconnor on 2011-07-02
Thanks.  But I don't understand.  And I tried Places -> Network -> Windows Network but there's no folders in there.  I tried making one but I got this error:

"There was an error creating untitled directory folder. There was an error in creating the directory in smb:///"  And when I click on "more details" it says "operation not supported by backend"

What do you mean by 
Nautilus=smb://192.168.1.1  ?

I get what Nautilus is for browsing directories but I can't name a new file "smb://192.168.1.1"  And I don't see where I can put this when I right click on a new folder.  Where does it go exactly?

Thanks again.

---

### Post by oconnor on 2011-07-03
I'm still having problems with this.  I'm now trying to use Nautilus by going to File -> Connect to Server

I'm trying Public FTP.
Here are the fields I fill out:

For trying Public FTP
Server: readyshare.routerlogin.net  
Port: 21
Folder: shares

Message:
Could not display "ftp://anonymous@readyshare.routerlogin.net/shares". Error: The file is not a directory
Please select another viewer and try again. 

I really don't understand what the problem could be - any help would be greatly appreciated.  I've also typed in the IP address and made sure it works in Firefox.  This works for taking me to the network share using Firefox:
[ftp://readyshare.routerlogin.net/shares/USB_Storage/](ftp://readyshare.routerlogin.net/shares/USB_Storage/)
but I really want a folder so I can have a backup by just dragging and dropping the things I want to back up.

---

