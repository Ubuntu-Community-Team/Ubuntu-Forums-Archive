---
title: "upgrade to gutsy breaks network printing"
date: 2007-10-24
forum: Networking &amp; Wireless
---

### Post by bcrowell on 2007-10-24
I upgraded to gutsy, and when Update Manager asked me if it should replace the edited cupsd.conf file with a new, default one, I said yes, although I did save the old version of the file. Network printing is no longer working, and I'd prefer not to have to restore my old cupsd.conf, because I'm assuming the reason Update Manager wants to replace hand-edited ones is that otherwise you could end up with a misconfigured system.

Here's what I've done so far:

#  /usr/share/cups/enable_browsing 1
System->Administration->Printing > Server Settings > share ...

I have two other machines on my local network, a mac and a linux box.

The mac now allows me to print to the machine with the printer on it. However, every file I print comes out as a few lines of raw postscript, followed by a whole bunch of blank pages. This didn't happen before I upgraded the linux machine to gutsy.

Then there's the other linux machine (also running ubuntu). The ubuntu client used to print fine to the ubuntu server before I upgraded the server to gutsy. After the upgrade, it no longer listed the server's printer as a choice on its menus. I tried to follow the directions at [https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu) to get it to work again. First I did system>admin>printing>global settings>detect lan printers> new printer>newtork printer . The help page linked to says that I should make an ipp:// url using the ip address of the server, combined with "the name you gave the printer when you set it up (usually the model of the printer)." I'm not sure what name to use here. In the cups interface, the printer's page in the cups web interface is [http://localhost:631/printers/Brother_HL-1440_series_USB_1](http://localhost:631/printers/Brother_HL-1440_series_USB_1), so I tried ipp://192.168.1.104/printers/Brother_HL-1440_series_USB_1 . (In some other places in the cups web interface, it uses the name HL-1440%20series.) Once I've done that, when I try to print I get the following under HL-1440 Properties: "Printing: Unable to get printer status (client-error-forbidden)!" It seems strange to me that this would be forbidden, since printing does seem to be allowed from the mac (although it doesn't work properly). Looking through the new cupsd.conf file, I have this:

```
<Location />
  # Allow shared printing...
  Order allow,deny
  Allow @LOCAL  
</Location>
```

In my old one, I had this:

```
<Location />
Order Deny,Allow
Allow From All 
</Location>
```

Is this the problem? I could hack around on the cupsd.conf file in an editor, but it seems like I'd then get back to the same situation on my next upgrade: I'd be forced to abandon my hand-edited conf file, and have more problems. It seems like ubuntu prefers for you to do all this stuff through the gnome gui, but I just can't figure out how to fix the present problem through the gnome gui.

I've attached my new cupsd.conf file.

Here are some errors from the /var/log/cups/error_log , which I assume were from the attempts to print from the linux client:

```
E [24/Oct/2007:13:27:22 -0700] Pause-Printer: Unauthorized
E [24/Oct/2007:13:27:24 -0700] Resume-Printer: Unauthorized
E [24/Oct/2007:13:33:47 -0700] CUPS-Add-Modify-Printer: Unauthorized
E [24/Oct/2007:13:33:53 -0700] CUPS-Add-Modify-Printer: Unauthorized
E [24/Oct/2007:13:43:24 -0700] cupsdAuthorize: Local authentication certificate not found!
E [24/Oct/2007:13:43:24 -0700] cupsdAuthorize: Local authentication certificate not found!
E [24/Oct/2007:13:43:24 -0700] cupsdAuthorize: Local authentication certificate not found!
E [24/Oct/2007:13:43:24 -0700] cupsdAuthorize: Local authentication certificate not found!
E [24/Oct/2007:13:43:24 -0700] cupsdAuthorize: Local authentication certificate not found!
E [24/Oct/2007:13:45:37 -0700] Pause-Printer: Unauthorized
E [24/Oct/2007:13:45:57 -0700] Resume-Printer: Unauthorized
E [24/Oct/2007:13:46:35 -0700] Pause-Printer: Unauthorized
E [24/Oct/2007:13:46:38 -0700] Resume-Printer: Unauthorized
E [24/Oct/2007:13:48:43 -0700] Pause-Printer: Unauthorized
E [24/Oct/2007:13:48:58 -0700] Resume-Printer: Unauthorized
E [24/Oct/2007:13:50:10 -0700] [Job 541] Unable to write print data: No such device
E [24/Oct/2007:13:50:10 -0700] Pause-Printer: Unauthorized
E [24/Oct/2007:13:50:15 -0700] Resume-Printer: Unauthorized
E [24/Oct/2007:14:12:19 -0700] DNSServiceRegister failed with error -65537
```

Thanks in advance for any help!

-Ben

---

### Post by vernhcclab on 2007-11-07
Hi,

This may not apply, and I am certainly no expert, but when I upgraded to Gutsy from Feisty I found that  I could no longer share the printer.  I did not actually upgrade, but did a fresh install of Gutsy.  When I go to System=>Administration=>Printing, the dialog box is changed from Feisty.  I could not find the appropriate settings on this box (they may be there, but I couldn't find them).  

So, I downloaded gnome-cups-manager (sudo apt-get install gnome-cups-manager), and then I ran it (sudo gnome-cups-manager).  This gave the more familiar (to me) dialog box for setting up printing.  I went to the global settings and turned on Detect LAN Printer and Share Printers, and this worked in my case.  Hope this helps

---

### Post by twelve17 on 2007-11-19
For me, I had to explicitly put my network in the <Location />
 section.  Looks like the @Local wasn't doing what I think it should be doing.

---

### Post by Ariaflame on 2007-11-22
I upgraded to gutsy and did similar thing and it stopped working. Then  went to help.ubuntu.com/community/NetworkPrintingFromWinXp and it worked again. 

Then recently after an upgrade (couldn't tell you whether it was windoze or Ubuntu as I don't print that often) it stopped working again. Tried setting a smbpasswd. No joy. 

The only way I got it working was to pretend my laptop wasn't on the LAN and tell the printer server to accept printing from the internet. It didn't require that when I first upgraded. Gah.

---

### Post by mabovo on 2007-11-22
Has anybody filled a bug report on this ?
Because CUPS is giving a lot of headache lately.
So far, just to add a network printer on my LAN it asks me for a password for localhost.

What that means ? I've never seen something like this, only in Gutsy.

---

### Post by Ariaflame on 2007-11-22
Not yet. Too new at this really to give adequate information. 

Oh, and it now refuses to connect even if I make it ok to print from internet (it reverted back to not doing it during the night)

---

### Post by bcrowell on 2008-02-02
This turned out to be the following bug:

[http://www.cups.org/articles.php?L520+T+P1+Q](http://www.cups.org/articles.php?L520+T+P1+Q)

debian/patches/fix_regression_reactivate_net_ifaces_changes_detection.dpatch :
     Fix a regression in upstream code that has removed the network interface
     update poll (CUPS STR #2631, LP: #177075). Thanks to Hugues Fournier
     (hugues dot fournier at gmail dot com) for the patch.

---

