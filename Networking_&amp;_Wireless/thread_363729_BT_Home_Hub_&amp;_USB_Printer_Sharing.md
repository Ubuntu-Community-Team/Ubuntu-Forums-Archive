---
title: "BT Home Hub &amp; USB Printer Sharing"
date: 2007-02-17
forum: Networking &amp; Wireless
---

### Post by ahaslam on 2007-02-17
Hi, I know nothing about networking but would really like to share my printer. I will be giving this laptop to a family member when I build a desktop next week, it would be great if we could both print to the same printer. I would be connected to the Hub via an Ethernet cable & the laptop would be using wireless.

I've a BT Home Hub that has a spare USB port, where I'd like to connect my HP845c Deskjet. I've seen a Windows guide here: [http://www.wallaceit.co.uk/wit/article.aspx?id=80](http://www.wallaceit.co.uk/wit/article.aspx?id=80) and a similar forum question to mine here: [http://hubbub.labs.bt.com/?pagename=viewpost&id=1246](http://hubbub.labs.bt.com/?pagename=viewpost&id=1246)

My problem is that I have absolutely no network experience & no idea how to do that in Linux. A Linux translation for n00bs would be fantastic & any suggestions would be greatly appreciated

Thanks in advance,

Tony.

---

### Post by Tilex on 2007-02-17
Well, if your printer _can_ be connected to a network, then it should be a piece of cake.  Once the printer is connected to the hub, it should be given an IP address, say 192.168.0.100.

Then, when you add the printer on your computer, you specify that it's a network printer and the wizard will scan the network in order to find it.  If it doesn't, well then maybe you should manually specify the IP adress of the printer (192.168.0.100), the default gateway (in that case 192.168.0.1) and the network submask (probably 255.255.255.0).

Hope that'll work...

---

### Post by Tilex on 2007-02-17
Oh, I should have read the Microsoft how-to first.  Then, the IP address is 192.168.0.253.

---

### Post by ahaslam on 2007-02-17
Thanks for your quick reply.
I'd tried selecting 'Network Printer' & 'CUPS Printer (IPP)' & entered '192.168.[COLOR="Red"]1[/COLOR].253' as the URI to no avail. Is that what you meant, or am Imissing something - I'm a complete n00b at this.

Thanks again,

Tony.

---

### Post by moffatt666 on 2007-06-17
*BUMP*
I'm having the same problem, can anyone help please?

---

### Post by Fitzcarraldo on 2007-07-05
You might like to install the Samba share browser smb4k to see if you can see the IP address of the BT HomeHub's Samba Server. Install smb4k by typing the following into a Terminal window:

```
sudo apt-get install smb4k
```

When installation has completed, an icon should appear under Applications > Accessories. You can lauch smb4k using that or via the command line in a Terminal window:

```
smb4k
```

----------

I'm running Ubuntu 6.06 on a laptop with a CardBus wireless card networked to a BT HomeHub. I have plugged an HP PSC-2110 multifunction printer into the USB-A port of the BT HomeHub and managed to print to the printer, but it is unreliable: I have to unplug and plug in again the USB cable after each print job otherwise subsequent jobs do not print, so this is not a practical solution. Anyway, this is how I configured Ubuntu 6.06 to print to the printer via the BT HomeHub:

1. System > Administration > Printing

2. Double-click on 'New Printer'

3. Select 'Network Printer' and 'Unix Printer (LPD)'

4. In the 'Host' field enter the IP address of the BT HomeHub Samba Server, which is, by default on my BT HomeHub, 192.168.1.253

5. In the 'Queue' field enter "LPT1" (without the quotes)

6. Click 'Forward'

7. Select the printer Manufacturer and Model (HP and PSC 2110 in my case)

8. In my case the recommended Driver was "hpijs (recommended) - HPLIP 0.9.7 (Suggested)".

9. Click on 'Forward'

10. Enter whatever you want in the 'Name' field (no spaces allowed). I decided to call my printer "PSC-2110-BT-HomeHub" (without the quotes). Enter whatever you want in the 'Description' and 'Location' fields.

11. Click on 'Apply'

12. An icon for the printer should now be visible in the 'Printers' window. Right-click on this and select 'Properties'. Click on 'Print a Test Page' and the printer should print a test page.

Warning: You may find that you can only print the test page, and any other subsequent job you send to the printer does not print. The only solution I have found for this so far is to cancel the print job in Printers and on the printer itself, unplug the USB lead then plug it in again, and then resend the job, which is unsatisfactory. Maybe you'll have more luck.

---

### Post by doncristobal on 2007-07-08
With the help of Fitzcarraldo's last post, i managed to solve the problem with my Siemens Gigaset SX541 WLAN dsl and my HP LaserJet 1200. Here is how i did it: [http://ubuntuforums.org/showthread.php?t=369972](http://ubuntuforums.org/showthread.php?t=369972)

I hope this can help other people.

---

