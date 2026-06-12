---
title: "Configuring a Network Printer"
date: 2014-10-03
forum: Networking &amp; Wireless
---

### Post by Cbhihe on 2014-10-03
I want to print over a simple W/LAN at home where I have a box with Trusty 14.04 Desktop on it and an old _HP LaserJet 4 Plus_ printer. The 3rd element is a simple DHCP router that gave the printer its LAN IP: 192.168.1.222.
[SIZE=1]*Note: The printer functions correctly under Windows XP (in the direct USB connection configuration) with original HP drivers.*[/SIZE]

After days of trying/reading everything I thought could be relevant, I need help for the network printer install.

Kernel: 3.13.0-36-generic #63 x86_64
Hostname: Schub

I installed along with all additional/optional packages both *Cups 1.7.2-0ubuntu1.2* from the GUI and [downloaded]("http://hplipopensource.com/hplip-web/gethplip.html") *HPLIP v3.14.3* from the Terminal before I [installed]("http://hplipopensource.com/hplip-web/install/install/index.html") it. I then updated HPLIP to v3.14.6 from the Canonical repo. 
I subsequently run:
```
> sudo apt-get update; sudo apt-get dist-upgrade; sudo apt-get upgrade
> sudo apt-get clean; sudo apt-get autoremove
```
All installs went well (0 error, 0 warning) and I removed over 150MB of dependencies rendered useless.

I tried the network printer installation in two ways.[B]

Install #1[/B]:
System Settings>Printers>Add printer>Network Printer>AppSocket/HP JetDirect > 
            [SIZE=1]*I chose AppSocket/HPJetDirect, because the Linux printer driver page by HP recommends it for that class of printers.*[/SIZE]
The install utility program then asks for a "Host" and informs that the "Port number" is 9100.
In the terminal, I checked: ```
> more /etc/hosts
127.0.0.1    localhost
127.0.1.1    Schub
```
and provided "Schub" as host and, not knowing any better, chose the generic driver recommended for PCL5:[I]
Generic PCL 5 Printer - CUPS+Gutemprint v5.2.10 pre2 [en] (recommended)[/I]

-- I could not print a test page correctly, all I got was several pages with just a couple of line of gibberish on them (driver problem ?). I had to kill the test page job, because it kept repeating itself always with gibberish. 

I went to [HTML]http://localhost:631/printers[/HTML] in my browser to try to tweak the install... I selected the printer and, in the drop down admin menu, chose "Modify printer". 
That got me to [HTML]http://localhost:631/admin[/HTML] where the shown "Current connection" was:
*socket://Schub:9100*. I changed that to  *AppSocket/HPJetDirect* and went on to [read]("http://localhost:631/help/network.html") about choosing the rigth URl for the network printer.
> The DHCP protocol is the usual way of setting the IP address of a printer on a managed network. Using the standard [FONT=courier new]dhcpd(8)[/FONT] program supplied with UNIX you simply need to add a line to the [FONT=courier new]/etc/dhcpd.conf[/FONT] file:
[FONT=courier new]host _*hostname*_ 
{ 
  hardware ethernet _*mac-address*_;   
fixed-address _*ip-address*_; 
} [/FONT]
Make sure that the hostname you use is also listed in the */etc/hosts* file or is registered with your DNS server.

I suppose that _*hostname*_ will be "Schub" and the _*IP-address*_ the printer IP actually visible in my DHCP router, 192.168.1.222, but where do I find the _*MAC address*_ ? It is not written on the back of the ethernet module providing the printer with connectivity and since I cannot get it to print a test page... ??

**Q:** Is this the right way of going about this or am I confused beyond redemption ? 
Perhaps I got it wrong from the beginning. Pointers would be welcome.

**Install #2**: (I tried the HP Device Manager way too.)
```
> sudo hp-setup  # the device discovery window opens.
```
I chose: *Network/Ethernet/Wireless network (direct connection or JetDirect)*
along with "Manual discovery" and I entered the IP 192.168.1.222 with JetDirect Port as 1

Clicking the "next" button, "*Created directory: /var/lib/snmp/mib_indexes*" appears in the terminal, and the small window changes to blank with a message saying "*No device found on bus: net*".
If I connect the printer to a usb port of the Ubuntu box, and look for printer under the "Universal Serial Bus (USB) category, the result is identical with "net" replaced by "usb".

