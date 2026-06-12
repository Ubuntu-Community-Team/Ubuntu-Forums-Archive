---
title: "Network Printer Does Nothing"
date: 2007-06-07
forum: Networking &amp; Wireless
---

### Post by randal on 2007-06-07
I've setup a small home network with my desktop on XP and laptop on Feisty. I installed smb4k and so far things are ok on the file sharing. I've set the printer through kcontrol by selecting network printer (Windows) class. However the printer on my XP box did not print the test pages I'd send to its queue. Things I want to print only got added to its job queue but would never be printed. My printer would make noise as it prepares to print but would not print anything. One thing that puzzles me is that the number of pages detail is always N/A as I see it on the printer job queue on XP. Also from the 'ready' it'd go to 'no toner' status...

I really need to get this done ASAP. Thanks in advance.

---

### Post by randal on 2007-06-10
The forum doesn't seem to be very helpful these days... :-?

---

### Post by timzak on 2007-06-10
I wish I could help you, but I'm having a similar problem and not getting any replies to my post either.  :(  

I wish you luck.  Hopefully if someone helps one of us, the other can benefit too.

---

### Post by timzak on 2007-06-10
Don't know if this will help you at all, but I finally got the printing to work on my network.  And I'm sad to say it was a dumb mistake on my part.  Despite the Windows computer being set up to automatically log in (no password or username to input), I realized I still needed to type in "Administrator" for username instead of leaving it blank.  That's all I needed to do to get the printing to work.  I found it odd that I could still see the Windows computer and its printer without typing the username in.  But as long as it works!

Hope this helps you.  If not, then good luck to you.

---

### Post by randal on 2007-06-11
I didn't forget the username part... but I still got the same problem. I also find it odd that the document I'm trying to print registered on the guest's ownership even if I entered a different username... this is really frustrating me.

---

### Post by Dedoimedo on 2007-06-11
Hello,

I have written a tutorial about this, especially addressing this issue:

[http://ubuntuforums.org/showthread.php?t=465896](http://ubuntuforums.org/showthread.php?t=465896)

In particular:

[http://www.dedoimedo.com/computers/linux_commands.html](http://www.dedoimedo.com/computers/linux_commands.html)


Here's from my article:

... Printer sharing

Well now, folder and file sharing is really easy. What about the printers?

Again, it is very simple. If you have a printer installed on a Windows machine, accessing it from a Linux machine will be easy. The rougher side of the coin is accessing a printer installed on a Linux machine from a Windows machine.

First, you will have to allow your printer to be shared. Backup and then edit the Common UNIX Printer System configuration file.

cp /etc/cups/cupds.conf /etc/cups/cupsd.conf.bak
gedit /etc/cups/cupsd.conf

In the file, search for the entry #Listen 127.0.0.1:631 and add or change as follows:

#Listen 127.0.0.1:631 OR localhost:631
xxx.xxx.xxx.xxx:631 OR *:631
Listen /var/run/cups/cups.sock

CUPS listens on the port 631. If you use a static IP address for the Linux machine, you can specify only that IP. Otherwise, you might need to use a wildcard.

Of course, you should be aware that an open port means a wee less security than before, so keep that in mind.

After saving the changes, you will have to restart CUPS:

/etc/init.d/cupsys restart

Now that the printer is available, you will have to add it for the Windows machine.

Start > Settings > Printers and Faxes
File > Add Printer

... A network printer, or a printer attached to another computer ...
... Connect to a printer on the Internet or on a home or office network ...

[http://xxx.xxx.xxx.xxx:631/printers/printer_name](http://xxx.xxx.xxx.xxx:631/printers/printer_name)
OR
[http://netbios_name:631/printers/printer_name](http://netbios_name:631/printers/printer_name)

When prompted for the driver, either select from a list or install it from a disk (like CD). And that's it! You can now print from a Windows machine on a printer connected to a Linux machine ...

Hope this helps,
Dedoimedo

---

### Post by randal on 2007-06-11
That was helpful... but the thing is I'm in the situation where the printer is connected to windows... and it sure isn't easy.

---

### Post by timzak on 2007-06-11
randal, 

I'm sorry I can't help further, but I did want to emphasize that I did not have to customize the samba configuration file at all.  That holds true when sharing a WinXP printer as well as a Win2k printer.  Also, I don't have any software firewalls running, only the built-in firewall on my router.

If you haven't already, try accessing your router's setup from within Ubuntu.  I'm talking about the one you access from the web browser.  Ie, [http://192.168.xx.xx](http://192.168.xx.xx).  I don't know if this will do anything, but maybe it'll let your router know (from within Ubuntu) that you have a network.

---

### Post by randal on 2007-06-13
It's ok timzak.

I'm not sure what the problem is... my printer gets the job and prepares to do it but it never prints anything.. 

I'm guessing that the problem has something to do with the data that kubuntu sends to the printer's job queue but I'm not sure how to fix it...

---

### Post by alexmidd on 2007-07-29
I'm getting this same problem with an HP Deskjet 3420, a pretty standard printer that works over the network from a Windows machine no problem, but try it on Ubuntu and I get the same problems as the OP - the printer will click about a bit, a job wll go int the queue, but no action from there. Searched the internet, no drivers available (only Windows and MAc) and tried the drivers in the ubuntu file system, still no dice. This should be a no-brainer, but it is one of the (many) frustrations that are still making using Linux hard work. I love Linux, and want to commit myself to it, but there are these constant problems that take up loads of my time when I could be being productive. I'm sorry, but I just don't get the same in Windows. :(

---

