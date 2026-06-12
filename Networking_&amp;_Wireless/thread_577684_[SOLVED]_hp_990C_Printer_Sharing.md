---
title: "[SOLVED] hp 990C Printer Sharing"
date: 2007-10-16
forum: Networking &amp; Wireless
---

### Post by measekite on 2007-10-16
**[COLOR=Red]See SOLUTION down below[/COLOR]**


I am using a current updated version of Feisty on two computers.  Computer A is a wired Ethernet computer.  Computer B is a wireless Ethernet computer.  I also have a Windows Advanced 2000 Server that Computer A can access.  Both Computer A and B can access the internet.

Attached to computer A is an HP990Cse printer via usb.  The printer prints fine with all applications tested so far.

**Desire:**
I would like computer B to be able to use the printer attached to Computer A.

[COLOR=Red][B]Problem:
When Computer B submits a "Print Test Page" the print job can be seen in the Print Q but the and the job says printing but it never prints.

[/B][COLOR=Black]What I have done:
On Computer A, dual boot but running Feisty at this point in time I clicked the share printer choice.

On Computer B I went through the steps to add a new printer and chose IPP and entered the URI for the hostname that I saw on the connection tab of Computer A.  I then chose HP and selected the Deskjet-990C and selected the appropriate driver.  At this point I saw the printer and selected it for the default.  I then clicked the button to print a test page.

[/COLOR][/COLOR][COLOR=Red][COLOR=Black] The print job went into the print queue and said the job was printing. However, after some time nothing happened and I had to cancel the job.

I have also tried Windows/SMB but I though and that did not work. I thought that is only if you have Windows booted on Computer A and selected printer sharing.

It is my understanding that Computer B would have to configurte 2 printers; one to use if Computer A is running Windows and the other if Computer A is running Linux. Please correct me if I am wrong.

[COLOR=Red]**Can anyone help?  I thought this would be an easy task but it seems that something is not right.**[/COLOR]
[/COLOR][/COLOR]
[COLOR=Red][COLOR=Black]
I found the solution so I decided to post it to help others:

[/COLOR]
_**SOLUTION**_[/COLOR][COLOR=Red][COLOR=Black]

**This worked for me under Feisty:**

You have to change the line
[B]Listen 127.0.0.1:631
to
[COLOR=Red]Listen 631
Listen /var/run/cups/cups.sock[/COLOR][/B]

It may be possible to do this:  machine-name:631 if you do not want an ip address OR 192.168*:631 to narrow it down OR *631.  But the above in red worked.

in your file [COLOR=Blue]/etc/cups/cupsd.conf[/COLOR]

in order to share printers on your LAN. At least this is what selecting share printers on Feisty did

After this change you should restart cups with **[COLOR=Red]sudo /etc/init.d/cupsys stop[/COLOR]** followed by **[COLOR=Red]/etc/init.d/cupsys start[/COLOR]** (or just a reboot). 

Turning on both "Global" options both the host and client PCs was all it took.

On the Host PC I turned on Global -> [x] Share Printers. Then from the client PC I turned on Global -> [x] Detect Printers and saw the CUPS printers for the client PC. Here it was 192.168.xxx.xxx:631/printers/Deskjet-990C Ready.  It takes a up to a couple of minutes of nothing apparent happening (it searches the network for all shared printers) before the printer appeared.

Then I printed a test page.



[/COLOR]
[/COLOR]

---

