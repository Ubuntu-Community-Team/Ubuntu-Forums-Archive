---
title: "Help to setup a network between my laptop and PC to transfer files (Both have Ubuntu)"
date: 2007-06-09
forum: Networking &amp; Wireless
---

### Post by Newbie29 on 2007-06-09
Hi,

I need help to setup a network between my laptop and PC to transfer files (both have Ubuntu), like a workgroup network if I were using XP...

Thanks in advance.......

---

### Post by jim87410 on 2007-06-09
Hi,
Hopefully this will be fairly simple...
Some assumptions:
1. Both have a network card
2. You either have a switch with a ethernet cable for both <OR> a ethernet cross over cable.

I. If you have a switch, connect your laptop and PC to the switch <OR> if you have a cross over cable, just connect the laptop and PC together.

II. On each you will need to configure a static IP address.
    A.  On each computer open System -> Administration -> Network
         a. Select your Wired connection and click Properties
         b. Select Static IP Address from the Configuration Drop Down Menu.
         c.  Enter 192.168.0.1 for the PC and 192.168.0.2 for the laptop.
         d.  Enter 255.255.255.0 for the subnet mask.
         e. You can leave the Gateway address blank.
    B. Now you need to check to make sure you have connectivity.
        a. On the PC, open System -> Administration -> Network Tools
             1. On the Devices tab, select the Ethernet Interface you are using.
             2.  Select the Ping tab
             3.  Enter 192.168.0.2 and press the Ping button.  If your Packets received is the same as the Packets transmitted then you have connectivity.

III.  Now you need to share a folder on one of the machines.  Doesn't really matter which one... or you could share a folder on both.  For this discussion say you want to share a folder on the PC and connect to it with the laptop.
     A. Open System -> Administration -> Shared Folders
         a.  Click the Add button and enter the path of the folder to be shared.
         b. Share through: Windows networks (SMB)
         c. enter the Name of the share (comment that will show up on the share link)
         d. Un-check the Read Only checkbox

NOTES: If SMB hasn't been installed you will be prompted to install it.  

IV.  The only thing left is to connect to the share.
     A.  On the laptop, open Places -> Connect to server...
          a.  Service Type: Windows Share
          b. Server: 192.168.0.1
          c. Share: enter the name of the folder you shared... EXACTLY, case matters!
          d. Folder: you can leave this blank
          e. User Name: Enter the username of whoever owns the shared folder.
          f. Domain Name: can leave this blank
          g. Name to use for connection: This is the name of the folder that will identify this connection.
     B.  When you press connect, a folder will be placed on your desktop.
     C.  Open up this folder and you should be prompted for a password.  Enter the password of the user that owns the shared directory.

NOTE:  You didn't mention what version of Ubuntu you are running.  I have had various amounts of frustration using Draper to Fiesty connecting to Windows 2000 server and Windows 2000 Pro.  Fiesty has been caused less frustration than Edgy did.  If this doesn't work come on back and we will see if we can figure it out.

---

### Post by Newbie29 on 2007-06-10
Thanks, I'll try it out right away, thanks, oh and, both of them have Fiesty.....

---

