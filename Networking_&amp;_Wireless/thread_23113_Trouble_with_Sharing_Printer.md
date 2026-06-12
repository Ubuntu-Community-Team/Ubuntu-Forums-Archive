---
title: "Trouble with Sharing Printer"
date: 2005-03-31
forum: Networking &amp; Wireless
---

### Post by corza on 2005-03-31
Hi,

I have been trying to allow my windows computer share my Ubuntu connected printer. On the windows machine all the drivers and everything have been setup. But when i go into the printer it says, "Access Denied, unable to connect to printer on ubuntu". Here is my samba configuration for the printer.

[printers]
   comment = All Printers
   path = /var/spool/samba
   browseable = yes
# to allow user 'guest account' to print.
   guest ok = yes
   writable = yes
   printable = yes
   create mode = 0700

if someone can help me out with this that would be awesome.

Thanks :)

---

### Post by kleeman on 2005-03-31
I had this problem and found the answer in the Bruce Perens Open Source book on samba. First you need to create a group called nobody and make the user nobody (which should already exist) a member of it. Then do the following (from the book
The Official Samba-3
HOWTO and
Reference Guide):

Enabling Anonymous Printing
• The UNIX/Linux system must have a guest account. The default for this is usually
the account nobody. To find the correct name to use for your version of Samba, do
the following:
$ testparm -s -v | grep "guest account"
Make sure that this account exists in your system password database (/etc/passwd).
• The directory into which Samba will spool the file must have write access for the guest
account. The following commands will ensure that this directory is available for use:
root# mkdir /var/spool/samba
root# chown nobody.nobody /var/spool/samba
root# chmod a+rwt /var/spool/samba


Let me know if you find the above unclear...

---

### Post by corza on 2005-03-31
k just having trouble with putting nobody into the group 'nobody'

---

### Post by corza on 2005-03-31
Ok i followed ur steps and still i cannot get access through my windows computer..

---

### Post by kleeman on 2005-03-31
Here are the relevant lines from  my smb.conf:

[printers]
        comment = All Printers
        path = /var/spool/samba
        create mask = 0700
        guest ok = Yes
        printable = Yes
        print command = /usr/bin/lpr -P%p -r %s
        lpq command = /usr/bin/lpq -P%p
        lprm command = /usr/bin/lprm -P%p %j
        lppause command = /usr/sbin/lpc hold %p %j
        lpresume command = /usr/sbin/lpc release %p %j
        browseable = No

[print$]
        comment = Printer Drivers
        path = /etc/samba/drivers
        guest ok = Yes

The samba book has a troubleshooter you might find useful. Download it here:
[http://www.phptr.com/content/images/0131453556/downloads/0131453556.pdf](http://www.phptr.com/content/images/0131453556/downloads/0131453556.pdf)

---

