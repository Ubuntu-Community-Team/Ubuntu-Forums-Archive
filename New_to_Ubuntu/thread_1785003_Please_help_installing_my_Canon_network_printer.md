---
title: "Please help installing my Canon network printer"
date: 2011-06-17
forum: New to Ubuntu
---

### Post by bennypr0fane on 2011-06-17
Hello,
I'm very new to Linux,
and I'd like to install my network printer on my machine recently equipped with Ubuntu 10.04 (amd64).
The printer is Canon Pixma MX 350 and is connected to the router via WLAN, my pc is connected with a cable. This setup already works for me under Windows XP.
I tried to make Ubuntu detect the printer on the network automatically, but no joy. It seems I'm supposed to tell U. where my printer's at, but it wouldn't take "in the hall" for an answer :p
The printer didn't come with software for Linux, so I downloaded some mysterious tarball from Canon, which seemed to contain only i386-packages, and these refused to install. 
So how would you helpful people here suggest I proceed?
Thanks, Ben

P.S. Is it that generally I have to find 64-bit versions for anything I want to install, or is there a way to run i386 applications as well?

---

### Post by pqwoerituytrueiwoq on 2011-06-17
did you search for the printer using its ip address?
you can force the packages to install but that should not be first choice
edit:
for the scanner
sudo apt-get install sane-pixma
[http://manpages.ubuntu.com/manpages/natty/man5/sane-pixma.5.html](http://manpages.ubuntu.com/manpages/natty/man5/sane-pixma.5.html)
scanner should work out of the box on natty
you probably need a driver ppa
edit: ([source]("http://edigitales.org/how-to-easily-install-canon-printer-driver-in-ubuntu/"))
sudo apt-add-ppa repository: michael-gruz/canon
 sudo apt-get update

---

### Post by bennypr0fane on 2011-06-17
> **pqwoerituytrueiwoq said:**
> did you search for the printer using its ip address?
I don't know how to find out its IP address :-(

you can force the packages to install but that should not be first choice
edit:
for the scanner
> **pqwoerituytrueiwoq said:**
> sudo apt-get install sane-pixma
[http://manpages.ubuntu.com/manpages/natty/man5/sane-pixma.5.html](http://manpages.ubuntu.com/manpages/natty/man5/sane-pixma.5.html)

it says packages sane-pixma not found...

> **pqwoerituytrueiwoq said:**
> you probably need a driver ppa
edit: ([source]("http://edigitales.org/how-to-easily-install-canon-printer-driver-in-ubuntu/"))
sudo apt-add-ppa repository: michael-gruz/canon
 sudo apt-get update

it says "apt-add-ppa command not found"

:(

---

### Post by pqwoerituytrueiwoq on 2011-06-17
> **bennypr0fane said:**
> I don't know how to find out its IP address :-(

you can force the packages to install but that should not be first choice
edit:
for the scanner


it says packages sane-pixma not found...



it says "apt-add-ppa command not found"

:(
sudo add-apt-repository ppa:michael-gruz/canon
looks like the site i copy/pasted from does not know there commands very well
i fixed their typos in the command

---

### Post by jtarin on 2011-06-17
[Here's a thread ]("http://ubuntuforums.org/showthread.php?t=1314209&highlight=Canon+Pixma+MX+350")on the 250...a little dated but still relevant to this series of Canon. Read through thoroughly and follow links. Come back with questions.

---

### Post by bennypr0fane on 2011-06-19
> **pqwoerituytrueiwoq said:**
> sudo add-apt-repository ppa:michael-gruz/canon
looks like the site i copy/pasted from does not know there commands very well
i fixed their typos in the command

so i did that, here's what happened:

"Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv 84E550CD36EC35430A66AC5A03396E1C3F7B4A1D
gpg: Schlüssel 3F7B4A1D von hkp Server keyserver.ubuntu.com anfordern
gpg: Schlüssel 3F7B4A1D: "Launchpad Misakovi" nicht geändert
gpg: Anzahl insgesamt bearbeiteter Schlüssel: 1
gpg:              unverändert: 1"

What now?

---

### Post by bennypr0fane on 2011-06-19
> **jtarin said:**
> [Here's a thread ]("http://ubuntuforums.org/showthread.php?t=1314209&highlight=Canon+Pixma+MX+350")on the 250...a little dated but still relevant to this series of Canon. Read through thoroughly and follow links. Come back with questions.

Thank you, looks like this is what I was looking for (a little hint that the link I needed was on the *last* page of that thread would have been nice).
I installed the drivers from australia, now I just need to make Ubuntu FIND that darn printer...
How can I find out its IP-address, or whatever else is supposed to go in the "Host"-field?
Thanks, Ben

---

### Post by jtarin on 2011-06-19
> **bennypr0fane said:**
> Thank you, looks like this is what I was looking for (a little hint that the link I needed was on the *last* page of that thread would have been nice).
I installed the drivers from australia, now I just need to make Ubuntu FIND that darn printer...
How can I find out its IP-address, or whatever else is supposed to go in the "Host"-field?
Thanks, BenUse the CUPS interface to setup your printer.....I find it easier and have more control over print jobs.
I usually bookmark my browser to get it to come up. In the browser enter the address ```
http://localhost:631/
```
[Ubuntu Tutorial]("http://ubuntu-tutorials.com/2009/03/19/configuring-printers-via-the-cups-web-interface/")
[http://www.cups.org/doc-1.1/sam.html](http://www.cups.org/doc-1.1/sam.html)

---

### Post by jtarin on 2011-06-19
> **bennypr0fane said:**
> Thank you, looks like this is what I was looking for (**a little hint that the link I needed was on the *last* page of that thread would have been nice**).
I was going to ask them to move it to the top of the first page but didn't have time. So sorry!:P

---

### Post by bennypr0fane on 2011-06-20
> **jtarin said:**
> Use the CUPS interface to setup your printer.....I find it easier and have more control over print jobs.
I usually bookmark my browser to get it to come up. In the browser enter the address ```
http://localhost:631/
```[Ubuntu Tutorial]("http://ubuntu-tutorials.com/2009/03/19/configuring-printers-via-the-cups-web-interface/")
[http://www.cups.org/doc-1.1/sam.html](http://www.cups.org/doc-1.1/sam.html)

thank you so much, I did it! ubuntu can now see my printer.
now there remains the task of getting scanning function to work over the network. i installed the australian scanner drivers, but there's no new scan application showing up in my apps menu.
i tried Simple Scan, but it says no scanner found.
1. is there supposed to be a dedicated scanning software coming along with the driver from Canon, or is it just the bare driver, and I am to use any application of my choice e.g. simple scan?
2. how do i make ubuntu realize my canon is also a scanner?

---

### Post by jtarin on 2011-06-20
Glad you got it working.....now for that scanner. Try simply unplugging the printer/scanner, then reboot. When you have returned to the desktop and everything is idle.....plug the printer/scanner back in. Now see if simple scan detected it.

---

### Post by bennypr0fane on 2011-06-21
> **jtarin said:**
> Glad you got it working.....now for that scanner. Try simply unplugging the printer/scanner, then reboot. When you have returned to the desktop and everything is idle.....plug the printer/scanner back in. Now see if simple scan detected it.

Nope, didn't work. The printer/scanner was never plugged into anything but the power socket though - like I said, it's connected to the network via WLAN. What I did is pull the power plug, reboot, plug it back in, switch on the Canon - no luck :(

---

### Post by jtarin on 2011-06-21
[I found this.]("http://software.canon-europe.com/software/0038682.asp?model=")...it was recommended by a developer for Sane on their BB.

[And this also]("http://ubuntuforums.org/showthread.php?t=1475336") which is a little more complicated process.

---

### Post by bennypr0fane on 2011-06-26
> **jtarin said:**
> [I found this.]("http://software.canon-europe.com/software/0038682.asp?model=")...it was recommended by a developer for Sane on their BB.

I think this is exactly what I got from the download section of Canon's support page in the first place, 32-bit drivers only.

> **jtarin said:**
> [And this also]("http://ubuntuforums.org/showthread.php?t=1475336") which is a little more complicated process.

As far as I can tell, that would only help me force the install of the 32-bit software? But with zero coding skills, it's sort of intimidating -

And besides, I already have 64-bit drivers and print/scan apps installed now from [here]("http://support-au.canon.com.au/contents/AU/EN/0100236101.html"), so I was hoping I would NOT have to go through a similar procedure.

Do you think using the 32-bit-stuff instead will help the scanning software (btw, turns out there IS on from Canon coming with the drivers after all, called ScanGearMP) see the device on the network?

---

### Post by jtarin on 2011-06-26
[The latest I could find.]("https://launchpad.net/~michael-gruz/+archive/canon/+build/2562068")They are for Oneiric release, but I don't see why they wouldn't work on yours. You can download and right-click using DEBI installer. If they don't work you can uninstall them.

---

### Post by bennypr0fane on 2011-06-26
> **jtarin said:**
> [The latest I could find.]("https://launchpad.net/~michael-gruz/+archive/canon/+build/2562068")They are for Oneiric release, but I don't see why they wouldn't work on yours. You can download and right-click using DEBI installer. If they don't work you can uninstall them.

HEUREKA!
Scangear found the Scanner (Simple Scan did not)!
Initiating a scan from the PC works nicely now - which is a bit weird, because:
Since it's a network device, when initiating a scan from there, you have to tell it which pc to send the results to. Here I have the same problem the other way round: On the scanner, my PC doesn't show up in the list of available computers, so I left the setting on a different computer in the network. Then I initiated the scan from PC and voilà, I still got all the pictures sent to me.
So the only thing remaining to be fixed now is to make my scanner see Ubuntu on the network!

---

### Post by jtarin on 2011-06-26
[Insure your network server for printing is setup correctly.]("https://help.ubuntu.com/community/NetworkPrintingWithUbuntu")....I'm guessing.

---

### Post by bennypr0fane on 2011-06-27
> **jtarin said:**
> [Insure your network server for printing is setup correctly.]("https://help.ubuntu.com/community/NetworkPrintingWithUbuntu")....I'm guessing.

I'm not sure if these instructions are for my network setup.
It talks about the print server being an Ubuntu computer, whereas my printer/scanner is not connected to any pc directly, meaning the thing between my PC and the Canon is not another PC.
The Canon is network aware itself and it's connected to the modem/router via Wifi, so I guess that means it has its own printserver built in or sth.?
The communication between the Canon and all the PCs in the house should go like this:

PC <-(cable)-> modem/router <-(WiFi)-> Canon

Anyway, if I wanted to configure the printserver, I'm guessing I'd need to directly access either the router's or the Canon's finmware?

---

### Post by jtarin on 2011-06-27
Maybe I'm not understanding you correctly. How many computers and what type of OS do they have? Are you having specific problems scanning from one of these? Which one?

---

### Post by bennypr0fane on 2011-06-28
There are 4 computers in the network: one with Win Vista, two with Win7 and mine is running Ubuntu/WinXP dual boot. The printer is in the hallway with the router, the PCs are in different rooms.
All the Windows PCs have no issues communicating with the Canon via the router, be it printing or scanning. That includes my own PC if I boot WinXP instead of Ubuntu.
- Now, printing works fine under Ubuntu as well (only sending command from Pc to printer).
- Scans can be initiated from each of the computers using the software provided by Canon (called ScangearMP). **This** you helped me get to work now under Ubuntu, too.
- **But** scanning can **also** be initiated **from the Canon itself ** - it has an interface and controls for setting scanning options, file type and which PC to send the files to. That automatically opens the scanning software on the destination PC for editing and saving the scanned files. I think there is a dedicated network scan-utility used for this. **This** is the part not working yet under Ubuntu.

So, issuing scanning commands *from Ubuntu * already works, but if I want to send a scanned document from the Canon *to Ubuntu*, without having initiated it from the Pc first, that is not possible, because the Canon is now not able to see my Ubuntu machine on the network and send files to it. It can only see the Windows Pcs.

---

### Post by jtarin on 2011-06-28
> **bennypr0fane said:**
> 
- **But** scanning can **also** be initiated **from the Canon itself ** - it has an interface and controls for setting scanning options, file type and which PC to send the files to. That automatically opens the scanning software on the destination PC for editing and saving the scanned files. I think there is a dedicated network scan-utility used for this. **This** is the part not working yet under Ubuntu.

So, issuing scanning commands *from Ubuntu * already works, but if I want to send a scanned document from the Canon *to Ubuntu*, without having initiated it from the Pc first, that is not possible, because the Canon is now not able to see my Ubuntu machine on the network and send files to it. It can only see the Windows Pcs.Is it possible it could be closed port on Ubuntu?

---

### Post by jtarin on 2011-06-28
Example Setup:

Installing Cannon Network ScanGear for _**scanning from the Photocopier**_

    The copier is configured to pull it's IP address etc. from the Institute's DHCP server.
    As of 7th November 2005, the copier is statically allocated the IP address 163.1.148.102 using the 
MAC address 00:00:85:0a:58:b4.
    IMPORTANT NOTE: The TWAIN driver will not work if the client is on a different subnet than that of the copier.
e.g. A machine on the 163.1.148.0/23 network with a asymmetric route to an RFC1918 network, although 
able to ping the copier, the drivers will fall over. Ensure they are both on the 163.1.148.0/23 network.
    Install the software from either CD or download the self extracting zip file. The TWAIN drivers will be installed
along with the ScanGear tool for selecting which copier to use.
    Ensure the photocopier is in network scan mode and it's network plugged in.
    Fire up the Network ScanGear tool and "Discover" the copier. Select the copier from the list and click Exit.
    You should now be ready to start up your favourite software and use the TWAIN interface to scan documents in using the copier.
    Save scanned UCAS forms to \\admindb0\socrates

---

