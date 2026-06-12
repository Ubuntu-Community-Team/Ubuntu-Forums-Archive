---
title: "STILL need help with wireless printing"
date: 2009-05-12
forum: New to Ubuntu
---

### Post by donniemack1 on 2009-05-12
[SIZE=3]Hello,[/SIZE]

[SIZE=3]Been working on this all day and can't get all the steps I need to complete the task.  I have a PC that I just loaded Ubuntu 9.04 on.  I reformatted and took Windows completely off, so a clean install or Ubuntu.  I was running Windows XP Pro, have a cable modem (wired connection to my PC)  I have a Dell laptop that has print privileges and a wireless router so the laptop can connect to the internet.  

Since I installed Ubuntu (Home edition) 9.04 I cannot print with my laptop.  I have received some information via a previous post and made some changes to [/SIZE][SIZE=3][COLOR=Blue]smb.conf[/COLOR][/SIZE][SIZE=3]  Following is what I have done so far in this file regarding printing:

[/SIZE][SIZE=3][COLOR=Blue]########## Printing ##########

# If you want to automatically load your printer list rather
# than setting them up individually then you'll need this
#   load printers = yes

# lpr(ng) printing. You may wish to override the location of the
# printcap file
;   printing = bsd
;   printcap name = /etc/printcap

# CUPS printing.  See also the cupsaddsmb(8) manpage in the
# cupsys-client package.
    printing = cups
    printcap name = cups
    security = share

[printers]
   comment = All Printers
   browseable = yes
   path = /var/spool/samba
   printable = yes
   guest ok = yes
   use client driver = yes
   read only = yes
   create mask = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
   comment = Printer Drivers
   path = /tmp
   browseable = yes
   read only = yes
   guest ok = no
# Uncomment to allow remote administration of Windows print drivers.
# You may need to replace 'lpadmin' with the name of the group your
# admin users are members of.
# Please note that you also need to set appropriate Unix permissions
# to the drivers directory for these users to have write rights in it
;   write list = root, @lpadmin[/COLOR][/SIZE][SIZE=3]


If there are other changes to be made or problems with what I've done so far, please advise.  Also, how do I get the laptop to [/SIZE][SIZE=3][COLOR=Blue]see[/COLOR][/SIZE][SIZE=3] the printer that is local to the Ubuntu machine.  I'm stuck... Please help.


thanks in advance for your help,
donniemack1[/SIZE]

---

### Post by cariboo on 2009-05-13
I use cups to share the printer connected to my server. Start the cups web interface:

```
http://localhost:631
```

Install the printer, and there is an option to allow the rest of the network to see the printer. See the screenshot.

---

### Post by donniemack1 on 2009-05-13
> **cariboo907 said:**
> I use cups to share the printer connected to my server. Start the cups web interface:

```
http://localhost:631
```

Install the printer, and there is an option to allow the rest of the network to see the printer. See the screenshot.
Thank you so much.  Gonna try this right now.
donniemack1

---

### Post by donniemack1 on 2009-05-13
I've run into trouble setting this up.  I have a laptop connected to a wireless router so it can access the internet.  I simply want to print from my desktop (running Ubuntu 9.04 with attached HP deskjet 960c) printer.  How do I set up the laptop (running windows xp pro)  I guess my biggest problem is telling the laptop where to find the printer.  ie I can't seem to figure out the "location" of the printer so the windows laptop can see it.  Can you help with this?

thanks
donniemack1

---

### Post by manofthefield on 2009-05-13
I'm going through the same thing (been following your thread).  Here's where I'm at on my WinXP Pro laptop (and I'm guessing you're at the same point):

[IMG]http://img.photobucket.com/albums/v213/manofthefield/printsetup1.jpg[/IMG]

Then it can't find it on it's own:

[IMG]http://img.photobucket.com/albums/v213/manofthefield/printsetup2.jpg[/IMG]

Not sure what file path or url to use to find the printer connected to my Ubuntu pc (wired to wireless router)

Can't find printer from Vista laptop either

---

### Post by Jazzy_Jeff on 2009-05-13
See if this helps [http://localhost:631/help/network.html?TOPIC=Getting+Started&QUERY=](http://localhost:631/help/network.html?TOPIC=Getting+Started&QUERY=)

---

