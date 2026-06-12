---
title: "[SOLVED] Edubuntu 7.10 wireless network not persistent"
date: 2007-10-24
forum: Networking &amp; Wireless
---

### Post by impalerau on 2007-10-24
Hi,

I've had this in the Absolute Beginner forum all day with no success.  Maybe it belongs here.  I hope I'm not breaking any rules.

I have successfuly installed edubuntu 7.10 on my daughter's machine and connected to my wireless network using the ndiswrapper with the help of the instuctions for 7.04 at [https://help.ubuntu.com/7.04/interne....html#wireless](https://help.ubuntu.com/7.04/interne....html#wireless)

Every time I reboot I lose the wireless conection and have to repreat the "sudo depmod -a" and "sudo modprobe ndiswrapper" commands to enable wireless networking again. Then I have to use the "Connect to Other Wireless Network.." to re-enter the network name and WEP details. At least that is working consistently.

Can the set up be made persistent or is this something I have to live with?

In case it matters, I'm using a Netgear WG311 v3 PCI card.

Thanks in advance,
Vlad.

---

### Post by impalerau on 2007-10-30
Well, it's certainly been an experience.  One minute network working, next minute no device visible and so on...  But after countless false successes and reinstalls including gigabytes of update and package downloads, hours of Googling and forum trawling I finally got there.  Once I had it sorted, I set up 2 desktops and a laptop all on a wireless network in no time at all and without a hitch.

The desktops are PIII 750s fitted with Netgear WG311v3 PCI cards, running edubuntu 7.10.  The laptop is an old Dell Inspiron 5000 (PIII 750 as well) fitted with a WG511v2 CMCIA card, running ubuntu 7.04 (can't install 7.10 or upgrade because of missing ATI support but that's for another thread).

The answer to my specific question re persistence was to add the line "ndiswrapper" to the /etc/modules file which is the list of modules to load at startup.

The breakthrough was finding this site:- [http://www.linuxquestions.org/linux/answers/Networking/NdisWrapper_The_Ultimate_Guide/](http://www.linuxquestions.org/linux/answers/Networking/NdisWrapper_The_Ultimate_Guide/)

Just 4 simple steps (copied) as follows:-http://ubuntuforums.org/showthread.php?t=192281&highlight=keyring+auto+login&page=8

[INDENT]To install the driver using NdisWrapper, follow these instructions:

   1. Open a terminal window (Applications -> Accessories -> Terminal). In the window, type the following to switch to the directory containing the driver files:

      Code:

      cd /home/<username>/Desktop/driver

      Replace <username> with your own username.

   2. To install the driver, type the following:

      Code:

      sudo ndiswrapper &#8211;i filename.inf

      Replace filename.inf with the name of the .inf file you discovered in the previous steps.

   3. Next, type the following:

      Code:

      sudo ndiswrapper &#8211;m 
      gksu gedit /etc/modules

      This will open the modules configuration file for editing. On a new line at the bottom, add the following:

      Code:

      ndiswrapper

      Ensure you press Enter after adding the line.

   4. Save the file, close Gedit, and reboot your computer.
[/INDENT]

After the reboot, the wireless network appears on the drop-down on the network panel icon.  Click on the network you want, fill in the configuration details (WEP key etc.) and it's done.  All drivers were the XP ones straight off the CDs in the box and if anything, seem to be more stable than they were under Windows.

Next little hitch was with with ubuntu 7.04.  Each time I rebooted, I had to enter a Keyring password.  this didn't happen on edubuntu 7.10, it just connected by itself.  The answer was to add the line, "@include common-pamkering" to the end of the /etc/pam.d/gdm file.  I found that in the forum here, [http://ubuntuforums.org/showthread.php?t=192281&highlight=keyring+auto+login&page=8](http://ubuntuforums.org/showthread.php?t=192281&highlight=keyring+auto+login&page=8)

Not really sure what any of that means but it seems to work :)  

3 down, now just 3 more (another laptop, a desktop and a music server) to go and I will be Windows free!  Yipeeee :)

Hope the above helps someone out there and saves them some grief. 

Cheers,
Vlad.

---

### Post by KOld Iron on 2007-10-30
Hello impalerau,

thanks a lot for this detailed description. It really saved my day, because I had the exact same problem (also WG311). I have not testet yet, whether it will re-ask for the keyring password, but I know where to look for the solution, if that needs correction, too :-) (I am using Xubuntu). But I have had the same problem in the past, when I tried Kubuntu, but I did not have it with Ubuntu. So there seem to be some inconsistencies between the derivates.

Anyways, being also a beginner to (X/K)Ubuntu, respectively to Linux, this helped a lot.

best regards
Heinrich

---

