---
title: "Guide on BCM Wireless Chipsets (Hardy Too!)"
date: 2008-04-29
forum: Networking &amp; Wireless
---

### Post by MrObvious on 2008-04-29
Ok this is how I got my wireless to work without a hitch for those who are wondering.

Notes:
Ndiswrapper must be installed first.
This guide is written for those who have a working connection and don't (connect your computer wired for now)

**Prepare Computer**
1) Open a terminal.
2) Do this:
```
gksudo gedit /etc/modprobe.d/blacklist
```
3) Add the following lines anywhere without a # in front (for example the end of the document):
```
blacklist bcm43xx
blacklist b43
```
4) Put a # in front of any lines containing ndiswrapper if there isn't one already or remove that line and save the document and close it.

**Download Firmware - Working Connection**
1) Open a terminal.
2)```
cd ~ && mkdir tmp
cd tmp
wget http://ftp.us.dell.com/network/R151517.EXE && unzip R151517.EXE
```
3) Close the terminal.

**Download Firmware - No Connecction**
1) Download [http://ftp.us.dell.com/network/R151517.EXE](http://ftp.us.dell.com/network/R151517.EXE) and unzip it either on a Windows computer or follow the steps above and unzip the EXE.
2) Copy the whole unzipped contents or the EXE file to the non connected computer and unzip it if not done so already.

**Get Ndiswrapper Working**
1) Assuming you did the working connection step and made a "tmp" folder in your $HOME directory, open the terminal if not already done so.
2) ```
cd ~/tmp/DRIVER
sudo ndiswrapper -i bcmwl5.inf
sudo modprobe ndiswrapper
```
3) Now do a search for wireless signals as before, but this time you should see some activity.
4) To have this work on bootup: ```
gksudo gedit /etc/modules
``` Then add the line ```
ndiswrapper
``` and save and close.

If this doesn't work or I have made an error please let me know by posting or PMing me.

Credits:
[http://*wiki.debian.org/bcm43xx](http://*wiki.debian.org/bcm43xx) for the download link and instructions
Dell for providing the drivers
Ubuntu for an OS worth using.

---

