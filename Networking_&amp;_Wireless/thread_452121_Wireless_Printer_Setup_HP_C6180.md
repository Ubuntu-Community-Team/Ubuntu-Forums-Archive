---
title: "Wireless Printer Setup HP C6180"
date: 2007-05-23
forum: Networking &amp; Wireless
---

### Post by xx75 on 2007-05-23
Hi fellow forum-ers,

Just hoping someone can help me with my problem-

I have a HP C6180 printer/scanner/fax which works perfectly on ubuntu via usb on my desktop. I have recently purchased a laptop and will not be using the desktop anymore. The printer has built-in wireless and I am hoping to setup my ubuntu laptop to connect to it wirelessly, no fancy networking through windows or the like, just a simple straight through connection to my printer.
I don't know where to start and all my searches so far have led to networking through windows or similar.
I have a broadcom 4310 wireless chip, through which I have been able to set up a wireless connection to my adsl modem/router with ndiswrapper.
Where do I start?

Thanks for looking

xx75

---

### Post by benanzo on 2007-05-23
I am not exactly sure if the printer requires any specific config to access it's built-in print server, but my guess is that you just add a new printer and point it to the IP address of the printer.  You can probably just open gnome-cups-manager and opt to Detect Shared Printers.  It will probably show up.

---

### Post by xx75 on 2007-05-23
Thanks for the reply benanzo.

Tried that, but to no avail. No detected printers showing. 

I just had a squiz through my printer's manual and it suggests to network it through an existing network. By the setup results the printer has spat out for me it looks like I have already done that (I have already set up my wifes xp laptop, some time ago now).

So, this means I have the printer on the same network as my modem/router. My guess is that this changes things a bit. But since my ubuntu is already hooked up to the same wireless network, what is stopping me seeing the printer?

Thanks again.

xx75

---

### Post by benanzo on 2007-05-23
I think this printer is going to interface with JetDirect.

I read through [this pdf]("http://h10032.www1.hp.com/ctg/Manual/c00753538.pdf") (which is probably the user manual that you got) and discerned that pretty much all the network configuration is done on the printer itself.  So, first make sure all the wireless network settings are correct on the printer, then try this:

Open gnome-cups-manager
**System** -> **Adminstration** -> **Printers**
and select **New Printer**

Under **Printer Type** select **Network Printer**
This will open a drop-down list.
Select **TCP/Socket/HP JetDirect, Raw connection**

This will show two text boxes called **Host:** and **Port:**
for **Host:** you need to put the IP address of the printer.
Leave the **Port:** as the default **9100**

[I]You can determine the IP of the printer by pressing the **Setup** key on the printer, then select **Network** -> **Network Settings** -> **Display Wireless Summary**
If the printer is currently connected to the network, it's IP address will be listed.
[/I]

Enter the IP address and select **Forward**

Now you need to choose your printer driver.

Under **Manufacturer** choose **HP**
Now for **Model** you will choose **Photosmart C6100**

It will suggest that you use the **hpijs** driver.  This is correct.
Click **Forward** and **Apply**

Now you can go back to the printers box and right-click your new printer and select **Make Default**.

This should set your printer up for networking on Ubuntu's end.  If you have connectivity problems you might double-check the network settings on the printer (ie WEP/WPA etc).

Good Luck!

---

### Post by xx75 on 2007-05-23
It works!

Thanks for your help benanzo,. You really went out of your way for me to locate the manual and study it, I appreciate it.

I can't believe it was that easy.
Wireless and even networking in general is still very new to me and is somewhat scary. I really need to learn more!

I love ubuntu even more now!

---

### Post by benanzo on 2007-05-23
Awesome!

A little note about the network connection on your printer.. If you ever power-off either your printer or your router in the future, there is a good chance that the printer will get a different IP address when your turn it back on.  This will (obviously) cause Ubuntu to not be able to find it when you want to print.  If that happens you will just need to check what new IP it got and set it correctly in the printer settings in Ubuntu.  Just a warning.

Good Luck!

---

### Post by grgzfla on 2007-05-24
Double thanks!  :)

I'm adding a Feisty Fawn system to and existing home wireless network and your instructions worked flawlessly.

---

### Post by randominterrupt on 2007-06-14
Hey.

I've got a photosmart C7150 (or something like that) and I found the best and easiest way to hook it up was with hp's HPLIP software.
It's pre-installed in ubuntu, but I needed python-qt3 to run it.

So from the command line-

> sudo apt-get install python-qt3

and then

> hp-toolbox

(you may have to run hp-toolbox as root with sudo, can't quite remember)

Best thing about doing it this way is you can use the printer, scanner and fax functions with hp-toolbox.
Good luck.

---

### Post by dtvarnum on 2007-11-08
> **benanzo said:**
> I think this printer is going to interface with JetDirect.

I read through [this pdf]("http://h10032.www1.hp.com/ctg/Manual/c00753538.pdf") (which is probably the user manual that you got) and discerned that pretty much all the network configuration is done on the printer itself.  So, first make sure all the wireless network settings are correct on the printer, then try this:

Open gnome-cups-manager
**System** -> **Adminstration** -> **Printers**
and select **New Printer**

Under **Printer Type** select **Network Printer**
This will open a drop-down list.
Select **TCP/Socket/HP JetDirect, Raw connection**

This will show two text boxes called **Host:** and **Port:**
for **Host:** you need to put the IP address of the printer.
Leave the **Port:** as the default **9100**

[I]You can determine the IP of the printer by pressing the **Setup** key on the printer, then select **Network** -> **Network Settings** -> **Display Wireless Summary**
If the printer is currently connected to the network, it's IP address will be listed.
[/I]

Enter the IP address and select **Forward**

Now you need to choose your printer driver.

Under **Manufacturer** choose **HP**
Now for **Model** you will choose **Photosmart C6100**

It will suggest that you use the **hpijs** driver.  This is correct.
Click **Forward** and **Apply**

Now you can go back to the printers box and right-click your new printer and select **Make Default**.

This should set your printer up for networking on Ubuntu's end.  If you have connectivity problems you might double-check the network settings on the printer (ie WEP/WPA etc).

Good Luck!

Benenzo, thank you so much for the post. I purchased my HP Photosmart c6100 series printer yesterday at Circuit City. I have an old DeskJet 720C that's still kickin. However I wanted to print some good 4x6 pix and this machine does a better job than the pixs at CVS. I compared a pix today and it was stunning. The wireless was a bit of a mistery but with your post I was amazed at how cool it is to print wirelessly. I can now get some cable off my office floor. Thanks a million or at least 200.00 (cost of open box printer). dtv

---

