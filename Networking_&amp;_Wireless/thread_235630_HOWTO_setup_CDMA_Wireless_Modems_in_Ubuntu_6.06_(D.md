---
title: "HOWTO setup CDMA Wireless Modems in Ubuntu 6.06 (Dapper)"
date: 2006-08-13
forum: Networking &amp; Wireless
---

### Post by docplastic on 2006-08-13
This has been tested using a "Zapp Telemodem Z020" also known as "AnyDATA ADU-E100D" modem


1. You will **need a Linux kernel 2.6.15-26 or newer**

[INDENT][LIST]
[*]Check if you have a valid kernel by starting "Synaptic" (System->Administration->Synaptic) and doing a search for: linux-image-2.6.15-
[*]Check if you have installed and are using a "linux-image-2.6.15-26" or newer/higher.
[*]If you do not have it, install one, reboot your computer and choose the new kernel from the boot menu.
[*]There are ways to make these modems work with older kernel images but, I have been there, it is just a waste of time and in the end you do not get the advantages of the better driver included from 2.6.15-26 (and which, BTW, was taken from a 3G PCMCIA card, not from pure CDMA hardware).
[/LIST]
[/INDENT]
2. Use **ppconfig** to set up your connection:

Open a terminal window and execute: ***sudo pppconfig***
Choose "Create a connection"
[INDENT]Provider *my_isp_name* (any name will do, perhaps the name of your ISP provider?)
 Dynamic (ISP usually use a dynamic DNS system)
 PAP (you may choose other, but if your ISP bundles the modem with software for windows chances are that they will expect some kind of windows/PAP protocol. So make them happy and give them PAP)
 your login name
 your password
 modem port speed: 460800
 method of dialing: tone (it doesn't matter)
 number to dial: #777 (CDMA providers in many countries use this number)
 Choose 'no' when it asks if you want the modem port automatically identified
 Choose "Manually Select Modem Port" and enter: /dev/ttyUSB0
 In "Properties of provider" check the configuration and correct any errors.

Use the cursor keys to go down and choose "**Advanced Options**"
 "Modeminit" should be **ATZ**
 In "ISP	Connect" should stay clean (i.e., without any codes in it)
 "Defaultroute" should be **defaultroute** (use the defaultroute set up by your ISP)
 "Persist" should be **on** (it will make the modem reconnect if it losts connection)
 "Ipdefault" should be **noipdefault** (your ISP will provide one)
 "Debug" should be **disabled** (otherwise if you are a "techie")
 "Demand" should be **disabled**
 "Persist" should be **enabled** (to make the modem automatically reconnect in case that it losts connection)
 "Nameservers" should be **dynamic** (most ISPs like to assign their own numbers)
 Select "Add-User" and enter your usual login user name
 "Remotename", usually you will not need to change this one
 "Idle-timeout", idle time in seconds after which your modem will auto-disconnect.

 Select "Return to previous menu"
 Select "Finished Write files and return to main menu."
 Select "<Ok>"
 Select "Quit Exit this utility"[/INDENT]

In your file system you should now have 2 new entries using the name you gave in 2.2.1:
**/etc/ppp/peers/*my_isp_name*** and the other in **/etc/chatscripts/*my_isp_name***
You may also have a new entry in your existent **/etc/ppp/pap-secrets** file

3. Start modem connection from a terminal window with the following command:
[INDENT]***pppd replacedefaultroute nodetach call my_isp_name***[/INDENT]
 
 [LIST]
[*]The *replacedefaultroute* is used to replace the default system route which may be already setup to some other device.
[*] The *nodetach* lets me see what the modem is doing. It helps to keep an eye if it getting its IPs, if it was disconnected and when I am done I can always shut it down by executing a simple <control-C>. Using *nodetach* implies that the terminal window must be open during all the session, but I do not know a better way to keep an eye at the connection.  Perhaps some day a little gnome panel application will appear to do all this in a more elegant way.
[/LIST]

---

