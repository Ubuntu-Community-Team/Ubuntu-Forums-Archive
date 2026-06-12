---
title: "Gnome RDP error"
date: 2006-11-02
forum: Networking &amp; Wireless
---

### Post by bschuteker on 2006-11-02
I am using edgy and have had no real problems. I use Gnome RDP every day and can't go without it. Today I was at a client with WPA on their wireless and was trying to get it to work and I downloaded from Synaptic several different wireless programs. Now my Gnome RDP is broken. When I open it it says "Error durring the connection to the database"

Can anyone help?????

Thanks,

Bill

---

### Post by akniss on 2006-11-02
> **bschuteker said:**
> I am using edgy and have had no real problems. I use Gnome RDP every day and can't go without it. Today I was at a client with WPA on their wireless and was trying to get it to work and I downloaded from Synaptic several different wireless programs. Now my Gnome RDP is broken. When I open it it says "Error durring the connection to the database"

Can anyone help?????

Thanks,

Bill

Do you remember which packages you installed?  How about any settings you changed to try and get your connection working?  Any specifics you could provide would certainly help diagnose the issue.

Also, if you start from the terminal ```
rdesktop
``` do you get any more useful information?  Post any error messages you get from the terminal output.

---

### Post by bschuteker on 2006-11-03
Thanks for the reply.

I was reckless and installed anything that said WPA. I know I installed WPA supplicant, Aircrack, Kwifi, Knetwork manager, and possibly others. I have now removed all that I can find because I was never able to get WPA working.

When I run rdesktop from terminal it works normally. I also did a complete removal of Gnome-RDP from synaptic and reinstalled. 

I am still getting the same error.

Thanks

---

### Post by stucky on 2006-11-11
Same sort of issue here. I also ran amok with installing WPA stuff. Seems to be a common denominator. Suppose the easiest place to start would be to try and roll back the installs.:-?

---

### Post by LoRaK on 2007-06-26
Read this:[http://gnome-rdp.linuxforge.hu/?q=node/30](http://gnome-rdp.linuxforge.hu/?q=node/30)

---

### Post by Endolith on 2007-11-19
Try deleting your configuration file .gnome-rdp.db in your home folder.  After an upgrade, it stops working because it's not compatible with the latest version of libsqlite

---

### Post by starbugx on 2008-04-25
Here is a way to read the old .gnome-rdp.db and a workaround to start without errors:

[http://ubuntuforums.org/showthread.php?p=4790024](http://ubuntuforums.org/showthread.php?p=4790024)

---

### Post by hodenkat on 2008-06-16
> **starbugx said:**
> Here is a way to read the old .gnome-rdp.db and a workaround to start without errors:

[http://ubuntuforums.org/showthread.php?p=4790024](http://ubuntuforums.org/showthread.php?p=4790024)

that's a wee bit dirty... I just renamed .gnome-rdp.db and it worked.

---

