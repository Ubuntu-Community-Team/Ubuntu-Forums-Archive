---
title: "wireless troubles"
date: 2008-11-22
forum: Networking &amp; Wireless
---

### Post by slammed87d21 on 2008-11-22
Well, to start, I have an Acer Aspire 4720Z laptop and I'm honestly unsure of what wireless card it has. I had used the ath5k modules before in 8.04, but since I've upgraded to 8.10 witha disc, my wireless isn't working. I've read it somewhere on here I think  about a backport module that works. Does anyone know which it is? Thanks in advance.

---

### Post by slammed87d21 on 2008-11-22
*bump*

---

### Post by Olivier2371 on 2008-11-22
Don't know if that helps but I read somewhere that you should be using the ath0 modules instead of the one you mentioned.

---

### Post by Joe2Shoe on 2008-11-22
slam, 
If you are using Ubuntu v8.10, you must enable all the repositories to be able to download the needed drivers.
Go to System/Administration/Synaptic Package Manager.
Enter password.
Click Settings/Repositories.
Under the "Ubuntu Software" tab, check the first 4 choices, and your region (United States).
Under the "Third-Party Software" tab, check both choices.
Under the "Updates" tab, under "Ubuntu updates", check the first 2 choices.
Under "Automatic Updates", check "Check for updates: daily".
Close.
File/Quit.
Reboot.
Your pc will check all repositories and download all the required updates for your system.

AFTER doing this, the drivers for my Broadcom BCM4306 rev. 02 wifi card were downloaded/installed, and now works!

---

### Post by Joe2Shoe on 2008-11-22
slam, 
Open up a Terminal and type "sudo lshw -C network" (without the quotes) to find the name of your wifi card.

Joe2Shoe.

---

### Post by slammed87d21 on 2008-11-22
> **Joe2Shoe said:**
> slam, 
Open up a Terminal and type "sudo lshw -C network" (without the quotes) to find the name of your wifi card.

Joe2Shoe.

That does nothing.

---

### Post by Joe2Shoe on 2008-11-22
This fix worked for someone else, as it puts your wifi card's driver in the system under System/Administration/Hardware Drivers.

Using Windows Wireless Drivers

Ubuntu supports a system known as NDISWrapper.  This allows you to use a Windows wireless device driver under Ubuntu.

   1. Obtain the Windows Driver for your wifi card and locate the file that ends with .inf.
   2. Install ndisgtk (System/Administration/Synaptic Package Manager).
   3. Open ndisgtk (System/Administration/Windows Wireless Drivers).
   4. Select Install new driver.
   5. Choose the location of your Windows .inf file and click Install.
   6. Click OK.


[https://help.ubuntu.com/8.10/internet/C/ndiswrapper.html](https://help.ubuntu.com/8.10/internet/C/ndiswrapper.html)
Install NDISwrapper so you can install the Windows driver for your wifi card.

Even though the driver seems to be activated and 'working fine', it isn't.  That was my case, also.

Copy the .inf Window's driver file for your wifi's card to a flash drive or cd, then copy it to your desktop in Ubuntu.
After installing NDISwrapper per the above link, locate the driver file and install it.
Then go to System/Administration/Hardware Drivers, and the driver should be listed, activate it, reboot if necessary (most often is), and check wifi connection.

---

### Post by Ayuthia on 2008-11-22
> **slammed87d21 said:**
> Well, to start, I have an Acer Aspire 4720Z laptop and I'm honestly unsure of what wireless card it has. I had used the ath5k modules before in 8.04, but since I've upgraded to 8.10 witha disc, my wireless isn't working. I've read it somewhere on here I think  about a backport module that works. Does anyone know which it is? Thanks in advance.

I think that you are looking for linux-backport-modules.  Here is a link to a post that mentions how they got theirs to work:
[http://ubuntuforums.org/showpost.php?p=6089169&postcount=3](http://ubuntuforums.org/showpost.php?p=6089169&postcount=3)

---

### Post by Foxcow on 2008-12-25
This worked for me.  It is very simple.

[http://ubuntuforums.org/showthread.php?t=1013378](http://ubuntuforums.org/showthread.php?t=1013378)

---

### Post by slammed87d21 on 2008-12-26
I just went back to 8.04. I seemed to have too many issues with 8.10. Also made my HD start clicking on both my Aspire one and Aspire 4720Z. Stopped on the 4720Z with 8.04.

---

