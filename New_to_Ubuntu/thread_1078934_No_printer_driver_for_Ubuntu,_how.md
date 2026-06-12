---
title: "No printer driver for Ubuntu, how?"
date: 2009-02-23
forum: New to Ubuntu
---

### Post by ohjani on 2009-02-23
I am in a mixed Windows and Ubuntu network, we only have a Ricoh Aficio 3224C print station for all the printing, scanning and copying jobs.  However, I cannot find the driver for my Ubuntu PC (and I heard they don't have any Linux driver for that model).  May I know what is your advise to solve this problem so that the Ubuntu can use the print station?

---

### Post by yeats on 2009-02-23
Is the printer attached to a workstation, or is it on a separate print server?  I use Kubuntu, which has different tools, but I'm sure there is a way to add a network printer through one of the printer management programs . . .

---

### Post by HotShotDJ on 2009-02-23
> **ohjani said:**
> I am in a mixed Windows and Ubuntu network, we only have a Ricoh Aficio 3224C print station for all the printing, scanning and copying jobs.  However, I cannot find the driver for my Ubuntu PC (and I heard they don't have any Linux driver for that model).  May I know what is your advise to solve this problem so that the Ubuntu can use the print station?This printer works perfectly with Linux.  Use the Generic PCL 5c driver when you set it up in Ubuntu.

EDIT:  According to OpenPrinting database, the proper driver is  pxlcolor-Ricoh (see: [http://www.openprinting.org/show_printer.cgi?recnum=Ricoh-Aficio_3224C](http://www.openprinting.org/show_printer.cgi?recnum=Ricoh-Aficio_3224C) )

(Google is your friend -- that is how I found this information)

---

### Post by ohjani on 2009-02-24
chrissharp123, the printer is a stand alone IP printer, not attaching to any PC.

HotShotDJ, I followed your suggestion to install both the PCL 5c  and pxlcolor-Ricoh driver but I still cannot print as I don't see a place for me to key in my user ID.  Our printer is set to use the individual ID to control the printing level.  I couldn't put in an ID to both the drivers, thus I cannot print.  May I know where do I get the ID field to fill in?

---

### Post by bailbath on 2009-02-24
I guess if you are in a mixed network you are using samba hope this helps. I only use Linux so don't have a windows network to worry about so I hope this is right for you.
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

Ubuntu Client

1. Again go to System -> Administration -> Printing

2. Click "New Printer" in the upper right. In the next menu select "Windows Printer via SAMBA". Now enter your Ubuntu Samba Print Server (set up as above) IP address in the box on the left titled "smb://". Click the "Browse" button.

3. Select the printer in the "SMB Browser" window (Click on the little arrows). Once you have selected your printer, check the "Authentication required" and enter your samba user name and password. Then click the "Verify" button. You should see confirmation that the share is available.

4. Click the "Forward" button and install the drivers for your printer as you would for any other printer.

Windows Client

1. Go to control panel -> Printers

2. Click "Add a printer" on the upper left. The printer wizard will start -> click forward. Select Network Printer and click "Next". Select "Browse for a printer" (Top button) and click "Next". In the next window, navigate to your Ubuntu Samba Print Server and click "Next". Continue with the printer and driver installation.

---

### Post by HotShotDJ on 2009-02-25
> **ohjani said:**
> HotShotDJ, I followed your suggestion to install both the PCL 5c  and pxlcolor-Ricoh driver but I still cannot print as I don't see a place for me to key in my user ID.  Our printer is set to use the individual ID to control the printing level.  I couldn't put in an ID to both the drivers, thus I cannot print.  May I know where do I get the ID field to fill in?Ah!  Ok... I understand your problem better now.  I believe Samba will take care of this for you. Bailbath's instructions look right to me.

---

### Post by ohjani on 2009-02-25
I am so sorry for didn't make the question clear, what I meant by the user code is actually the user code within the printer, not the network authentication.  You see, we can set all the users to have a user code before they are allowed to print, copy or fax something to/from the Ricoh station, the particular user code will generate a report (from the Ricoh station) to show how many pages the user has printed/faxed.  This report is for admin dept to monitor usage.  When I install the printer driver to Windows PC, I will embedded the user code in the respective printer installation and PC user cannot change the code even though they login using a different Windows user name.  The Windows printer driver installation has an utility for me to key in the user code (only a 6 digits code, no password required) and it will be fixed for that PC throughout the time.

I believe my Ubuntu already has the samba configured, or else I won't be able to transfer files to/from Windows PC.  But this time I can't get it to print to the Ricoh printer because the printer declined the access without a valid user code.  And I cannot find a place to key in the user code from the Generic PCL 5c driver.

---

