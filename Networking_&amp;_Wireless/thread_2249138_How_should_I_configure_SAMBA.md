---
title: "How should I configure SAMBA?"
date: 2014-10-19
forum: Networking &amp; Wireless
---

### Post by Mike_Walsh on 2014-10-19
Evening, all.

I'm trying to set up network printing.

I'm running Ubuntu 14.04 on a Compaq Presario desktop, with an Epson SX218 all-in-one connected via USB, and an Ethernet connection.

My mother has a Dell Inspiron N5110 laptop. Previously it ran only Windows 7; since approximately a fortnight ago, it now dual-boots with Ubuntu 14.04......connected to the same router via wireless.

I decided, 3 days ago, to try and set up network printing. When both machines run Ubuntu, it's quite easy, since you simply enable 'Sharing' in the Printer Properties settings, and 'Publish this printer for sharing' (or something similar; I'm in Kubuntu at the moment, and the printer set-up page is completely different!), in the 'Server Settings'.

Printing a document from the Dell worked perfectly, and printed off on my machine with no problem. Running the Dell on Windows 7, however, is another story; naturally, Windows doesn't even SEE the Compaq on the network...

I discovered that you need to run SAMBA, in order to share files & printers between Ubuntu & Windows. I've installed SAMBA, but I'm unsure as to how it should be configured.

Curiously enough, since installing SAMBA, the previously reliable print-sharing between the two Ubuntu installs has now quit working. Is this normal; and if so, as I said before, how should SAMBA be set up.....or can the two methods not co-exist? Do they cancel each other out?

Advice would be appreciated from anyone who has had experience of trying to set something similar up..!


Regards,

Mike.

---

### Post by bab1 on 2014-10-19
> **Mike_Walsh said:**
> Evening, all.

I'm trying to set up network printing.

I'm running Ubuntu 14.04 on a Compaq Presario desktop, with an Epson SX218 all-in-one connected via USB, and an Ethernet connection.

My mother has a Dell Inspiron N5110 laptop. Previously it ran only Windows 7; since approximately a fortnight ago, it now dual-boots with Ubuntu 14.04......connected to the same router via wireless.

I decided, 3 days ago, to try and set up network printing. When both machines run Ubuntu, it's quite easy, since you simply enable 'Sharing' in the Printer Properties settings, and 'Publish this printer for sharing' (or something similar; I'm in Kubuntu at the moment, and the printer set-up page is completely different!), in the 'Server Settings'.

Printing a document from the Dell worked perfectly, and printed off on my machine with no problem. Running the Dell on Windows 7, however, is another story; naturally, Windows doesn't even SEE the Compaq on the network...

I discovered that you need to run SAMBA, in order to share files & printers between Ubuntu & Windows. I've installed SAMBA, but I'm unsure as to how it should be configured.

Curiously enough, since installing SAMBA, the previously reliable print-sharing between the two Ubuntu installs has now quit working. Is this normal; and if so, as I said before, how should SAMBA be set up.....or can the two methods not co-exist? Do they cancel each other out?

Advice would be appreciated from anyone who has had experience of trying to set something similar up..!


Regards,

Mike.
I saw your earlier posts.  I share files using Samba and print via a networked printer.  The two services function independently.  Having said that, it is important to understand that each printer has to have a print server.  This can be a computer (host) that has a print server service running or as in my case a printer that has a print server built into it (or added later).  Which method are you using?

Samba can function as a print server on the computer (host) that has the printer connected to it if you need it.  I'm not sure if you need that functionality.  Ubuntu uses CUPS (common unix printing system) via IPP for this purpose.  I would guess that you would need Samba if your computer has a directly attached printer and your Windows machines can't find the printer at all. 

See [here]("https://help.ubuntu.com/community/NetworkPrintingWithUbuntu") for more information.

---

### Post by Mike_Walsh on 2014-10-21
Thanks for that! 

I've looked at so much stuff over the last few days that I'm developing square eyes..! I'm beginning to suspect part of my trouble is the firewall; I need to configure it to allow CUPS through on port 631, so, I'm currently working on that. I'm running 5 or 6 distros (all the 'buntu family, basically); and I want to set up every single distro to let CUPS through the firewall. I don't know whether I need to re-configure the printer in each one; does CUPS itself save all your changes, so that you only need to add the appropriate network printer for each OS?

I'm getting a real 'crash-course' in this stuff; see my other current thread:-

[http://ubuntuforums.org/showthread.php?t=2249262](http://ubuntuforums.org/showthread.php?t=2249262)

There's a list of sites there I've visited in the last 48 hrs or so.....and that's only a small part of what I've been browsing!

Regards,

Mike.

---

### Post by bab1 on 2014-10-21
> **Mike_Walsh said:**
> Thanks for that! 

I've looked at so much stuff over the last few days that I'm developing square eyes..! I'm beginning to suspect part of my trouble is the firewall; I need to configure it to allow CUPS through on port 631, so, I'm currently working on that. 
Sometimes it just helps to simplify the networking system you are diagnosing.  I would just turn off all the host based firewalls  until you have solved the basic printing problem.> 
I'm running 5 or 6 distros (all the 'buntu family, basically); and I want to set up every single distro to let CUPS through the firewall. I don't know whether I need to re-configure the printer in each one; does CUPS itself save all your changes, so that you only need to add the appropriate network printer for each OS?
Re-read the link I sent you.  It explains this question specifically.  The bottom line is: each host that is running Linux that is to either print to or from needs to have CUPS configured in some way.  Samba is only needed for Windows hosts.  [QUOTE]
/QUOTE]

---

