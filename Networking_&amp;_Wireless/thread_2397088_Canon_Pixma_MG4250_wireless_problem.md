---
title: "Canon Pixma MG4250 wireless problem"
date: 2018-07-25
forum: Networking &amp; Wireless
---

### Post by xoob on 2018-07-25
Canon Pixma MG4250, Dell Inspiron 1520, Technicolor TG582n (plusnet), Xubuntu 18.4 /Windows 10 Home.
 
 
 In Xubuntu, the Pixma prints and scans with a usb connection but I can’t get it work wirelessly.
 
 
 The printer app detects the printer, searches for additional software, doesn’t find any and returns the message ‘There was an error during the CUPS operation ‘server-error-internal-error’.
 
 
 The Canon website has 6 driver files to download – source, rpm and deb for printing and scanning.
 
 
 I extract the deb.tar.gz file to get a deb file but trying to install using the dpkg -i command returns ‘This is not a regular deb file’.

 
 
 The extracted source file contains no configure folder and the help file refers to rpmbuild command.
 
 
 Any comments would be appreciated.

---

### Post by chili555 on 2018-07-25
It seems that if the printer scans and prints when attached by USB, then your xubuntu computer has the drivers it needs already. The only thing that should change is the URI. In other words, the Device URI is now usb:/something and you want to change it to network protocol ipp:/something. I suspect that the result will be close to ipp:/192.168.0.5:631/lpr where 192.168.0.5 is the IP address of the printer and 631 is the port used by CUPS.

Rather than deleting the USB printer and auto-detecting the wireless printer, simply change its URI.

Are there any informative clues in the log?```
less /var/log/cups/error_log
```'less' allows you to scroll through the log using the up/down arrows. Get out of less with Q.

---

### Post by xoob on 2018-07-26
Thank for your reply.

I am new to linux. I know the IP address of my printer is 192.168.1.76 which I set as static. I don't know how to access or change the port number.

The error log is ...

E [26/Jul/2018:07:31:33 +0100] Unknown directive JobPrivateAccess on line 123 of /etc/cups/cupsd.conf.
 E [26/Jul/2018:07:31:33 +0100] Unknown directive JobPrivateValues on line 124 of /etc/cups/cupsd.conf.
 E [26/Jul/2018:07:31:33 +0100] Unknown directive SubscriptionPrivateAccess on line 125 of /etc/cups/cupsd.conf.
 E [26/Jul/2018:07:31:33 +0100] Unknown directive SubscriptionPrivateValues on line 126 of /etc/cups/cupsd.conf.
 E [26/Jul/2018:08:27:59 +0100] [cups-deviced] PID 5120 (gutenprint52+usb) stopped with status 1!
 E [26/Jul/2018:08:30:29 +0100] [CGI] Unable to create PPD file: Printer does not support required IPP attributes or document formats.
 E [26/Jul/2018:08:30:40 +0100] [CGI] Unable to create PPD file: Printer does not support required IPP attributes or document formats.
 E [26/Jul/2018:08:30:40 +0100] copy_model: empty PPD file
 E [26/Jul/2018:08:30:40 +0100] [Client 20] Returning IPP server-error-internal-error for CUPS-Add-Modify-Printer (ipp://localhost/printers/Canon-MG4200-series) from localhost
 E [26/Jul/2018:08:30:40 +0100] [CGI] Unable to create PPD file: Printer does not support required IPP attributes or document formats.
 E [26/Jul/2018:08:30:40 +0100] copy_model: empty PPD file
 E [26/Jul/2018:08:30:40 +0100] [Client 23] Returning IPP server-error-internal-error for CUPS-Add-Modify-Printer (ipp://localhost/printers/Canon-MG4200-series) /var/log/cups/error_log

Thanks.

---

### Post by chili555 on 2018-07-26
>  Unknown directive JobPrivateAccess on line 123 of /etc/cups/cupsd.conf.May I assume that, as you are new to Linux, that you haven't made any changes to the file /etc/cups/cupsd.conf. Is that correct?

I am simply suggesting that you go to Settings > Devices > Printers and edit the settings:  [https://i.stack.imgur.com/NstCh.jpg](https://i.stack.imgur.com/NstCh.jpg)

In this example, the printer is now set us as a USB printer. I suggest that you click Change... and change the device URI to:```
ipp:/192.168.1.76:631/lpr
```Save and see if you can print a test page.

If not, let us see the last twenty or so lines from the error log as above.

---

### Post by xoob on 2018-07-27
I haven&#8217;t changed the file /etc/cups/cupsd.conf.
 
 
 In printer settings I changed the device URI to:     ipp:/192.168.1.76:631/lpr

 
 
 Trying to print I get    Processing - Unable to locate printer  

 
 
 The error log -  
 E [27/Jul/2018:09:04:10 +0100] Unknown directive JobPrivateAccess on line 123 of /etc/cups/cupsd.conf.
E [27/Jul/2018:09:04:10 +0100] Unknown directive JobPrivateValues on line 124 of /etc/cups/cupsd.conf.
E [27/Jul/2018:09:04:10 +0100] Unknown directive SubscriptionPrivateAccess on line 125 of /etc/cups/cupsd.conf.
E [27/Jul/2018:09:04:10 +0100] Unknown directive SubscriptionPrivateValues on line 126 of /etc/cups/cupsd.conf.
E [27/Jul/2018:09:14:03 +0100] [cups-deviced] PID 2769 (gutenprint52+usb) stopped with status 1!
E [27/Jul/2018:09:15:57 +0100] [cups-deviced] PID 2920 (gutenprint52+usb) stopped with status 1!

I am thinking I should try re-installing the cups file?

---

### Post by chili555 on 2018-07-27
> I am thinking I should try re-installing the cups file?Let's see what is on the lines mentioned.

My cupsd.conf file has, at lines 123-126:```
  # All printer operations require a printer operator to authenticate...
  <Limit Pause-Printer Resume-Printer Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After Cancel-Jobs CUPS-Accept-Jobs CUPS-Reject-Jobs>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>

```Please see if yours is identical with:```
sudo apt install vim
sudo vim /etc/cups/cupsd.conf
```vim has a line counter so you can scroll down to lines 123-126.  Get out of vim with Esc, then :q!

Note that the error listing appears in both log snips you posted.

Do you see any differences?

---

### Post by arthur660 on 2018-10-17
> **xoob said:**
> Canon Pixma MG4250, Dell Inspiron 1520, Technicolor TG582n (plusnet), Xubuntu 18.4 /Windows 10 Home.
 
 
 In Xubuntu, the Pixma prints and scans with a usb connection but I can’t get it work wirelessly.
 
 
 The printer app detects the printer, searches for additional software, doesn’t find any and returns the message ‘There was an error during the CUPS operation ‘server-error-internal-error’.
 
 
 The Canon website has 6 driver files to download – source, rpm and deb for printing and scanning.
 
 
 I extract the deb.tar.gz file to get a deb file but trying to install using the dpkg -i command returns ‘This is not a regular deb file’.

 
 
 The extracted source file contains no configure folder and the help file refers to rpmbuild command.
 
 
 Any comments would be appreciated.

Actually I also have the same problem with you, I searched on several Canon sites but didn't find it.
I used to download drivers on this site [https://www.canon-europe.com](https://www.canon-europe.com) and [https://www.canonsoftwaredrivers.com](https://www.canonsoftwaredrivers.com).

---

