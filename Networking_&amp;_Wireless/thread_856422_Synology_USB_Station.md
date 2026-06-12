---
title: "Synology USB Station"
date: 2008-07-11
forum: Networking &amp; Wireless
---

### Post by trevh on 2008-07-11
I've just installed Ubuntu and I want to connect to by Synology USB Station.
The Synology website doesn't say it supports Linux for the USB Station and the firmware version is wrong to allow me to use their documented workaround for their other devices.
I hoped and expert out there could advise me on how to set it up.
A port scan shows the device as:

192.168.1.159:80 Open HTTP (this will be the web interface)
192.168.1.159:139 open netbios-ssn
192.168.1.159:445 open microsoft-ds
192.168.1.159:515 open printer
All  other ports are closed.

I have a 350 gb drive attached to the device that is ext3 formatted and an Epson printer.

The device supports FTP, but I haven't enabled it. Not sure if that helps.

---

### Post by trevh on 2008-07-13
Well, lots of playing and I've had a major success.
I entered the following command from a terminal

sudo mkdir /etc/win

Then edited /etc/fstab with

//192.168.1.159/public /mnt/win cifs defaults 0 0

And now I can see the network attached drive via the file browser in File System /mnt/win

Fantastic, really pleased with myself.

Now I have the next stumbling block.

How to do the printer. I want Cups to see it, don't know if this is right but I've done sudo mkdir /etc/printer and added to /etc/fstab

//192.168.1.159/printer /mnt/printer cifs defaults 0 0

However, it doesn't matter if I use //192.168.1.159/printer or /mnt/printer when defining to cups, I can't seem to see the printer.

---

### Post by Macchi on 2009-07-27
Synology USB Station works in Ubuntu for file sharing and printing without any modifications to the system.

FILE SHARE
To access the file shares got to Places->Network and browse to desired file share (admin, private, or public). The usernames for admin is apparently just "admin" and for private is "guest". You may also access the ftp area through Places->Connect to Server->FTP (with login) 

PRINTER
Set up your printer as usual in System->Administration->Printing->New Printer and choose "Internet Printing Protocol" from the list. Provide the IP address for the USB Station and the queue should be /printers/usbprinter1 or /printers/usbprinter2 


It works fine for me despite the statements from the supplier that it is not compatible with Linux!







OBS: Dear Trevh, a)/etc/fstab contains the entries for the filesystem and is not related to the printing system (CUPS) in GNU/Linux and Ubuntu. b)The /etc contains folders and configuration files for the system but it is not directly related to mount points in the system other that in very special cases.
Mounting the file share manually in fstab as you did may work fine but will be less flexible in many cases. I personally would recommend accessing the file-shares through the built-in smb (samba) in Ubuntu.

---

