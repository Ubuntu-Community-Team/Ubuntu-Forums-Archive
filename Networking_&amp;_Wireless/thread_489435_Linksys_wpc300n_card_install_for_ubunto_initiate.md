---
title: "Linksys wpc300n card install for ubunto initiate"
date: 2007-07-01
forum: Networking &amp; Wireless
---

### Post by hiway on 2007-07-01
I have successfully installed Ubuntu on an old Dell C510/610 and want to install a Linksys WPC300N wireless card. 

I have the nidswrapper software on the desktop, as well as the driver .exe file from the internet for this card from the vendor... I really don't know what to do next, nor am I sure if I have completed the install of the sourceforge software. I am sure the drivers aren't installed, and I know the card is not recognized by the OS or machine.

I really want to understand this software, and I am setting this machine up for an autistic adult, with me doing the admin work. Old windows refugee here with simple hack skills and a hardware background... I am patient with this, and I won't be able to check back on the forum for step by step until later tonight. 

From reading the forums here, I see alot of competent help available... hopefully tolerant of an Ubuntu newb who is desperate to shorten his learning curve.:(

Remember, I am not familiar with terminal, but do know how to access it.;)

---

### Post by cipher00 on 2007-07-10
Yeah, I'm in the same boat.  :confused:  I can't even get ndiswrapper to install properly.

I know you will need the .inf and .sys files from your .exe file -- is it maybe a .zip file you can extract?  My card came with the drivers in its own folder on the installation cd (which I've moved to the harddrive).

Good luck.

-Cipher

---

### Post by robinbillings on 2008-07-15
I managed to install the ndiswrapper files using the driver disk distributed with the wpc300n card by doing the following:

1.  Install ndisgtk package.

2.  Click System/Administration/Windows Wireless Drivers menu item (ndisgtk) and selected Install Driver.

3.  Using the distribution CD, pointed it to the /Driver/2KXP/lsbcmnds.inf file.  This installs several files into the /etc/ndiswrapper/lsbcmnds folder.

4.  Go to the /etc/ndiswrapper/lsbcmnds folder and delete all files EXCEPT for the lsbcmnds.inf and the wpc400n.sys file.  Reboot.
5.  Note that there is a major bug in the message handler.  I can connect to an unsecured network, but if the network is secured (WPA Private, etc.), the message handler cannot negotiate the password exchange. If you execute "tail /var/log/messages" you will find lines like this:

Jul 15 09:47:06 rigpa dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.reason

If a password is not required, the connection works just fine.  If the router requires one, I still haven't figured out a solution.  I think I'll just by a prism 2 chipset wireless card, which is supported natively in linux.  

And why does a message handler refer to a redhat folder?  Someone in Ubuntu developer land just cutting and pasting code without reading it?!  

Any other suggestions would be most welcome.

Robin Billings

---

