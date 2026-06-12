---
title: "How to print to a network dual boot machine?"
date: 2005-08-28
forum: Networking &amp; Wireless
---

### Post by foxy123 on 2005-08-28
Printing in Linux is a headache for me. Networking in general is another headache. So network printing is an absolute nightmare for me.

The story is as follows. I've got a laptop which is purely Ubuntu and a dual boot PC, which has a printer. Both PCs are in a local wireless network.

Firstly I set up a SMB printing, following a HOWTO and it works fine for me, when the desktop was booted in Windows. However, I wanted to make it possible to print when the desktop is booted in Ubuntu as well. So i followed a HOWTO how to share CUPS printer and set up it. 

The problem now is that I cannot print to Windows. If the desktop is booted in Windows, it just does not work. 

If I try to run Gnome CUPS manager I've got an error:
```
~$ gnome-cups-manager

** (gnome-cups-manager:30430): WARNING **: failed request with status 1280
``` 

However if I got to localhost:631 I can see the printer which configured for SMB:

```
Description: Stylus-Photo-790
Location:
Printer State: processing, accepting jobs.
"No pages found!"
Device URI: smb://10.0.0.11/epson790
``` 

I can see a job but is is being processed forever...

I wonder how to configure the printer so I could print through the network whether the desktop is booted  in Windows or Linux?

---

### Post by foxy123 on 2005-09-04
the advice i was given at LinuxQuestions was as follows:
1. create two different queues in CUPS: one for Windows SMB printer and another for Linux CUPS printer
2. put them into one class
3. setup the class as a default printer

As a result when I print to default printer it prints to the queue which is available...

It looks like a neat solution, though I was not able to test it. 

My probblem is that since it is actually the same printer, it's called identically in CUPS amd SMB: Stylus-Photo-790. Therefore it is not possible to get both queues into one class. All my attempts to rename a printer failed. Neither CUPS web interface not gnome-cups-manager allow to do it. Following another advice I changed the name in /etc/cups/printers.conf, but was not able access neither printer after that.

Any ideas?

---

### Post by BlueNoteMKVI on 2005-10-24
I had the same problem.  My solution cost a bit of money, but saved me some headache in the long run.  I bought this:
[http://www.linksys.com/servlet/Satellite?childpagename=US%2FLayout&packedargs=c%3DL_Product_C2%26cid%3D1114037289494&pagename=Linksys%2FCommon%2FVisitorWrapper](http://www.linksys.com/servlet/Satellite?childpagename=US%2FLayout&packedargs=c%3DL_Product_C2%26cid%3D1114037289494&pagename=Linksys%2FCommon%2FVisitorWrapper)

Now I can share the printer over the network to any of the five computers in my house, some of which are dual-boot systems.  I think it cost me about $80.

---

### Post by foxy123 on 2005-10-24
[QUOTE=BlueNoteMKVI]I had the same problem.  My solution cost a bit of money, but saved me some headache in the long run.  I bought this:
[http://www.linksys.com/servlet/Satellite?childpagename=US%2FLayout&packedargs=c%3DL_Product_C2%26cid%3D1114037289494&pagename=Linksys%2FCommon%2FVisitorWrapper](http://www.linksys.com/servlet/Satellite?childpagename=US%2FLayout&packedargs=c%3DL_Product_C2%26cid%3D1114037289494&pagename=Linksys%2FCommon%2FVisitorWrapper)

Now I can share the printer over the network to any of the five computers in my house, some of which are dual-boot systems.  I think it cost me about $80.[/QUOTE]
it's a bit pricey solution for my 2 PCs home network. I called the printer differently in Linux and Windows and choose a printer depending on how desktop is booted. Anyway thanks for your advice.

---

