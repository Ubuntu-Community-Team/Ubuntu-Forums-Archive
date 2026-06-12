---
title: "Correctly configuring the Linksys WPS54GU2"
date: 2006-11-06
forum: Networking &amp; Wireless
---

### Post by wireless-gee on 2006-11-06
I recently purchased the Linksys WPS54GU2 for the bargain basement price of £19.99 from my local Staples.

I've read a couple of posts in this forum where people were having problems with the Linksys WPS54GU2: endless printing of pages and print queues not automatically being cleared. These problems are caused by CUPS failing to ascertain the current status of the printer via the Linksys WPS54GU2. The printer status function of the Linksys WPS54GU2 is a privileged operation, which requires a user and a password: try accessing the WPS54GU2 via [http://xxx.xxx.xxx.xxx/ipp](http://xxx.xxx.xxx.xxx/ipp)

The correct URI (in the printer configuration dialogue) for the WPS54GU2 is of the form:

[http://user:password@xxx.xxx.xxx.xxx/ipp/L1](http://user:password@xxx.xxx.xxx.xxx/ipp/L1)

user:password is your user and password for the WPS54GU2

xxx.xxx.xxx.xxx is the address of WPS54GU2

L1 is the parallel port, L2 is the USB port.

NB. The user and the password will not subsequently be shown in the printer dialogue.

Contrary to popular perception, the Linksys WPS54GU2 is an excellent - but poorly documented - piece of kit.

---

### Post by brundles on 2006-11-08
I can't believe how simple that was to install!

Other websites and documentation make it sound like black magic ([or at least a nightmare](http://linksys.custhelp.com/cgi-bin/linksys.cfg/php/enduser/std_adp.php?p_faqid=120&p_created=1084204013&p_sid=PN6orMli&p_accessibility=0&p_lva=&p_sp=cF9zcmNoPTEmcF9zb3J0X2J5PSZwX2dyaWRzb3J0PSZwX3Jvd19jbnQ9MSZwX3Byb2RzPSZwX2NhdHM9JnBfcHY9JnBfY3Y9JnBfc2VhcmNoX3R5cGU9YW5zd2Vycy5hX2lkJnBfc2NmX2xhbmc9MSZwX3BhZ2U9MSZwX3NlYXJjaF90ZXh0PTEyMA**&p_li=&p_topview=1) to connect one of these things to Linux so it kept slipping down the list of things to do.

Something about your post just made me think perhaps it was easier than I had been led to believe just using CUPs - and it was! That was easier to install and use than under Windows (admittedly that is HPs fault rather than Microsofts for my printer though).

As you say, it's an excellent piece of kit but just (like most of the stuff Linksys do) very poorly documented.

---

### Post by Komissar on 2006-11-13
> **brundles said:**
> I can't believe how simple that was to install!

You are so right. However I had difficulty getting cups to work properly, but I got "UNIX Printer (LPD)" up in 4.5 mins. on two(2) Ubuntu Dapper installs. I couldn't believe how fast the printers could spit out the pages. I connected one on the paralell port, HP 6L Laserjet, and one on the usb port, HP PSC 1610.
All I did was choose:
Network Printer "UNIX Printer (LPD)"
Host: 192.168.1.100    <Non Static IP to WPS54GU2
Queue: L1     <That's the parallel port, L2 for the USB

Now I have some questions....:confused:

1. Is there a way to network the HP PSC 1610 to capture the scans?
2. Is there a way to access the storage devices when I insert an SD card into the front of the HP PSC 1610?

I have one desktop right beside the printer and I would need to use the  scanning ability of the printer. Any help would be greatly appreciated. It's beyond my level of expertise... :-?

Also, I found out that linksys has hard coded a "universal password" in the printserver, If are having problems getting into the admin pages use it instead of "admin",  " [+_*] " <everything between the quotes, no spaces.

---

### Post by brundles on 2006-11-13
> **Komissar said:**
> 1. Is there a way to network the HP PSC 1610 to capture the scans?
2. Is there a way to access the storage devices when I insert an SD card into the front of the HP PSC 1610?

I don't have one of these but I'm afraid the most likely answer for both of these is no. I've not yet found a home scanner or all-in-one printer that you can share the scanner on when it's hooked into the desktop machine (Windows or Linux). And given that the Linksys print servers don't support 2 way communication on the USB connection for thing like ink levels you've got no chance with the scanning side of things. Sorry :(

If you want to share the SD card reader you're probably better off getting a USB SD card reader and sharing that from the PC.

---

### Post by Komissar on 2006-11-13
I have been suspecting the same thing. I thought because the Linksys os on the router was a linux variant it would have a "hidden" option. Thanks for the info.

---

### Post by JackD on 2007-08-05
I found that the CUPS configuration seemed to work best with the following syntax:

[LIST]
[*][http://192.168.1.4:631/L1](http://192.168.1.4:631/L1)
[/LIST]

The key is that (1) I used "http" with the ":631" port rather than "ipp", (2) I do not include "printers" and L1/L2 works as described above.

I'm very happy with the Linksys and would recommend it.

---

### Post by Michael Matthews on 2007-12-11
thanks for the tip on the [http://user:password](http://user:password). Using ipp://  lp job would never finish unless I manually cancelled it. Device had to be power cycled often which is annoying. Maybe that problem will go away now.
As far as queue name, L1,2,3 P1,2,3, it is configurable from device web interface(Logical Port). I used P2 for IPP because that is what (totally inadequate) doc said as I remember. L1,2 was recommended for LDP. If you use http it may not matter.
Device should support LDP also which is not documented by linksys, but is on the web somewhere for VISTA config. I have not tried it for Ubuntu.

---

### Post by psoup1965 on 2008-04-13
All the instructions here cannot help you if you do not know what port you are running on...

The only way that I was able to connect my HP Laserjet 1320 through the WPS54GU2 (USB Port) was to do the following:

Install and run nmap  (apt-get install nmap) and run the command:

nmap -sV 192.168.1.3 (My static IP of my print server). If you do not know your IP then hold the reset button on the print server for about 10 seconds and then release. The config will print on your printer with the IP address.

Look for something that says ipp or as mine did:

9100/tcp open  jetdirect?
9101/tcp open  jetdirect?

In CUPS choose 
Network Printer: TCP/Socket, HP JetDirect, Raw connection

Host: 192.168.1.3 (your print server IP)
Port: 9101 (either worked for me but I only have 1 printer installed.

Print Test page.

Hope this helps and saves you some time.

(P.S. I did not have to put in anything other than what I showed above... no username and password etc...). I was not able to get it to work any other way... it may be worth trying to use ipp, but this is much easier.  After finding the correct port, the whole process takes about 1 minute until you are reading your test page.

---

