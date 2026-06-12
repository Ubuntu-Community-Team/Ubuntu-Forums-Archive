---
title: "Another File Sharing Thread"
date: 2008-09-21
forum: Networking &amp; Wireless
---

### Post by greyblitz on 2008-09-21
So, firstly, the background of my dilemma. I am running a laptop and desktop connected through a Linksys router. The laptop runs WinXP and the desktop is running Kubuntu. It used to run Ubuntu until I messed it up and formatted. In Ubuntu the sharing was working just fine, but now Kubuntu is giving me troubles. 

The WinXP laptop shared folders have been doing just fine and have been working the entire time. I would now like to place a shared folder on the Kubuntu desktop PC.  I created a folder and shared it. When I look back at the WinXP laptop network places, I can see the desktop computer but cannot access it. It keeps asking for me to log into the desktop machine and regardless of what I enter, it still pops up repeatedly. However the sharing works great in the opposite direction, Kubuntu can access WinXP shared folders without even a hiccup.

In my newbie opinion, it has nothing to do with WinXP because I didn't change anything on it, and it worked just fine in Ubuntu. Does anyone have a lead to what the problem might be?

Any help is very much appreciated.

---

### Post by greyblitz on 2008-09-24
Bump...anyone, please?

---

### Post by Iowan on 2008-09-24
I presume you installed Samba-server on the Desktop (Samba-client comes pre-installed).  Some threads suggest you must install smbfs, too.

---

### Post by greyblitz on 2008-09-25
I'm not sure if samba-server is installed. I will check into both the server side and smbfs.

---

### Post by Iowan on 2008-09-25
Try **ps ax |grep mbd**. smbd and nmbd should show up.The **smbfs** package actually installs CIFS - the replacement for SMBFS. CIFS Mounting How-to link is in my sig.

---

