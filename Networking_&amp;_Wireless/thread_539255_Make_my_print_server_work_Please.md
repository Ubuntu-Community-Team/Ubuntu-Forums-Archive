---
title: "Make my print server work? Please?"
date: 2007-08-31
forum: Networking &amp; Wireless
---

### Post by mlissner on 2007-08-31
I am running the latest and greatest Ubuntu version, have an HP JetDirect ew2400 external print server, a run of the mill wireless linksys router, and a Brother MFC 4800 printer.

I want them all to talk to each other.

So far, I have connected the print server to the network and to the printer, but that's abouts as far as I can figure out. Pressing the test button on the print server doesn't seem to do anything, I can't figure out how to find the printer on the network...

...can somebody help me out? I feel like this ought to be much easier than it is seeming to be, but I can't even figure out where to begin. Networking remains a weak point in my repertoire.

---

### Post by mtn on 2007-09-07
Hey,

I'm no network expert but I notice this post is a week old so I'll just mention how I would start with this issue.

First, I would try and get the printer going as a network printer between 2 machines. I.e. the printer hardwired into an Ubuntu machine and sharing  the printer to either another XP or Ubuntu machine accross the network. I got things going using this how to: [http://www.linuxquestions.org/linux/answers/Networking/Setting_Up_a_Network_Printer_using_CUPS](http://www.linuxquestions.org/linux/answers/Networking/Setting_Up_a_Network_Printer_using_CUPS)

I had to stop the firewall on the server (i.e the machine that the printer is attached to), using Firestarter, while setting the printer up. I also had to create a new policy to always allow access to the print server (Ubuntu machine) 0n port 631 from the client machine’s IP address.

Once the Ubuntu machine was setup as a server for the printer it took about 5mins to get a Windows XP machine sharing the printer, over the same home network, using this how to: [http://www.owlfish.com/thoughts/winipp-cups-2003-07-20.html](http://www.owlfish.com/thoughts/winipp-cups-2003-07-20.html). The only bits I actually had to use are posted below.

(Note: my network printer address - [http://192.168.2.4:631/printers/LaserJet-1018](http://192.168.2.4:631/printers/LaserJet-1018)) 

> 
**Hostname lookup**

Another common step is to ensure that hostname broadcast by CUPS is accessible from the Windows XP machine. If your CUPS machine is accessible using a name rather than just an IP address then you don’t need to do anything for this step. If the CUPS machine is not accessible via it’s hostname then you need to set a mapping between the CUPS hostname and its IP address in the Windows hosts file. Under WindowsXP the host file is in C:\WINDOWS\SYSTEM32\DRIVERS\ETC\HOSTS, in Win2k replace WINDOWS with WINNT. The format is simple:

# Example hosts entry
192.168.0.3 rock

Under some CUPS server configurations you will be able to use the IP address instead of the hostname, but often only a hostname will work.
Postscript Printing

To use a printer queue as a Postscript printer requires a Windows XP Postscript printer driver, such as the built-in MS Publisher Imagesetter or this freely available one from Adobe.
Built-in MS Publisher Imagesetter

To use the MS Publisher Imagesetter driver, use “Add Printer” to add a new network printer, select “Connect to a printer on the Internet…” and enter the URL for your printer queue (e.g. [http://rock:631/printers/Epson](http://rock:631/printers/Epson)). When prompted for a driver select a Manufacturer of “Generic” and the Printer “MS Publisher Imagesetter”.

To get the print server working I would first make sure it was hooked up to the network. I think  most decent print servers (like routers) have web based admins, i.e you can login to them just like they are a web site but located on your local network - [http://192.168.2.1](http://192.168.2.1) Can you hardwire it into the router? Try getting the print servers IP from the router admin, and then  try login in to the print server admin pages i.e. putting the print servers IP address into your web browser.

Once you have the print servers IP and you can login to it's admin I think you are getting somewhere. I'm not sure, but I think not all print servers will work with Linux, that is they don't support the necessary protocols. I could be wrong on this. I am looking for a print server at the moment and am going to ask on the forums if this is the case, or not, and what print server folks recommend. So far I have seen this one [http://www.edimax.gr/en/support_detail.php?pd_id=24&pl1_id=7&pl2_id=33#02](http://www.edimax.gr/en/support_detail.php?pd_id=24&pl1_id=7&pl2_id=33#02) that looks good but in it's "compatibility list" my HP 1018 B&W laser Jet is not listed as being supported!!!

Oh well, hope this helps a bit.

---

### Post by CalvinK on 2007-09-09
> **mtn said:**
> Hey,

I'm no network expert but I notice this post is a week old so I'll just mention how I would start with this issue.

First, I would try and get the printer going as a network printer between 2 machines. I.e. the printer hardwired into an Ubuntu machine and sharing  the printer to either another XP or Ubuntu machine accross the network. I got things going using this how to: [http://www.linuxquestions.org/linux/answers/Networking/Setting_Up_a_Network_Printer_using_CUPS](http://www.linuxquestions.org/linux/answers/Networking/Setting_Up_a_Network_Printer_using_CUPS)

I had to stop the firewall on the server (i.e the machine that the printer is attached to), using Firestarter, while setting the printer up. I also had to create a new policy to always allow access to the print server (Ubuntu machine) 0n port 631 from the client machine’s IP address.

Once the Ubuntu machine was setup as a server for the printer it took about 5mins to get a Windows XP machine sharing the printer, over the same home network, using this how to: [http://www.owlfish.com/thoughts/winipp-cups-2003-07-20.html](http://www.owlfish.com/thoughts/winipp-cups-2003-07-20.html). The only bits I actually had to use are posted below.

(Note: my network printer address - [http://192.168.2.4:631/printers/LaserJet-1018](http://192.168.2.4:631/printers/LaserJet-1018)) 



To get the print server working I would first make sure it was hooked up to the network. I think  most decent print servers (like routers) have web based admins, i.e you can login to them just like they are a web site but located on your local network - [http://192.168.2.1](http://192.168.2.1) Can you hardwire it into the router? Try getting the print servers IP from the router admin, and then  try login in to the print server admin pages i.e. putting the print servers IP address into your web browser.

Once you have the print servers IP and you can login to it's admin I think you are getting somewhere. I'm not sure, but I think not all print servers will work with Linux, the at is they don't support the necessary protocols. I could be wrong on this. I am looking for a print server at the moment and am going to ask on the forums if this is the case, or not, and what print server folks recommend. So far I have seen this one [http://www.edimax.gr/en/support_detail.php?pd_id=24&pl1_id=7&pl2_id=33#02](http://www.edimax.gr/en/support_detail.php?pd_id=24&pl1_id=7&pl2_id=33#02) that looks good but in it's "compatibility list" my HP 1018 B&W laser Jet is not listed as being supported!!!

Oh well, hope this helps a bit.

I'm presently trying to connect my laptop to a print server TRENDnet TE100-P1U connected to my wifi router Gigaset SE515dsl (Siemens). I configured it with a static IP address (but it works also with DHCP) via firefox. It works well enough with Windows XP but I cannot see it in my network when I am in Ubuntu (maybe a firewall problem, I will try it). I can scan the ports and retrieve it by the means of the network tools but I'm currently enable to print a test...  I tried it as ipp, lpd, windows type ...
I have modified the /etc/cups/cupsd.conf file to listen to this IP but it doesn't detect my printer.
I am scanning Internet but I found no response until now.
I will post the solution if I find it.
:confused:

---

### Post by CalvinK on 2007-09-09
> **CalvinK said:**
> I'm presently trying to connect my laptop to a print server TRENDnet TE100-P1U connected to my wifi router Gigaset SE515dsl (Siemens). I configured it with a static IP address (but it works also with DHCP) via firefox. It works well enough with Windows XP but I cannot see it in my network when I am in Ubuntu (maybe a firewall problem, I will try it). I can scan the ports and retrieve it by the means of the network tools but I'm currently enable to print a test...  I tried it as ipp, lpd, windows type ...
I have modified the /etc/cups/cupsd.conf file to listen to this IP but it doesn't detect my printer.
I am scanning Internet but I found no response until now.
I will post the solution if I find it.
:confused:
 
It works at last !!!
Just choose Unix printer then type in host name the IP address of your server. In queue type the port of the server (lp1 for example or U1, you can obtain it via your internet browser). And that's all folks:popcorn:

---

