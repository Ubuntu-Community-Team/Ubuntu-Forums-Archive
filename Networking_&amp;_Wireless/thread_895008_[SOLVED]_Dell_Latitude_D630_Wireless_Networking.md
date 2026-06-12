---
title: "[SOLVED] Dell Latitude D630 Wireless Networking"
date: 2008-08-19
forum: Networking &amp; Wireless
---

### Post by Quicksilver_Johny on 2008-08-19
I've been trying to set up the Wireless card on my Dell D630 with a fresh install of Ubuntu 8.04.

[Apparently]("http://www.linlap.com/wiki/Dell+Latitude+D630") it needs [ipw3945]("http://ipw3945.sourceforge.net/") (which is deprecated) or [iwlwifi]("http://intellinuxwireless.org/?p=iwlwifi").

iwlwifi is supposed to be included in the kernel, but how would I go about setting it up?
Thanks

---

### Post by Quicksilver_Johny on 2008-08-20
Update: I connected via ethernet and installed all the updates not on my CD.
Then, a restricted driver "wl" popped up, and is in use.
Now, the wireless card appears to be recognized as eth1, but I've yet to connect to a network.

---

### Post by rmaultz on 2008-09-21
Here  Is the solution  




Here is the instructions to instal the 1490  and the 1505  agn Dell wireless in kubuntu   this  can be technicial  but this is what i found works  

 

Here is the best write up on using ndis wrapper.

 

IF you need more like the whole extracting it..let me know.

 

3.4. Installing Windows driver 3.4.1. Installing Windows driver using ndisgtk (ndiswrapper graphical interface)
·         If you chose to install ndisgtk, the graphical interface for ndiswrapper, after installation click on System | Administration | Windows wireless drivers and follow the instructions on-screen. For an idea of what to expect, some screenshots of ndisgtk can be found here.

If this works, and you have a network connection, then you can skip to Automatically loading at Startup - ndisgtk will load the driver if it installs correctly.

3.4.2. Installing Windows driver using command line
In a Terminal, run the following command:

·           sudo ndiswrapper -i ~/drivers/drivername.inf
(assuming the driver is in a directory in your home folder called drivers, and is named drivername.inf)

ndiswrapper then copies the .inf and sys files into /etc/ndiswrapper/.... Don't forget that the filename you type in is case-sensitive.

3.4.2.1. Check to make sure the driver was installed correctly
Run the following command from a Terminal:
  ndiswrapper -l
If the driver is installed correctly, you should see the following output:

  Installed ndis drivers:
  {name of driver} driver present, hardware present
or

  {name of driver} : driver installed
       device ({Chipset ID}) present
If you don't see this message:

a.       Try a different driver such as the drivers for Windows 2000, or another driver matching the PCI ID on the ndiswrapper list.

b.      This document has a troubleshooting section which may provide an answer.

c.       Look for additional help. Read HowToGetHelp for more information.

3.5. Load the new driver module
If ndiswrapper correctly associates the driver to the wireless adapter, you are now ready to load the driver into memory, and try to establish a network connection. Open a Terminal and run the following commands:
·           sudo depmod -a
  sudo modprobe ndiswrapper
Then, also in a Terminal, check for error messages:

  tail /var/log/messages
Alternatively, open a Terminal and try the commands ifconfig and iwconfig. Your wireless card should appear with an interface name of wlan0. If it doesn't appear here, then the driver is not working properly. If no errors are given, you should now be able to configure the network connection.

---