**Q:** Again, what is wrong with my way of doing this  ?  

Help.

---

### Post by chili555 on 2014-10-03
What is wrong is, I assume, that it doesn't work. Here is a tutorial I wrote that explains the process I use on my system involving four Ubuntu computers and a printer attached to my router.  [http://ubuntuforums.org/showthread.php?t=2238997&p=13095533#post13095533](http://ubuntuforums.org/showthread.php?t=2238997&p=13095533#post13095533)

I suggest you try this method and post back if you have problems.

---

### Post by buzzingrobot on 2014-10-03
I have banged my head against HP printers several times.

Is the driver correctly installed?  I've found that if it is not, no amount of fiddling with CUPS or Ubuntu's printer config tool will be of any use.

The fact that the printer doesn't work when attaached via USB might be an indication that it can't find the driver.

When I've been successful, it's been by using HP's GUI version of hplip:  hplip-gui (it's in the repos). This does essentially the same things as the hplip script, but it is easier to use. There's a "Manual" option to enter the printer's IP. When you click through, the printer (cross fingers) will be listed.  Then the little app goes on to download and install the driver, setup the printer, and let you print a test page.  (Sometimes I need to power cycle my printer before it's recognized.)

Good luck.

---

### Post by ajgreeny on 2014-10-03
Here's how I have done it for a printer connected to my machine by USB but also enabling printing from my wife's machine.
SHARED PRINTING

HOST SERVER COMPUTER WITH PRINTER ATTACHED
1    On the server machine (the one the printer is attached to),
    open System -> Administration -> Printing
2    Select Server in the menu bar, and then Settings.
3    Check the second box:    Publish shared printers connected to this server 
4    Right click the printer and check the Shared option, if not checked yet 
5    Go to Properties and "allow printing for everyone"

CLIENT MACHINE TO PRINT FROM
6    Now configure the client (the Ubuntu computer from where you want to print):
7    Open System -> Administration -> Printing
8    Add - Network printer
9    Click Find network printer and specify the host computer IP address, eg. 192.168.0.11.
10    Click Find

---

### Post by Cbhihe on 2014-10-06
@chili555: Thanks a lot for the pointer. 
I finally determined that something must have happened to my printer network card between the moment I pulled the printer from its former Win environment and when I tried to insert it in Lx environment. [SIZE=1]Several weeks passed in between and although electronics does not flare up just so, especially when left powered off, I finally am sure that I can't ping the printer although it is seen by the router.
```
>sudo nmap -sP 192.168.1.*
```
also failed to reveal its MAC address.
So either the network card is fried or I am doing something very stupid, or both.
[/SIZE]So I decided to first connect that HP LaserJet 4 plus directly by USB 2.0 and to temporarily share it with others through my machine. I will later install Samba on my machine so Windows clients can also print. Hardly the optimal solution I sought, but workable.

1) I entered the service menu on the printer itself and did a cold reset.
 2) I set the Serial config to XON/XOFF as required for Ux/Lx environments, 
