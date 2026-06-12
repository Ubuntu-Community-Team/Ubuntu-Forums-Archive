---
title: "[SOLVED] CUPS Connection Crashes OOo"
date: 2007-10-29
forum: Networking &amp; Wireless
---

### Post by inyoka on 2007-10-29
I have a dedicated Feisty CUPS print server.  However when I try to connect with a Gutsy client which ever program I use crashes.

I have tried three different methods of connecting the printer. First I just created a client.conf in the /etc/cups directory with the "ServerName 192.168.0.251" line added.  This works with Feisty clients.  Upon completing this I have restarted the local CUPS system, indeed I have restarted the laptop, but when trying to view the printer either through OOo Print option or using System-Config-Printer the respective program fades to grey and doesn't come back.

OOo crashes even when I don't set a printer, but system-config-printer does not, this is the second Gutsy system I've had the problem on, although the other was upgraded from Tribe4 and I thought it might just be a glitch. This however is a fresh install and different hardware.

I also tried setting system-config-printer to auto detect shared network printers, and adding each printer individually through the wizard. TNA

Could it have anything to do with the integration of system-config-printer? I have had a couple of problems with this since its inclusion, although I like it in Fedora.

FYI All other clients (Fedora 4, and Ubuntu 6.10-7.04) are still happily printing, and I can ping the server from Gutsy, and indeed access all other network services.  

Any help greatly appreciated.

---

### Post by Lambert on 2007-10-30
Have you looked in your syslog for any info relating to the crash?

---

### Post by inyoka on 2007-11-01
The daemon is running but the CUPS error log is empty.   Have now tried on 2 Gutsy machines, all other Fedora 4 and Ubuntu 7.04 computers still printing fine.
Using system-config-printer I can see the printers on the server, but after 5 seconds or so I get the following error:-

> There was a problem connecting to the CUPS server.

I click okay and system-config-printer window closes. 

I un-installed hal-cups-utils, and system-config-printer on both machines. I then reinstalled system-config-printer, and one now prints, but the GUI (system-config-printer), still crashes.  Also when selecting print in OOo it takes 3-4secs for the print dialog to come up.  :confused:

This only works on the Upgraded from Tribe 4 Gutsy machine, the fresh install still won't print.

Has anyone been able to connect Gutsy to a CUPS server without problems?

---

### Post by inyoka on 2007-11-01
At the moment I can't even format a page in OpenOffice without it crashing.  I am sure there must be other people out there who use CUPS servers.  Is anyone else getting a problem, or is their anyone who has Printing working on Gutsy using a CUPS print server?

If I don't get a fix soon I will have to switch the user to 7.04, or SuSE.  If this is happening across the board its a major bug for companies.  Anyway as a last ditch attempt I am going to delete all the CUPS and OOo files from my Apt cache folder and try reinstalling from the main repo-server without system-config-printer.
[CENTER]:confused::(:confused::(:confused:[/CENTER]
[SIZE="3"]I will check back in a bit and would really appreciate it if anyone who has got Gutsy printing through a CUPS server could they **please confirm its possible**.[/SIZE]  It will take me a couple of hours to re-install b'cuz the internet in North Sumatera is a joke.

---

### Post by inyoka on 2007-11-01
Re-downloading and installing did not work.  If anyone has any ideas please post or else its back to SuSE or Fawn.

---

### Post by SpiritIsReality on 2007-11-01
howdy
Alan Pope seems a good bet here:
[http://screencasts.ubuntu.com/MoS2007/15_Connecting_to_Printers](http://screencasts.ubuntu.com/MoS2007/15_Connecting_to_Printers)

my 2 bits worth: it sounds like the feisty print server could stand to be a gutsy one, but
that'd take sand, and could lead to even more hurt. Or else feisty the gutsy clients.
trails

---

### Post by SpiritIsReality on 2007-11-02
howdy
link from lazyart's signature
[http://www.linux-foundation.org/en/OpenPrinting](http://www.linux-foundation.org/en/OpenPrinting)
set debugging
[http://www.linuxprinting.org/kpfeifle/LinuxKongress2002/Tutorial/VII.cups-help/VII.cups-help.html#tell1](http://www.linuxprinting.org/kpfeifle/LinuxKongress2002/Tutorial/VII.cups-help/VII.cups-help.html#tell1)
might help?

lazyat post 5 here
[http://ubuntuforums.org/showthread.php?t=474746](http://ubuntuforums.org/showthread.php?t=474746)
trails

---

### Post by Screaming Monkey on 2007-11-02
Not sure if this is where I should post, but I've just noticed that I have printing problems (I so rarely print from home, that I haven't noticed until now).  I upgraded to Gutsy when it was released.  And I can't print from Openoffice or Scribus.  

Openoffice just hangs on me.  Scribus doesn't hang, but when I print from it, I get a stopped message in the print jobs dialog.  I have been able to print a test page no problem and also a PDF from their standard PDF viewer. Haven't tried with anything else just yet.  

Any advice?

oh, I have an HP Deskjet 3845 and it worked fine in Fawn.

---

### Post by inyoka on 2007-11-02
Does OpenOffice hang when you go to Page>Format?  Or when you go to System>Administration>Printers in Gnome?  If it does you have a similar problem to me, I'll post a solution here as soon as I find one.

---

### Post by inyoka on 2007-11-02
[Also you can answer my poll of people with this problem, just click this text, I know a few people are having similar problems, but I installed another Gutsy system tonight that doesn't have the problem.  I think its a wide-spread problem but have yet to identify the cause.]("http://ubuntuforums.org/showthread.php?t=599554")

---

### Post by Screaming Monkey on 2007-11-02
It crashes when I go Page>Format in OpenOffice, but not when I go into System>Administration>Printers. 

I'll scout around too and if I find something, I'll post it here too.  But I'm a bit of a newb still, so don't hold your breath. ;)

---

### Post by v.cecchetto on 2007-11-09
[https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/153173](https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/153173)

Try to change your theme to Human

---

### Post by inyoka on 2007-11-09
Thanks v.cecchetto although I havn't tried it on all my computers it seems to be working.  My one working machine uses Human, this PC which has several problems is using UbuntuStudio theme and having switched to human now seems much better.  

My wifes which gives me my most problems (of course it would have to be my wifes) is using crux which is mentioned in the thread you linked to. I'll go into work tomorrow morning and try both systems with my CUPS server if it works I'll close the thread.

Thanks again v.cecchetto, I told my wife I'd get her printing working on her Birthday (today), and thanks to you it looks like I've managed it.

Screaming Monkey does this solve your problem also?
[CENTER]:):KS:)[/CENTER]

---

### Post by inyoka on 2007-11-09
FYI - If you don't mind loosing OpenOffice Gnome integration try removing OpenOffice-Gtk, this fix was suggested by Innovator on launchpad.
[URL="https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/131526"]
This is the Bug Report and related discussion.[/URL]

---

### Post by inyoka on 2007-11-10
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/131526](https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/131526) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Yep this problem is certainly solved by switching to the Human theme, OR via the fix suggested by Innovator of removing the OpenOffice-Gtk package.  

However things are not perfect, I get delays of a couple of seconds when doing something like changing the page orientation in OpenOffice, but it doesn't crash.

Special thanks to **v.cecchetto** for pointing me in the right direction, and everyone else who helped along the way.

---

