---
title: "D-link DWA-4 Install"
date: 2010-04-02
forum: New to Ubuntu
---

### Post by Aster Phoenix on 2010-04-02
Hey doing this for a friend, he's had Ubuntu for about a month and his only wifi is a d-link his installer disk is for windows andhe can't install it. Hes tried using wine to install it but it didn't work. Can anyone help???

---

### Post by anewguy on 2010-04-02
Well, you already found out, but for other beginners reading this, you cannot install things like wireless drivers in wine and expect Linux to see and use your device - they have to be installed to Linux itself.

Now on to more important things:

- with the adapter plugged in:

in a terminal window (applications/accessories/terminal) type:

lspci <press enter>

and 

lsusb <press enter>

Copy and past the output from those back in a reply here.  That will help us identify the chipset being used, to help locate a driver.

Additionally, if you have the Windows driver files (the .inf and .sys files), you can try the following:

- be sure ndiswrapper and it's utilities are installed.  If you can't use a hardwired network connection to use the package manager, they can be installed from the LiveCD used for installation.  Navigate to the /pool/main/n folder and you should see a folder for ndiswrapper.  Click on it to open it and you should see 2 files - 1 for ndiswrapper common or some such thing, and the other for the utilities.  Click on each of these (1 at a time) to install them.

From here, we assume you have ndiswrapper installed.

- copy the .inf and .sys files for your driver to the desktop

- open a terminal window (applications/accessories/terminal)

- type:

sudo ndiswrapper -l <press enter>  Where "l" is a lower case "L", for list.  This asks ndiswrapper to list it's known devices and drivers.

If nothing is returned, go on to the next step.  If a list is returned, you must do sudo ndiswrapper -e xxxx <press enter> where xxxx is the driver file named.  Do this until the list is empty.

cd Desktop

sudo ndiswrapper -i xxxxxx.inf <press enter>  Where xxxxxx.inf is the name of your driver's .inf file.  This instructs ndiswrapper to install the device driver specified.

sudo depmod -a <press enter>

sudo modprobe ndiswrapper <press enter>

sudo gedit /etc/modules <press enter>  This will call up an editor, showing the file containing the kernel modules we want loaded.  Go to the end of the file and add a newline of the following:

ndiswrapper

Save the file, exit the editor.

If your Windows driver is something like B43 or if the output from the lspci or lsusb shows a Broadcom chipset on the wireless adapter line, there is a need to exclude the internal Broadcom drivers from being loaded.  To do that:

- open a terminal window

- type:

sudo gedit /etc/modprobe.d/blacklist.conf <press enter>  This will call up the editor again, this time opening a file telling the system what modules not to load.  Go to the end of the file and add the following lines:

blacklist b43
blacklist ssb
blacklist b43legacy
blacklist b44

Save the file, exit the editor.

You can close the terminal window either by the "X" or by typing "exit" and pressing enter.

Reboot.

Now see if your wireless is showing under network manager.

Dave ;)

---

