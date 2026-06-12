---
title: "Unable to unlock the Network Admin"
date: 2008-05-09
forum: Networking &amp; Wireless
---

### Post by Onesimus on 2008-05-09
I am trying to examine (and modify) my network settings.  

When I select System->Administration->Network I get the Unlock button grayed out so that I am unable to modify anything (see attached image).  However, when I left-click on the Network icon in the notification applet (located near volume control applet) and select Manual configuration ..., then the button is not grayed out ?!?

Any ideas ?  Has the PolicyKit not been installed correctly ?

---

### Post by grndragon57 on 2008-05-09
I am not near my Ubuntu system so I can't give better directions, on one of the tabs is a box labeled roaming mode or something similar. Uncheck it.

---

### Post by .rdg on 2008-05-09
I did open up the program. I was asked for my password to unlock (which then gets grayed out). After that, when you select any interface you can set the properties. By default it's set to roaming mode, but you can change it.

---

### Post by Onesimus on 2008-05-10
I do get asked for a password, but it is not by the policykit.  The screen goes dim and I get the message:

Enter Your Password to Perform Administrative Tasks

The application 'network-admin' lets you modify essential parts of your system.


I get the image as displayed in first message, and then I cannot modify anything, because everything is grayed out.

---

### Post by koma77 on 2008-05-12
I get an error message when i enter my password. Something like: unknown error when trying to authenticate...

---

### Post by DarkRayne on 2009-01-09
I found this thread via google while trying to figure out my problem. I have the same issue, but an additional problem is that I have no network manager icon in the notification area.
EDIT: users and groups is also greyed out once open.

---

### Post by webdebbyjoss on 2010-01-17
Hi, 
I have the same issue on Karmic with all latest updates. Does anyone managed to resolve this problem?

---

### Post by MarkC502 on 2010-01-17
You could try Wicd to replace network-manager as it is very similar.

Just open synaptic package manager and search for wicd by name and select it for installation, It will prmpt you that it will remove network-manager when it installs. Once it is installed just reboot and you should have a new icon in your notificatin area that is for wicd , open it up and configure your network connections easily and save them.

Just don't remove network-manager and then try to install wicd as you wont be able to once network-manager is gone. Just install wicd and let it uninstall NM as part of that proccess and all will work :-)

Hope that works better for you.

---

### Post by Iowan on 2010-01-17
> **webdebbyjoss said:**
> Hi, 
I have the same issue on Karmic with all latest updates. Does anyone managed to resolve this problem?The same issue being - no Network Manager, greyed users/groups, locked network-admin (network-manager?), or a combination of the three?

---

