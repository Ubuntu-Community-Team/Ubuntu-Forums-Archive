---
title: "FAXING with Brother MFC model printers"
date: 2009-12-30
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2009-12-30
I have been all over the place with this problem. I have a Brother MFC-240c printer/copier/scanner/FAX. I have the printer/copier/scanner working as expected.

Following the (over complicated) instructions at the[ Brother Drivers for Linux® distributions]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html") page(s), I did:

[Pre-required Procedure (2)]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/before.html#002")
Related distributions
Ubuntu8.04/8.04.1, Ubuntu8.10, Ubuntu9.04
Related products/drivers
cupswrapper printer/PC-FAX drivers
Requirement
1. "sudo aa-complain cupsd" command is required before the installation.
2. "sudo mkdir /usr/share/cups/model" command (as it is) is required before the installation.

above reported no problems.

Then I d/l'd the cups and lpd for the FAX drivers. Again following the instructions:

Command (for dpkg)  :  dpkg  -i  --force-all  (lpr-drivername)
and the CUPS as well. The install went without errors.

The System/Admin/Printing opened and showed the BRFAX wiht a yellow warning icon on the printer-icon. That warning reads "Idle - "Filter "/usr/lib/cups/filter/brfaxfilter" for printer "BRFAX" has insecure permissions (0100777)"" - which I obtained from: [http://localhost:631/printers/?](http://localhost:631/printers/?) as well as the icon's Printer Properties.

I found this in the forums:[ Re: cups-insecure filter]("http://ubuntuforums.org/showthread.php?t=1313291") and tried:

sudo chown -hR root /usr/lib/cups/filter
sudo chown -hR root /usr/lib/cups/backend
sudo chgrp -hR root /usr/lib/cups/filter
sudo chgrp -hR root /usr/lib/cups/backend

but the only one Brother named file is in /filter and the backend contains no Brother named file, only lpd. Nautilus shows the brfaxfilter as being owned by root and by group owner root. 

Now, if you have read this far, and know the solution, please post it. However, if you are as lost as I am, wait, and I will post what the techs at Brother say, as I have an email into them. (although a little part of me thinks this ins't an end-user install problem, but rather something too complicated for non-nerds).

---

### Post by designedrat on 2010-01-02
you have to chmod 555 /usr/lib/cups/filter/brfaxfilter
Then you need to restart cups.
Then you can make sure that the error is gone by checking [http://localhost:631/printers](http://localhost:631/printers)

took me a while to find it, but it works. Hope this helps you out as well.

---

### Post by Mark_in_Hollywood on 2010-01-11
> **designedrat said:**
> you have to chmod 555 /usr/lib/cups/filter/brfaxfilter
Then you need to restart cups.
Then you can make sure that the error is gone by checking [http://localhost:631/printers](http://localhost:631/printers)

took me a while to find it, but it works. Hope this helps you out as well.

Yes, this has removed the warning icon.

---

### Post by nuchdog on 2010-03-08
I had to:

sudo chmod 700 /usr/lib/cups/backend/cups-pdf
sudo chmod 700 /usr/lib/cups/backend

also for those trying to get cups-pdf to work, you might have to manually create the folder ~/PDF

mkdir ~/PDF

---

### Post by topet2k12001 on 2010-11-21
> **designedrat said:**
> you have to chmod 555 /usr/lib/cups/filter/brfaxfilter
Then you need to restart cups.
Then you can make sure that the error is gone by checking [http://localhost:631/printers](http://localhost:631/printers)

took me a while to find it, but it works. Hope this helps you out as well.

Hi,

I have a Brother MFC-3360c printer. I also followed the instructions from the Brother website and ended up seeing the "insecure" error. This particular command you posted was the one missing thing that solved my problem. Thanks!

---

### Post by gdiloren on 2011-02-18
> **nuchdog said:**
> I had to:

sudo chmod 700 /usr/lib/cups/backend/cups-pdf
sudo chmod 700 /usr/lib/cups/backend

also for those trying to get cups-pdf to work, you might have to manually create the folder ~/PDF

mkdir ~/PDF
I can only access /usr/lib/cups the rest is access denied, because I have to do "sudo mkdir /usr/lib/cups/backend/cups-pdf" first.  I got the red exclamation point gone and the warning gone but tell me what's BRFAX doing? It doesn't print or fax or ask a fax number where to fax, I'm wondering??? :confused:

---

### Post by mwray on 2011-03-01
After re-reading thorugh Brothers Site, there is no "easy" way to use the fax, especially if your device is network attached.

Option 1. USe the PC-FAX utility (GUI)
Option 2. Use the PC-Fax utility command line.

Option 3. Use the PC_Fax Utility to roll your own print driver that prompts for proper info.

What's silly is since they already have a basic gui, and the command line verison is just a "filter" anyways, they could combine the 2 and pop-up a question box to ask about a cover page, and whom to fax to. But that would be too easy. You even have to jump through hoops on MacOSX to fax, but it's still easier than what they offer for linux.

---

### Post by arron on 2011-04-01
Took me a while, but i have about everything setup on my mfc, except for using the card readers, anyone get these going?

I have local and network printing, local and network scanning and, local and network faxing.

I kept a notes file for my install, ill post it here in hopes it may be of use to someone.  Its my own notes, so not a tutorial, but should get you on the right path...


** this is for a mfc 240c, check you have the right files / drivers for your own mfc!**

```

info:
http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html
http://chiralsoftware.com/blog/Linux-network-scanning-with-saned-9404a25b8342ba4e.html




##### printer install
# check for what drivers you need for printer and scanner, this is all for my mfc 240c
apt install brother-cups-wrapper-bh7 openjdk-6-jre
# enable proper share on windows
sudo gedit /etc/samba/smb.conf
# turn guest ok = no to yes under printers, then restart smbd
sudo restart smbd

# client printers
# install driver
apt install brother-cups-wrapper-bh7
#then setup as same as any other samba share printer, using the brother ->mfc 240c (or appropiate driver)






##### scanner with network support
apt install sane-utils xinetd xsane
# check i386 vs amd64 version
sudo dpkg -i brscan2-0.2.5-1.i386.deb
sudo dpkg -i brscan-skey-0.2.1-3.i386.deb
##or##
sudo dpkg -i brscan2-0.2.5-1.amd64.deb
sudo dpkg -i brscan-skey-0.2.1-3.amd64.deb

#this should now show the printer!
scanimage -L

#saned must be configured to expose the scanner over the net. Doing this is simple: add the network to 
/etc/sane.d/saned.conf
#You can add an entire network, like this:
192.168.1.0/24

#Make sure xinetd is active. It should be activated upon installation. You will need to add a file to the /etc/xinetd.d/saned directory to activate saned. Create a file called saned which contains:

service sane
{
   disable     = no
   socket_type = stream
   wait        = no
# saned in ubuntu does not like saned user
#   user        = saned
#   group       = saned
   user        = root
   group       = root
   server      = /usr/sbin/saned
}

#Check that /etc/services contains a line for sane like this:
sane-port       6566/tcp        sane saned      # SANE network scanner daemon
#edit this to turn on
sudo gedit /etc/default/saned


# Open "/lib/udev/rules.d/40-libsane.rules" file.
# Add the following two lines to the end of the device list. (Before the line "# The following rule will disable ..."):

# Brother scanners
ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes"

# Restart the OS.

# this is where the brother scan scripts to use with the buttons on the scanner, edit as needed
/usr/local/Brother/sane/script


##### client scanner for network sharing scanner
sudo apt install sane xsane
# edit the file /etc/sane.d/net.conf and put in the IP address of the scanner server machine
# should be up, Configure the network scanner back-end.









##### this is for FAX support...
sudo dpkg -i --force-all brmfcfaxlpd-1.0.0-1.i386.deb
sudo dpkg -i --force-all brmfcfaxcups-1.0.0-1.i386.deb
# fax machine should show up

***RENAME TO BRFAX FOR NETWORK PRINTING!!!!!***

In the menu go to System Settings, Printer and you should see another printer installed called BRFAX. The device URI is incorrectly created as /dev/usb/lp0. To correct this go to Menu, System Settings, Printers. Select BRFAX and select the Properties tab and then the Interface icon. Now click on Change and a window called Modify Printer should open. Select Local printer, Next, then select Brother MFC-215C USB#1 and click Finish.

# set proper permissions for faxing
sudo chmod 755 /usr/lib/cups/filter/brfaxfilter

-------------
Sending Faxes
-------------
The "brpcfax" utility only will send files in Postscript (.ps) format.
Any program can then print to a file named sendfax.ps.  To make a PC file, go print to file in the print menu of any app, select the name and where to save, and click "Postscript" under output format.  Then you can print under nautilus, see below for nautilus setup.

To setup Nautilus file manager, right click any file with .ps extension -> properties -> open with -> Add -> use custom command -> put in "brpcfax" -> add -> close.  Now double clicking any .ps file will bring up the brpcfax menu.  Or you can open with any viewer you like to make sure its what you want to send.

Set up the OpenOffice dialer (Sending PC-FAX to a single destination)
1. Run spadmin command to add your PC-FAX to the printer list
***spadmin command location (Example on Ubuntu8.04) : /usr/lib/openoffice/program/spadmin
2. On spadmin menu, click "New Printer" and select/input the following parameters according the menu.
- Select "Connect a fax device"
- Select "A default driver"
- Input "brpcfax -o fax-number=(PHONE)"

OR Input "/usr/bin/brpcfax" for br fax interface

- Input the name of the printer
3. Use Brother PC-FAX Interface from OpenOffice
3-1. Select the FAX printer as the destination device on OpenOffice print menu
3-2. Type the FAX number to the OpenOffice dialer.

Sending faxes from Firefox
Print as a Postscript file.
Using the "Open With -> brpcfax" method as described in the preceding section, fax the saved file from Dolphin (or Nautilus).


##### network faxing
# install brpcfax app, same package as the server, and setup for fax printing same as above.

# if the name change was done for the server setup, no worries here (this caused me a lot of time to figure out).  if you need a different fax name than "BRMFCFAX" then you will need to edit /usr/bin/brpcfax and look for this line to edit acordingly:
lprcmd="lpr -P BRFAX  -o $groupmember_opt  $lprargs"




```

---

