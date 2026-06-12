---
title: "CUPS Server Error Ubuntu 8.10"
date: 2008-12-20
forum: New to Ubuntu
---

### Post by hapsis on 2008-12-20
Hi!

I'm really frustrated for this problem:

1. I can install and print test page from "printing", I print thru home network and WinXP machine, I need to unplug the network cable because the config program tryes to go to my WinXP computers IP address but after unplugging cable I'm able to config the printer for me, BUT when I try to set this printer as my default printer from the "default printer" -applet I will receive error "CUPS Server error - CUPS scheduler is not running" -message. And I can't find my printer from any application such as OpenOffice or gedit nor print with it normally, only test page.

2. I've tried several fixes from forums but it seems that all instructions are outdated, I have also tried re-install all CUPS and printing stuff from Synaptics but no help.

3. It seems that if I could really clean all CUPS related and CUPS config files and redo them all again - it could possible help but I haven't found really good instructions for that.

4. What is the "latest" with this "CUPS bug" -> have anyone found solution? Ubuntu is 8.10, and home network I have on 192.168.0.102 a windows XP machine with Epson DX4850.

5. I also have tried to use CUPS web interface but when I try to do any config on it, it asks password and user name for me - root password doesn't work or any other. I also checked these instructions from forums but haven't got solution from those either... But I can do the config from "Gnome" -printing tool... But can't make it as default printer and show up to other programs.

So, "Linux Santa" my wish list numer 1. is that I want my CUPS working - so I could finally give up my Windows for ever... Any dwarf there to help me?

- Hapsis Ipex

---

### Post by cmnorton on 2008-12-20
Is cups installed?

sudo dpkg --get-selections | grep cups  

Is cups running?

ps -ef | grep cups

---

### Post by hapsis on 2008-12-22
Hi! 

I've got the following with those commands:

> 
hapsis@hapsis-laptop:~$ sudo dpkg --get-selections | grep cups  
[sudo] password for hapsis: 
cups						install
cups-bsd					install
cups-client					install
cups-common					install
cups-dbg					install
cups-driver-gutenprint				install
cups-pdf					install
cupsddk						install
cupsddk-drivers					install
cupsys						install
cupsys-bsd					install
cupsys-client					install
cupsys-common					install
cupsys-dbg					install
cupsys-driver-gutenprint			install
gnome-cups-manager				deinstall
hal-cups-utils					install
libcups2					install
libcupsimage2					install
libcupsys2					install
libgnomecups1.0-1				install
libgnomecupsui1.0-1c2a				deinstall
libnet-cups-perl				install
python-cups					install
python-cupshelpers				install
hapsis@hapsis-laptop:~$ ps -ef | grep cups
root      5711     1  0 11:31 ?        00:00:00 /usr/sbin/cupsd
hapsis   15790 10992  0 11:39 pts/0    00:00:00 grep cups
hapsis@hapsis-laptop:~$ 



There came an update for CUPS today and it helped me so that the web -interface accepts now my root name and password and I managed to put the printer as default printer. Even the test page comes from the CUPS web interface BUT the printer still doesn't show up on any program - I just can print to a file. If I try to use GNOMEs "default printer" -icon from the addministration menu - that program hangs.

- Hapsis Ipex

---

### Post by cmnorton on 2008-12-22
How is this printer connected to your Ubuntu system?

---

### Post by hapsis on 2008-12-23
> **cmnorton said:**
> How is this printer connected to your Ubuntu system?


Printer is Epson DX4850 and it's connected to WinXP -machine on local network (on ip 192.168.0.102).

- Hapsis

---

### Post by cmnorton on 2008-12-23
Then it won't necessarily be automatically detected. You must provide the "bridge" to it through CUPS. 

Here's a CUPS entry to my printer that is shared out on an XP workstation. It's much easier to find a printer shared out on a Windows server, and I believe this has to do with the various workstation, server, and messenger services that run on Windows, but run slightly differently between Windows workstation and server implementations.

 smb://MY_DOMAIN1/MY_WINDOWS_NODE/print_share_name

---

