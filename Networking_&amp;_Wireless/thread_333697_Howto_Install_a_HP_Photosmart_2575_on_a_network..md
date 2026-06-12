---
title: "Howto Install a HP Photosmart 2575 on a network."
date: 2007-01-07
forum: Networking &amp; Wireless
---

### Post by yendor56 on 2007-01-07
Connect and turn on printer, router etc.

Check to see if you have installed the HPLIP (HP Linux Imaging and Printing) package.
System-Administration-Synaptic Package Manager. Enter you password and search for hplip, install it if it is not already installed.

Press the setup button on the printer, then the down arrow button until network is highlighted, then press ok. Press ok, then press ok again. This will print the printers network settings. Note the ip address.

From a terminal do this, substituting your printers ip if different from the 192.168.1.3 of mine.

sudo hp-setup -a 192.168.1.3

Note down the CUPS URI: it will look something like this
      hp:/net/Photosmart_2570_series?ip=102.168.1.3

This may be all you have to do, however if it fails follow these instructions.

Open a web browser and go to [http://localhost:631](http://localhost:631), this is the CUPS administration page. Click on 'Manage Printers' and then 'Add Printer'. On the first screen just type basic information, note that the name must not contain any spaces.

On the second screen for 'Device' select 'AppSocket/HP JetDirect'

On the next screen for 'Device URI' paste in the CUPS URI generated above.

On the next screen just select HP for type of printer.

On the next screen select the printer type, Photosmart 2570 is the one I used.

Click continue button, If you are asked for a username and password, enter your login username and password.

That's all there is to it, also when you do this Xsane will be set up so you can now scan from the device as well.

If you want to see a fancy UI for your printer you can run hp-toolbox from the command line, this shows you the ink levels, print jobs and many other settings.

Add a menu entry for hp-toolbox from Syster-Preferences-Menu Layout if you wish.

---

### Post by 11hjpphty76lkjj on 2007-01-12
Great. Thanks for posting this.

:-D

Aaron

---

