---
title: "HP P1505n System Printer"
date: 2008-06-16
forum: Networking &amp; Wireless
---

### Post by tjh on 2008-06-16
:(I need assistance is getting my HP P1505n system printer working with Ubuntu.  HP indicates the printer can't be accessed by any of the Linux distros unless it is connected locally to a workstation.  The printer is connected via an Ethernet cable directly to my router and I don't want to have to make the printer shared by connecting it to a workstation.  The installation CD provided by HP include setup files for Mac's and Windows workstations but nothing for Linux.  Can anyone offer any suggestions?

---

### Post by prshah on 2008-06-16
> **tjh said:**
> The installation CD provided by HP include setup files for Mac's and Windows workstations but nothing for Linux.  Can anyone offer any suggestions?

Find the PPD file in the Mac drivers. Then open firefox, and in the location bar, give the address```
http://127.0.0.1:631
``` This opens the CUPS admin page. Add a printer, and when prompted, point it to your PPD file. [(See screenshot).]("http://ubuntuforums.org/attachment.php?attachmentid=74211&d=1213606715")

---

### Post by inyoka on 2008-09-07
Can anyone confirm if this actually works?  I am thinking of buying this printer tomorrow and these posts are the closest I have found to an answer so far. 

Any help much appreciated.

---

### Post by inyoka on 2008-09-16
> **prshah said:**
> Find the PPD file in the Mac drivers. Then open firefox, and in the location bar, give the address```
http://127.0.0.1:631
``` This opens the CUPS admin page. Add a printer, and when prompted, point it to your PPD file. [(See screenshot).]("http://ubuntuforums.org/attachment.php?attachmentid=74211&d=1213606715")

On my CD there were no .PPD files, I am in Indonesia so it may be a region specific problem.  However here is the fix for this or just about any other networked HP printer:

1) Use synaptic to download and install hplip (HP Linux Printing and Imaging System).

2) Once installed press Alt-F2 and type in "gksu hp-setup", you can of course run this from the command-line if you prefer.

3) You'll have to enter your admin password, and a GUI install program will come up, follow the on screen instructions.  

**NOTE:** *It didn't automatically detect the IP address of my printer (which was administered by my routers DHCP server).  On the P1505n press the "GO" button (the green page feed button), this will print a test page with the printers IP address under the section 'Network Information'.  Another problem I encountered is that Ubuntu automatically generated a printer name "HP_LaserJet_P1505n", however the program will NOT ACCEPT UNDERSCORES in the name, and you will not be able to click next until you remove them. (I called my printer 'HPP1505n' and this worked fine).*

I hope this helps somebody else, HP continues to be a very good choice from my experience of printers on Linux.

---

### Post by MartijnBuijs on 2008-10-20
Thanks for your reply, it helped me get this printer working on my Ubuntu box.

I should point out that for the GUI to work you need to check the "hplip-gui" package, this may not be installed by default.

So in a nutshell (for the newbies):

1) run synaptic package manager

2) search for "hplip"

3) check "hplip", "hplip-data" and "hplip-gui"

4) click "apply" and wait for it to complete

5) press ALT-F2, enter "gksu hp-setup" and press enter

6) the GUI will now popup to guide you through installation


Heck of a lot easier than installing on Windows! :)

---

### Post by inyoka on 2008-10-20
MartijnBuijs, thanks for your reply, however you do not need "hplip-gui" to run the "hp-setup" (with GUI), and "hplip-data" is a dependency of hplip so will be installed automatically if you install "hplip".

"hplip-gui" includes the GUI for "hp-toolbox" which is an HP Device Manager.  hp-setup is just a wizard for installing the printer.  However, hp-toolbox is certainly a useful tool to administer your HP printers, but ironically if you add a printer using "hp-toolbox", the GUI just runs "hp-setup -u".

....but if you are a newbie, and would prefer to manage your HP printers using HP's software, just... 

1) Install "hplip-gui" with synaptic and all the other packages are installed automatically.  

2) Then go to "System > Preferences > HPLIP Toolbox"

3) Then go to click "Device > Setup New Device" to run the wizard.

4) Then enter your admin password and follow the gui.

Anyway thanks for the post MartijnBuijs, installing hplip-gui does allow you to check the status of your ink cartridge, although I would suggest using "System > Administration > Printing" for managing the printer once its installed just to avoid the confusion of having different admin panels for different printers.

---

### Post by vgrisham on 2008-11-03
I installed the hplip software and the printer as directed, but I can't get it to print. I try to send a test page and the green light on the printer blinks for several minutes. It then prints a page that says "Unable to open the initial device, quitting." 

Any ideas?

---

### Post by vgrisham on 2008-11-04
I deleted the printer and started over. Still no dice. 

Here is the driver that hplip is choosing:
PPD File
drv:///hpijs.drv/hp-laserjet_p1505n-hpijs-pcl3.ppd
Description: HP LaserJet p1505n Foomatic/hpijs

I'd appreciate any help you may have as to how you got this printer to work with Ubuntu.

---

### Post by vgrisham on 2008-11-04
I got it working by downloading the foo2xqx driver and by following these instructions. After downloading and installing the driver, I fired up gnome cups and selected the p1505 driver instead of the p1505n driver.

---

