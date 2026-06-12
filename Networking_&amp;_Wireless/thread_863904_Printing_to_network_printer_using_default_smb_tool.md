---
title: "Printing to network printer using default smb tool"
date: 2008-07-19
forum: Networking &amp; Wireless
---

### Post by hchristopher on 2008-07-19
Hello.  I recently joined an Ubuntu 8.04 Desktop box (32-bit PC) to our Windows AD using a program called Likewise.  However, I can't seem to connect to the network printer (which is connected to a Windows print server).  I've tried using the built-in add printer tool (the 'smb' section), but it doesn't seem able to recognize the printer share.  I'm using the same server and share name info that is used on the Windows and Mac machines on our network.

Is there any special insider tricks for getting that to work?  Or is there some program I could install that would be able to scan AD for the printer? (The printer is published).  The Ubuntu documentation didn't seem to provide any really detailed troubleshooting info.

---

### Post by superprash2003 on 2008-07-19
typing the full correct location of the printer from the windows print server may help..

---

### Post by hchristopher on 2008-07-30
I was able to get connected to the printer and print to it.  However, this has led to another problem:

Ubuntu requires a valid domain account and password to be able to connect to the printer and print to it.  This was not a problem at first, because I just entered my own, and everyone who used the machine was able to print through that account.

However, as soon as I changed my domain password (as I do regularly), the Ubuntu machine was no longer able to print to those printers.

Is there some way to change the configuration so that Ubuntu uses the credentials of the user who is logged in? or perhaps asks the user who is logged in to provide a user name and password?  I could not find that option in the printing configuration GUI anywhere.

---

### Post by hchristopher on 2008-07-31
Oh no... this thread is being sucked into the timeless void of the black hole of cyberspace!  Help us, Ubuntu Masters!  Aaaaaaahhhhhh.......

---

