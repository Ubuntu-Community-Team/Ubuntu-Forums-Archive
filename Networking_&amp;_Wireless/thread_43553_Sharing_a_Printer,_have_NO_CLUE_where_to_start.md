---
title: "Sharing a Printer, have NO CLUE where to start"
date: 2005-06-22
forum: Networking &amp; Wireless
---

### Post by Kyral on 2005-06-22
Okay, I want to setup a printer sharing to the one lone printer in our house. We have currently 3 active computers (well, two, but dad brings his laptop home from work, so) and a wireless network through a Linksys router. I'm good with single machine things, and simple setting up of a LAN, but Printer Sharing I have no clue with. I also have my old laptop that I can "sacrifice" to turn into a server. 

Oh, my machine is running Ubuntu 5.04, the others are running XP Pro (I'm about to reformat my laptop into an Ubuntu machine)

Help please?

---

### Post by intangible on 2005-06-22
OK, here's some instructions:

If you have a network printer (that is the printer itself connects to the network) try this:
[http://ubuntuforums.org/showthread.php?t=41835](http://ubuntuforums.org/showthread.php?t=41835)

If you want to connect from Ubuntu to a Windows printer, try this:
[http://ubuntuforums.org/showthread.php?t=32190](http://ubuntuforums.org/showthread.php?t=32190)
Instead of the IP address, you can use the computer name if you have samba installed... You only want to use the IP if it is set static anyway.

If you want to setup Ubuntu to share the printer, first, make sure the printer is working under Ubuntu, then worry about the sharing part :D:
Installing printer under ubuntu: **System->Administration->Printing** then **New Printer**
Sharing the printer:
[https://wiki.ubuntu.com/NetworkPrintingFromWinXP](https://wiki.ubuntu.com/NetworkPrintingFromWinXP)
You don't have to modify the hosts file on the XP machine if samba is setup properly (can you ping the linux box by the hostname?).
More detailed instructions about accessing the printer from Windows:
[https://wiki.ubuntu.com/NetworkPrintingFromWin2000](https://wiki.ubuntu.com/NetworkPrintingFromWin2000)

Since you didn't describe your setup, I just gave you links to instructions.

If you give me more info about how you want to set it up, I will help walk you through it.  The only part that might give you problems is if the printer itself doesn't work in Ubuntu.

---

### Post by Kyral on 2005-06-22
Okay, its a Lexmark USB printer, I don't know if it works in Linux yet. My idea would be that I would connect it to the laptop which I am going to install Ubuntu on, most likely a barebones server install, then connect that laptop into the router with a standard Ethernet cable. Then somehow the other computers would send print requests to the computer via the wireless net and whatever would be printed out on the printer.

---

### Post by intangible on 2005-06-22
What model?

---

### Post by feld on 2005-06-22
[QUOTE=][/QUOTE]
 YOU DONT NEED SAMBA! SAMBA SUCKS! BAD BAD BAD! Especially for only sharing a PRINTER! Please NEVER tell people to use samba to share a printer!!!

_________________________________________

This assumes you can already print to the computer from the linux computer that it is 
connected to.

OK dude here's the easiest way to do it

1. edit /etc/cups/mime.types

at very bottom Uncomment the line

application/octet-stream

2. edit /etc/cups/

Uncomment the line

application/octet-stream

3. edit /etc/cups/cupsd.conf
Starting at line 790 you will see:

<Location />
Order Deny,Allow
Deny From All
Allow From 127.0.0.1
</Location>

Add to that another line saying
Allow From IP ADDRESS

If you want you can do something like
Allow From 192.168.1.* to allow all those computers/addresses

4. At line 862 you will see

Order Deny,Allow
Deny From All
Allow From 127.0.0.1
#Encryption Required

Add the IP Addresses in there too.

5. Go back up to line 445
You will see

Listen 127.0.0.1:631

That allows access to cups over the network but coming ONLY from 127.0.0.1
Add another line for the ip address or addresses like so

Listen 192.168.1.100:631

You can use the * again if you need to, or just specify the addresses individually.

Save the file now.

6. Now you need to 
sudo adduser cupsys shadow
sudo /etc/init.d/cupsys restart

7. Open up your web browser on the computer connected to the printer to:
[http://localhost:631](http://localhost:631)

and click on Classes at the top.

8. Add a class (if you are asked to login, use your user name and password on the computer)

9. name the class Home and click Continue

10. Choose the printer (should be the only one on the list) and click Continue

11. Ok done with linux -- go to the XP computers and add a printer

12. Click next, go to Network printer

13. Click the bottom dot to add a printer by its URL

14. Enter in [http://IP-OF-LINUX-COMPUTER:631/classes/Home](http://IP-OF-LINUX-COMPUTER:631/classes/Home)

15. Choose your printer driver and youre DONE



-Feld

PS Samba sucks

---

### Post by intangible on 2005-06-22
I would never tell someone to do printer sharing through samba, what is nice about samba though is that it will allow you to use computer names instead of IP addresses with CUPS.  That makes it simpler to explain to people than having them setup static ip addresses.

---

### Post by shanghaipi on 2005-06-23
On the 2nd step, you have "edit /etc/cups", but no file name.  What is edited?  And how do you find out your ip address for printing between a win Xp comp and a ubuntu comp?

---

### Post by intangible on 2005-06-23
To get your ip address on a Windows computer, goto "Start->Run" type "cmd" then in that box, type "ipconfig".

To get your ip on Ubuntu, goto "Applications->System Tools->Terminal" and type in "ifconfig".

The file you'll need to edit is /etc/cups/cupsd.conf

---

### Post by shanghaipi on 2005-06-23
So the 2nd and 3rd points have to do with changing the file: /etc/cups/cupsd.conf/

Just making sure I get it right before I change stuff.

Thank you for your help.

---

### Post by asimon623 on 2005-07-03
[QUOTE=shanghaipi]So the 2nd and 3rd points have to do with changing the file: /etc/cups/cupsd.conf/

Just making sure I get it right before I change stuff.

Thank you for your help.[/QUOTE]
 Ok, I just did all those steps....(CUPS)...and it didn't work

---

