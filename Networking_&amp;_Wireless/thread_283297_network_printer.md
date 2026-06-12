---
title: "network printer"
date: 2006-10-24
forum: Networking &amp; Wireless
---

### Post by Soccerguy on 2006-10-24
I am running Ubuntu and would like to print off my WinXP network printer which is fully supporter.  I assume I go to System/amin/printer/add printer, but what would the host name be?   BTW, I can get to the windows computer fine through the connect to server route and file browser.  It opens the graphics images, but tells me the .doc files don't exist.  They do, but they are not open on the Win machine

---

### Post by squibT on 2006-10-24
From a post found here:

How to setup your Ubuntu machine so it can print to a Windows XP shared printer

It was suggested that I add this from the following thread:
[http://ubuntuforums.org/showthread.p...7&page=1&pp=10](http://ubuntuforums.org/showthread.p...7&page=1&pp=10)

Step 1: Installing Samba on Ubuntu

    * Click System -> Administration -> Synaptic Package Manager
    * Enter your password
    * Now click Search and type Samba in the search box.
    * You should now see a list of items containing the word Samba.
    * Right click on the Samba with the little ubuntu icon on it and select mark for installation.
    * Click apply
    * The packages will now be downloaded and installed.


Step 2: Checking if your network is working

    * Find the ip address of your windows xp machine by going ... start -> run
    * Then type cmd
    * type ipconfig in this window and you should see your ipaddress there.
    * Now on your ubuntu machine goto the command line
      and type ping <your windows ip address>
    * see if you get a response.
    * add unix printing Add/Remove Programs

if you get timeouts:
a.) Check if your network cables are all connected
b.) Check if your network cards are working
c.) Check the settings of your network interfaces
d.) Try disabling any firewall software

Step 3: Sharing the Windows XP printer

    * start -> settings -> control panel
    * open printer and faxes
    * find the printer you wish to share with your ubuntu machine
    * Right Click -> properties on it and goto the sharing tab.
    * Click on share this printer and type a short name in the share name box.

Step 4: Adding the printer on the Ubuntu machine

    * System -> Administration -> Printing
    * Click Printer -> Add Printer
    * Click on network printer.
    * Select Windows Printer (SMB) from the dropdown.
    * In the host section type the IP address of your windows machine.
    * In the printer section type the share name you gave your printer
    * Now enter your username and password for your ubuntu machine.
    * Click forward.
    * Now select the manufacturer and model of your printer.
*************************************************************

---

### Post by Soccerguy on 2006-10-24
Great post, and thanks.  It might have been easier to replace "host selection" with "Host IP address" or something.  While I'ver been using Linux off and on for a few years, there is still places where a difference in terminology between Linux and Windows still gives me pause.

Also, Under step 4, When a person goes into Control Panel>Printers and Faxes, they will see the printer they wish to share with Linux, but if that printer is already on a network, they still need to click on the printer and go to printer>sharing and take note of what the share name is.  In my case, under printers and faxes it shows up as a LaserJet, but under Printer>sharing it was assigned Printer6, which is what needs to go in the printer selection type on the Linux box, not LaserJet XXX.  On my Windows machine, it was set up so long ago on the network, I'd forgotten that the share name was different than the assigned name in the Contol Panel.  I remembered it right away when the test page didn't print, but I can understand where that would be confusing.

---

