---
title: "cups password? which"
date: 2008-04-30
forum: Networking &amp; Wireless
---

### Post by fishtoprecords on 2008-04-30
I'm trying to get my 8.04 system to talk to a printer on my wife's XP box. I have not had cups working before the upgrade, so I'm not sure what is wrong.

When I try to select the printer, which has the device URI of
smb://accounting/l1010
something pops up a dialog box and asks for a password for my userid on localhost. But it complains that the password is incorrect.

I can do an 'help -> about' on the printer configuration, it says 
System-config-printer 0.7.81
a CUPS configuration tool.

The dialog box says "Password required" in bold,
"Password for pfarrell on localhost" with a textbox for the password

Neither my user id's password, or the root password work.

It could be that its really looking for a password on the Windows box, called accounting, but nothing hints at that.

thx
Pat

---

### Post by superprash2003 on 2008-04-30
have you enabled file and printer sharing correctly in xp?

---

### Post by fishtoprecords on 2008-05-01
> **superprash2003 said:**
> have you enabled file and printer sharing correctly in xp?

Good question. What does "correctly" mean here? 
I used to grok Windows, but I've stayed as far away from it as possible for years, so I may have missed something.

---

### Post by superprash2003 on 2008-05-02
in the folder options of windows explorer make sure than "enabled simple file sharing" is disabled.. then you get a better file sharing system.. also try the network wizard again

---

### Post by fishtoprecords on 2008-05-06
Seems to be it was complaining about cups access on my local ubuntu Hardy machine.

I added myself to the lpadmin group and now I can get past that part.
Next up: testing

---

### Post by fishtoprecords on 2008-05-06
It works. Thanks to all who had suggestions.

---

### Post by lns on 2008-11-25
This is a bug in system-config-printer for Ubuntu. Please see [https://bugs.launchpad.net/ubuntu/+source/system-config-printer/+bug/302158](https://bugs.launchpad.net/ubuntu/+source/system-config-printer/+bug/302158) for details.

---

### Post by leehach on 2009-01-04
Another way to accomplish this via the desktop is:
[LIST=1][*]go to System-->Administration-->Users and Groups

[*]Choose the user you want to be able to administer CUPS
[*]Select Properties
[*]Select the User Privileges tab
[*]Check "Manage printers"
[/LIST]  
This has the effect of adding the user to lpadmin.

---

