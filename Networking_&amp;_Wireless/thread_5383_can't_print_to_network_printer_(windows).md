---
title: "can't print to network printer (windows)"
date: 2004-11-18
forum: Networking &amp; Wireless
---

### Post by leeech on 2004-11-18
I have a windows shared printer

when i try smb://windowspc/

i do not see my shared printer?

smbclient shows the printer

$ smbclient -L //windowspc
Domain=[FARADELL] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

        Sharename       Type      Comment
        ---------       ----      -------
        IPC$            IPC       Remote IPC
        print$          Disk      Printer Drivers
        Documents       Disk
        HPLaserJ        Printer   HP LaserJet 6L
Domain=[FARADELL] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

        Server               Comment
        ---------            -------

        Workgroup            Master
        ---------            -------

---

### Post by leeech on 2004-11-18
anyone? thank u

---

### Post by Yoda_Oz on 2005-02-03
bump...

im having exactly the same problem. Im able to browse the windows network in nautilus fine but there are no printers. if i use smbclient it sees that there is a printer...

first i type:
smbclient

and i get:

Domain=[UPSTAIRS] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

        Sharename       Type      Comment
        ---------       ----      -------
        Dell_Printer    Printer   Dell AIO Printer A920
        IPC$            IPC       Remote IPC
        print$          Disk      Printer Drivers
        SharedDocs      Disk
        ftproot         Disk
        ADMIN$          Disk      Remote Admin
        C$              Disk      Default share
Domain=[UPSTAIRS] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

        Server               Comment
        ---------            -------

        Workgroup            Master
        ---------            -------

then i type in:
lpadmin -p DellPrinter -v smb://username:password@upstairs/Dell_Printer -P /root/dellprinter.ppd

and i get the error instantly:
lpadmin: add-printer (set model) failed: client-error-not-found

i have set up unix printing on my windows box. i have also set up another username and password (with admin privs) on the windows box... what else do i need? why can the lpadmin find the printer?

whats going on here?

cheers for any help at all... ive been googling for a couple of hours now!

---

### Post by WillCooke on 2005-02-10
At the moment I'm at work and don't have my linux box to hand to check what I'm about to say, so if it's all non-sense I'm sorry and I'll update when I get home.

So... I had a problem similar to this one on my Debian box before I blew it away and installed Ubuntu, and as yet I haven't got around to trying to set printing up again, but..

Have a look at the samba log's there is probably a bit more information in there than you'll get from a standard error message, also turn the logging up a bit from the default to something more verbose.

Also consider installing SWAT, it takes a lot of the pain out of sucessfully configuring a samba printer.

It's also worth sharing the printer on the windows machine with full access to everyone until you've got it working properly.

Sorry if this is all obvious stuff you've already tried, but I think the key here is to look at the samba logs to see what is actually going on when ubuntu tries to connect to the printer.

HTH,

W

---

