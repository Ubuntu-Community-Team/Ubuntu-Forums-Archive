---
title: "[SOLVED] connecting to a windows network"
date: 2008-04-14
forum: Networking &amp; Wireless
---

### Post by chicoharv on 2008-04-14
My ubuntu PC shows me a windows home network but when I click on it I get nothing. I have a cheat sheet that says I should see  the name of my windows network. I can access the internet through my gateway ok and it sees my IP address. I want to access my windows network for file sharing and especially to use the printer which is on my office machine running XP.Also when I got to printers in administration I do not see any place for a network printer only local. I am trying to set it up per a help inquiry on the web. The URL is: [http://www.europe.eclipse.co.uk/Ubuntu/Ubuntu-on-win-network.htm](http://www.europe.eclipse.co.uk/Ubuntu/Ubuntu-on-win-network.htm)

---

### Post by Iowan on 2008-04-14
Check [this]("http://ubuntuforums.org/showthread.php?t=202605") one, too.
Under System>Administration>Printing is a **New Printer** option that has a **Select Connection** section that includes a **Windows Printer via SAMBA** "Device".
Also, under Basic Server Settings is a checkbox to "Show printers shared by other systems".

---

### Post by chicoharv on 2008-04-14
Samba is installed. As I understand it this is my problem.
I go to places and click on networks
I get a image that shows windows network ok.      then when I click on the image I am supposed to brimg up the name. of the network What I get is a blank window and I can't follow the instructions from that point I have a 2W gateway and it shows my IP address for my ubuntu/XP SP1 PC but I can not get this PC to join the network (MSHOME). I have Norton protection on my windows network and this IP address is in the trusted zone.I have a feeling thatI have a problem with Norton protection on the windows network. I know Norton ignores linux and it should just pass through as long as I have the IP in the trusted zone  I may have to wait a few days and get Hardy Heron to fix this mess. Everything used to work until AT&T changed protection from  CA to Norton  and my windows PC crashed in the office with the printer.

URL:   [http://www.europe.eclipse.co.uk/Ubuntu/Ubuntu-on-win-network.htm](http://www.europe.eclipse.co.uk/Ubuntu/Ubuntu-on-win-network.htm)

---

### Post by Iowan on 2008-04-15
Can you **ping** the Windows machines from Ubuntu?

---

### Post by chicoharv on 2008-04-15
no I can ping the gateway and Ubuntu.com

---

### Post by Iowan on 2008-04-16
Hmmm, if it can't ping - it probably can't connect.  Are you **ping**ing Windows boxes by hostname or IP address? If by hostname, try by IP address.

---

### Post by Bosk22 on 2008-04-16
Check to see if your Windows PC is running a firewall - If it is you will need to open ports on it before you can connect and share its files!!!!

---

### Post by chicoharv on 2008-04-16
> **chicoharv said:**
> no I can ping the gateway and Ubuntu.com

Well I got everything working.Thanks for all the help and info. Still not quite sure how I fixed everything but I think most of the trouble was with the windows Office PC. then I had to mess with Samba and smb mostly as per the originalfile I got at [http://www.europe.eclipse.co.uk/Ubun...in-network.htm](http://www.europe.eclipse.co.uk/Ubun...in-network.htm)
Let's close this puppy and again thanks for the help.

---

### Post by Iowan on 2008-04-16
Glad it's working.  If you're convinced the problem is fixed, mark the thread as SOLVED (Thread Tools). :)

---