3) I also set ROBUST XON to "yes" (default). 
-> The test page produced a "W2 invalid Personality" error. 
So I went to the PCL menu and also to the Job menu on the printer and could not find automatic detection of language (choices of personalities are normally Auto/PCL/PS). A few hours of reading the official *[HP service manual]("https://archive.org/details/printermanual-hp-laserjet-4---5-service-manual")* and countless posts accross the net, I finally gave up on the basis that certain firmware versions may have "displaced" those configuration options. (Don't really know what it means concretely and I am not sure I want to know.) My firmware date is 1993.12.01. (*Don't laugh ! It's true. ;)*)

@buzzingrobot
Then I started heeding buzzzingrobot's reply on drivers. 
I found that the _*HP Service Manual*_ (referenced above - section 3. page 41 for my printer) and also one isolated post on the net, both suggest either NOT to use the Laserjet 4 Plus printer driver available through my CUPS install (cups 1.7.2-0ubuntu1.2) or to use something more generic and a little degraded instead... viz. drivers for either the *Laserjet III, IIIP *or plain* LaserJet 4*. I checked that both IIIP and 4 work fine and in fact offer more printing options than the equivalent Windows' driver I used before for that printer, ie. a "proper" *LaserJet 4 Plus printer driver* compiled for Windows.

@ajgreeny
Thank you too for the detailed description you provide. I was familiar with [that]("https://help.ubuntu.com/community/NetworkPrintingWithUbuntu") provided by _help.ubuntu.com_ as an Ubuntu Wiki. It is all working fine. I just have to install a Samba server now.


**FOLLOW-UP:**
I am still very interested in troubleshooting my network card and of course I don't know where to start. I ll post a new thread about that.

Cheers,  -ced.

---

### Post by Tim_McNaughton on 2014-10-11
I finally got my networked HP LaserJet p1102w to work over WLAN by using hp-setep from:  

[http://hplipopensource.com/node/309](http://hplipopensource.com/node/309)

 "Some HP printers require  proprietary software technologies to allow full access to printer  features and performance.  Unfortunately, these technologies cannot be  open sourced, but to resolve this HP uses a binary plug-in for these  printers.   it requires the user to read and agree  to a license agreement at the time of driver installation. 

Most  Linux distributions include HPLIP with their software, but most do not  include the plug-in.  Therefore, it is a safe practice to run a utility  called[FONT=Courier New] "hp-setup"[/FONT], which, will install the printer into the CUPS spooler, download, and install the plug-in at the appropriate time."

---

### Post by Cbhihe on 2014-10-11
Thanks, I had tried that quite early on in fact. 

In a nutshell, hp-setup does not detect my LaserJet 4 Plus:
[LIST]
[*]- either as a peripheral directly connected by USB (even though I print all day through USB without a glitch) 
[*]- or as a networked device on the LAN. 
[/LIST]
In both cases I tried repeatedly the automatic device detection mode and the manual detection mode. (entering correct bus and device codes as xyz:rst for the USB connection and the router defined IP for the network connection).

I am not sure whether this lack of success is because:

[LIST]
[*]my printer's network card  is too old to be recognized (possible although I deem it improbable and by what ? Ubuntu ? CUPS ? ) 
[*]my J2552A network-card is defective (unlikely since my router's DCHP service does give it an IP when connected to LAN through its 10Base-T port, and the self-test print-out yields a clean bill of health for the network card - namely: Novell status 29 (no Novell network available); AppleTalk status ready; TCP/IP status ready; DLC/LLC status ready ) 
[*]I'm basically not nearly as smart as I thought (always a nagging question, isnt it?) and I am missing something important I should do prior to using hp-setup 
[/LIST]

In any case I have a question about hp-setup:
The second window "*Device Discovery*" gives 3 choices. If I choose the second:[INDENT]*Network/Ethernet/Wireless Netword (direct connection or JetDirect)*
[/INDENT]
**1)** I do have a MIO card implementing *HP JetDirect* already. How do I check that is is in good condition ? 
**2)** And a question of semantics: what does "Direct connection" mean in that context ? Is it a direct connection to the router (my case of choice) ? Or a direct connection to the JetDirect card ?

---

### Post by Cbhihe on 2014-10-11
I found the solution for the *LJ4Plus*  config on Ubuntu 14.04 Desktop.
Everything lies in the fact that the MIO JetDirect card NEEDS to be network-configured. In the case of Linux and the MIO JetDirect card, it can only be done directly from the LaserJet's LCD control panel, following those [steps]("http://www.printertechs.com/other-instructions/network-printing-tutorial/152-entering-ip-address") - lookup the section entitled: "*Older Laserjets with displays like the LJ4 and LJ4Plus *". 

Once you're done with that, run *hp-setup. *It will recognize the printer faultlessly. Give it a distinctive name, e.g. *frigging-netwrk-lj4p. hp-setup* will correspondingly place a new printer icon on the printer panel.
Not quite done ! As before (for choosing the driver of the USB connected LJ 4Plus), you must then change the driver chosen by hp-setup from that of the *LJ4Plus* to that of the *LJ4*. Print a test page over the network after that and rejoice.

Thanks to all of you  and a special ):P to Tim_McNaughton, who goaded me into looking at this once more, while I really had had it and half considered the problem not quite so worthy of my time anymore.  
I had in truth looked at hp-setup from all angles before, without realizing that the problem is **one must physically punch an IP address and a subnet mask into the printer prior to using hp-setup**. In fact I had also tried doing that already, but somehow had botched it.

---

